+++
title = "How CloudFront Functions can Unify your Domain Strategy"
description = "How CloudFront Functions can Unify your Domain Strategy"
summary = "How CloudFront Functions can Unify your Domain Strategy"
date = '2025-09-10T00:18:30-04:00'
lastmod = '2025-09-10T00:18:30-04:00'
keywords = []
tags = ['aws', 'cloudfront', 'seo', 'google']
categories = []
draft = false 
[params]
    author = 'Manikandaraj Srinivasan'
+++

# Stop Splitting Your SEO: How CloudFront Functions Can Unify Your Domain Strategy for Pennies

If you're running a website, you've probably faced this dilemma: should your site be accessible at `yoursite.com` or `www.yoursite.com`? Maybe you've set up both to work, thinking you're being helpful to users. But here's the problem—**Google sees these as two completely different websites**, and you're accidentally splitting your SEO authority in half.

Today, I'll show you how to solve this using AWS CloudFront Functions to create seamless 301 redirects that cost virtually nothing and can be set up in minutes.

## The SEO Problem You Didn't Know You Had

When both `iammanis.com` and `www.iammanis.com` serve the same content, search engines treat them as separate sites. This means:

- Your backlinks are split between two domains
- Your page authority is diluted
- You might face duplicate content penalties
- Your search rankings suffer unnecessarily

The solution? Pick one canonical domain (let's say `www.iammanis.com`) and redirect all traffic from the other (`iammanis.com`) using a 301 permanent redirect.

## The Traditional (Expensive) Approach

Most tutorials will tell you to create two S3 buckets:
- One for content hosting (`www.iammanis.com`)
- Another just for redirects (`iammanis.com`)

Then you'd need two CloudFront distributions, potentially doubling your costs. This works, but it's overkill for a simple redirect.

## The CloudFront Function Solution: One Distribution to Rule Them All

Here's the elegant approach that uses **one S3 bucket**, **one CloudFront distribution**, and a tiny JavaScript function to handle the redirects intelligently.

### Step 1: Configure Your CloudFront Distribution

Set up a single CloudFront distribution with:
- **Alternate Domain Names (CNAMEs)**: Both `www.iammanis.com` and `iammanis.com`
- **SSL Certificate**: An ACM certificate covering both domains
- **Origin**: Your `www.iammanis.com` S3 bucket

### Step 2: Create the CloudFront Function

This is where the magic happens. Create a CloudFront Function with this simple JavaScript:

```javascript
function handler(event) {
    var request = event.request;
    var host = request.headers.host.value;
    
    if (host === 'iammanis.com') {
        return {
            statusCode: 301,
            statusDescription: 'Moved Permanently',
            headers: {
                "location": {
                    "value": `https://www.iammanis.com${request.uri}`
                }
            }
        };
    }
    
    return request;
}
```

This function:
- Checks the incoming host header
- If it's the non-www version, returns a 301 redirect to the www version
- Preserves the full path (so `/about` redirects to `/about`)
- Otherwise, passes the request through normally

### Step 3: Associate the Function

- Set the **Event type** to "Viewer Request"
- Attach it to the **default behavior** of your CloudFront distribution

### Step 4: Configure Route 53

Create two alias records pointing to your single CloudFront distribution:
- `iammanis.com` → CloudFront distribution
- `www.iammanis.com` → CloudFront distribution

## The Result: Perfect SEO-Friendly Redirects

Now when someone visits:
- `https://iammanis.com/about` → Automatically redirects to `https://www.iammanis.com/about`
- `https://www.iammanis.com/about` → Serves content directly from S3

Google sees the 301 redirect and consolidates all SEO signals to your canonical `www.iammanis.com` domain.

## Cost Analysis: Practically Free

Here's where CloudFront Functions really shine:

| Monthly Traffic | CloudFront Function Cost |
|----------------|-------------------------|
| Under 2 million requests | **$0.00** (free tier) |
| 5 million requests | **$0.30** |
| 10 million requests | **$0.80** |

For comparison, Lambda@Edge costs $0.60 per million requests—that's **10x more expensive** than CloudFront Functions.

### Real-World Example

Let's say your site gets 50,000 hits per day on the non-www domain:
- Monthly requests: ~1.5 million
- CloudFront Function cost: **$0.00** (within free tier)
- Even at 5 million requests: **$0.30/month**

That's less than a cup of coffee to solve your SEO consolidation problem!

### Key Advantages:

1. **Ultra Cheap**: Free tier covers most personal/small business sites
2. **Simple to Implement**: Basic JavaScript, no complex Node.js
3. **Instant Updates**: Changes deploy in seconds
4. **Resource Efficient**: One distribution instead of two

## Why This Matters for Your Business

Beyond the technical benefits, this approach delivers real business value:

- **Better SEO Rankings**: Consolidated domain authority
- **Improved User Experience**: Fast, seamless redirects
- **Lower AWS Bills**: Minimal CloudFront Function costs
- **Simplified Infrastructure**: Fewer moving parts to manage
- **Future-Proof**: Easily modify redirect logic as needed

## Getting Started Today

If you're ready to implement this solution:

1. Set up your CloudFront distribution with both domains
2. Create the CloudFront Function with the redirect logic
3. Associate it with your distribution
4. Update your Route 53 records
5. Test both domains to verify redirects work

The entire process takes about 15 minutes, and you'll immediately start consolidating your SEO authority.

## Conclusion: Small Function, Big Impact

CloudFront Functions prove that sometimes the best solutions are the simplest ones. For the cost of a few cents per month (if anything), you can solve a critical SEO problem that could be costing you valuable search traffic.

Whether you're running a personal blog, a business website, or managing multiple client sites, this approach gives you professional-grade domain consolidation without the enterprise-level complexity or costs.

Stop splitting your SEO authority across multiple domains. Your search rankings (and your AWS bill) will thank you.

---

