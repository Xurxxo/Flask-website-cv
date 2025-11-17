# Migration to Static Site

## Decision
Migrating from serverless Lambda to S3 static hosting for better cost-efficiency and performance.

## Rationale
- CV website is purely presentational (no dynamic backend needed)
- S3 + CloudFront provides better performance at lower cost
- Lambda charged per request is expensive for static assets
- Static site allows for faster page loads via CDN

## Architecture Change
**Before:** API Gateway → Lambda (Flask)
**After:** CloudFront → S3 (Static HTML/CSS/JS)

## Cost Comparison
- Lambda: ~$5-10/month
- S3 + CloudFront: ~$0.50/month

## Implementation
Flask templates will be pre-rendered to static HTML during CI/CD pipeline.
