# career-amplifier

## Description

This is the public repo for careeramplifier.com, a product manager interview prep service. The intent is to build this in public, and use this website as a tool to teach people about product, marketing, analytics, and more.

This is a static website that's hosted in an AWS S3 bucket with Stripe Payment Links and Calendly for scheduling. 

Have a question, tweet at us @careeramp_

## v0.0.4 - Optimize Website

I used the [Page Speed Insights](https://developers.google.com/speed/pagespeed/insights/) tool to determine what to optimize. Plus, I needed SSL and a CDN for best practices anyway. The addition of the CDN made a noticeable difference in the website's Page Speed Scores which will have a positive impact on both Search Engine Optimization and Google Ad's Quality Score which directly impacts ad pricing. In other words, this release benefits revenue and marketing efficiency. The image format change doesn't seem to have had as big an impact but it will keep the website light, so it's good practice to do this.
				
				Mobile 				Desktop
Before			50 					80
After			62 (+24%)			90 (+12.5%)

- Updated all the images used to WebP format. After looking around, I decided to just download an app and manually convert. The code version didn't seem worth the effort for this project, but it's odd that there isn't better Mac support for using homebrew. Perhaps I just didn't look in the right places: https://apps.apple.com/us/app/webp-converter-anywebp/id1527716894?mt=12
- Added the Twitter and GitHub logos + links for Career Amplifier to the footer.

Changes in AWS
- Added SLL certificate in AWS + Cloudfront as the CDN (with HTTP to HTTPS redirects so every connection to the server will be secure with TLS v1.2). This will enable the website to load significantly faster while also increasing its security. This [tutorial](https://link.medium.com/nxCSUEwaSkb) was invaluable.
- Fixed the www.careeramplifier.com issue by point the domain via Route 53 to the CDN (it wasn't possible to point this to the careeramplifier.com S3 bucket since the name has to match the domain exactly).
- Learned about invalidating paths in Cloudfront. If you release your code but realize you have to fix something so you quickly redeploy the fix, without invalidating the path, Cloudfront won't update the version of the website it has cached for easier distribution. As of now, [Cloudfront allows up to 1,000 invalidations for free per month](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html#PayingForInvalidation).

## Upcoming

I NEED to convert these to issues at some point.

X SSL + Cloudfront (AWS, no GitHub changes)
X Page Speed Improvements (see page speed score)
X 'Featured Career Coach' (image, short bio, Twitter + LinkedIn)
- Add FAQ section to homepage
- Add The Product Manager Role section to homepage
- Nagging issue: The goal tracking in GA seems off. The events appear to track as expected, but they aren't tracking as goals. Something for later.
- Meta description to render specific text and image when the link is shared
- FB Pixel + Facebook Retargeting + Don't market to converted users
- Privacy policy
- Add more keywords
- remove .html from urls (this may be more effort than it's worth.)
- New page (/[coach-name]) to feature a Career Coach (image, bio, Twitter + LinkedIn, Recommended Books, Recommended Articles, Best Advice)
- Tech Career Coaching page
- Product Marketing Management page
- Add GTM to pass utm_source and other marketing UTM params from one page to another. Tutorial with Code https://www.analyticsmania.com/post/transfer-utm-parameters-google-tag-manager/
- Pass utm param tracking. https://easyautotagging.com/track-custom-utm-parameters-google-analytics/
- Add Amazon affiliate links to the book recommendation page

More A/B experiment ideas
- 'What to expect for the first session' section on the homepage
- 'Resume tips' section on the homepage
- 'Behavioral Question Bank' section on the homepage
- 'Product Case Question Bank' section on the homepage
- Generic homepage with references to Tech / PM / PMM coaching

## History

v0.0.3 - Added New Content to Homepage

- Rearranged sections on the homepage
- Added PM Interview Question Types
- Added Featured Career Coach
- Added Recommended Books
- Added new images

v0.0.2 - Payments

- Create payment-confirmation.html
- Add 'noindex' to payment-confirmation.html and call-scheduled.html
- Stripe payment links redirects to payment-confirmation.html for tracking
- Update Google Tag Manager (GTM) to trigger conversion to Google Analytics (GA)
- Pass 'amount' utm param value in GTM
- Update GA to track the conversion

v0.0.1 - Hello World

- Static website: HTML + CSS + JS
- index.html is the homepage, and it's the only page in the sitemap.txt. 
- call-scheduled.html is the conversion confirmation page that allows for tracking when a calendly call has been scheduled. This page has a nofollow tag for search bots.
- Built website from Promodise Bootstrap template (license info below for Themefisher)
- Set-up Calendly to capture conversions
- Integrated with Google Tag Manager to manage all tracking include Google Analytics, Google Optimize, and Full Story.
- Added Google Search Console and connected the sitemap.
- Created Google Ad campaign to begin driving traffic.

## LICENSES

Copyright (c) 2019 Themefisher 
Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions: The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software. THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

Check out our Mega-Bundle:
1 - HTML Mega Bundle : https://themefisher.com/bundle/
2 - Hugo Mega Bundle : https://themefisher.com/products/hugo-mega-bundle