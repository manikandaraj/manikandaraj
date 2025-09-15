+++
title = "Hugo Pretty URLs CloudFront Fix"
description = "Resolving Directory Index Issues for Static Sites"
summary = "Resolving Directory Index Issues for Static Sites"
date = '2025-09-10T00:18:30-04:00'
lastmod = '2025-09-10T00:18:30-04:00'
keywords = []
tags = ['hugo', 'aws', 'cloudfront', 'pretty-url']
categories = []
draft = false 
[params]
    author = 'Manikandaraj Srinivasan'
+++

# Hugo Pretty URLs CloudFront Fix
## Resolving Directory Index Issues for Static Sites

---

### **Problem Statement**

Hugo static sites generate clean URLs by creating directory structures with `index.html` files. However, AWS CloudFront and S3 don't automatically serve `index.html` files when users request directory paths, resulting in "Access Denied" errors.

**Issue Example:**
- Hugo generates: `/blog/my-post/index.html`
- User requests: `https://example.com/blog/my-post/`
- Result: Access Denied error

### **Root Cause Analysis**

**Hugo URL Structure:**
Hugo with `uglyURLs: false` creates:
```
/blog/index.html
/blog/post-title/index.html
/categories/tech/index.html
```

**CloudFront Behavior:**
- Requests ending in `/` look for directory listings
- S3 REST API endpoints don't serve directory index files
- CloudFront passes requests as-is to S3 without index file resolution

### **Solution: CloudFront Function**

**Implementation:**
A CloudFront Function that intercepts viewer requests and rewrites URLs to append `index.html` when needed.

**Function Code:**
```javascript
function handler(event) {
    var request = event.request;
    var uri = request.uri;
    
    // Check whether the URI is missing a file name
    if (uri.endsWith('/')) {
        request.uri += 'index.html';
    }
    // Check whether the URI is missing a file extension
    else if (!uri.includes('.')) {
        request.uri += '/index.html';
    }
    
    return request;
}
```

### **How It Works**

**Request Processing:**
1. User visits `https://example.com/blog/`
2. CloudFront Function intercepts the request
3. Function detects URL ends with `/`
4. Function rewrites request to `/blog/index.html`
5. S3 serves the actual file
6. User sees content at clean URL

**URL Patterns Handled:**
- `/blog/` → `/blog/index.html`
- `/blog/my-post` → `/blog/my-post/index.html`
- `/categories/tech/` → `/categories/tech/index.html`
- Static assets (`.css`, `.js`, `.png`) remain unchanged

### **Implementation Steps**

**Step 1: Create CloudFront Function**
```bash
# Create function file
cat > index-rewrite.js << 'EOF'
function handler(event) {
    var request = event.request;
    var uri = request.uri;
    
    if (uri.endsWith('/')) {
        request.uri += 'index.html';
    }
    else if (!uri.includes('.')) {
        request.uri += '/index.html';
    }
    
    return request;
}
EOF

# Create CloudFront function via AWS CLI
aws cloudfront create-function \
  --name "hugo-index-rewrite" \
  --function-config Comment="Append index.html for Hugo pretty URLs",Runtime="cloudfront-js-1.0" \
  --function-code fileb://index-rewrite.js
```

**Step 2: Publish Function**
```bash
# Get function ETag
ETAG=$(aws cloudfront describe-function --name "hugo-index-rewrite" --query 'ETag' --output text)

# Publish function
aws cloudfront publish-function \
  --name "hugo-index-rewrite" \
  --if-match $ETAG
```

**Step 3: Associate with Distribution**
1. Open CloudFront console
2. Select your distribution
3. Edit Default Cache Behavior
4. Scroll to Function Associations
5. Select Viewer Request event type
6. Choose your function
7. Save changes

### **Benefits**

**User Experience:**
- Clean, professional URLs maintained
- No broken links or 404 errors
- Consistent navigation experience
- SEO-friendly URL structure

**Technical Advantages:**
- Minimal latency impact (edge execution)
- No backend infrastructure required
- Works with existing Hugo configuration
- Compatible with all Hugo themes

**Performance:**
- Function executes at CloudFront edge locations
- No additional round trips to origin
- Cached responses benefit from CDN
- Sub-millisecond execution time

### **Alternative Solutions Compared**

**Option 1: S3 Website Hosting**
- Pros: Built-in index document support
- Cons: Limited HTTPS/SSL options, no advanced CloudFront features

**Option 2: Lambda@Edge**
- Pros: More powerful processing capabilities
- Cons: Higher latency, more complex, higher cost

**Option 3: CloudFront Function (Recommended)**
- Pros: Fast execution, simple logic, cost-effective
- Cons: Limited to basic request/response manipulation

### **Monitoring & Validation**

**Testing Commands:**
```bash
# Test directory requests
curl -I https://example.com/blog/
curl -I https://example.com/categories/tech/

# Test clean URLs
curl -I https://example.com/blog/my-post
curl -I https://example.com/about

# Verify static assets unchanged
curl -I https://example.com/css/style.css
curl -I https://example.com/js/main.js
```

**Expected Results:**
- All directory and clean URLs return HTTP 200
- Content-Type headers show `text/html` for pages
- Static assets serve normally
- Browser URL bar shows clean URLs

### **Cost Impact**

**CloudFront Function Pricing:**
- $0.10 per 1 million function invocations
- Typical website: < $1/month additional cost
- No additional infrastructure required
- Scales automatically with traffic

---

**Status:** Production Ready  
**Execution Location:** CloudFront Edge  
**Latency Impact:** < 1ms  
**Compatibility:** All Hugo versions with `uglyURLs: false`  

---

*This solution provides a robust, scalable fix for Hugo pretty URL issues on CloudFront while maintaining optimal performance and minimal cost impact.*
