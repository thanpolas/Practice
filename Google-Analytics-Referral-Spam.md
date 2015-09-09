How to tackle Google Analytics referral spam.

1. Go to the Admin page of your analytics.
1. On the 'View' tab on the right, click on 'View Settings'.
1. Find the "Bot Filtering" checkbox and check it, then save.
1. From the left sidebar go to the 'Filters' view.
1. Create new filters as illustrated bellow:

## Creating Filters

All the filters we will create will be of **Type** "Custom" and **Field** "Campaign Source". We use the "Campaign Source" field because the "Referral" field will not do the job, it'll skew results and mixup bots with our general visitors.

The "Filter Pattern" accepts up to 255 characters so we have to break out the filters in multiples:

#### Referral Spam 1

> trafficmonetizer\\.org|success-seo\\.com|webmonetizer\\.net|4webmasters\\.org|dailyrank\\.net|floating-share-buttons\\.com|social-buttons\\.com|simple-share-buttons\\.com|free-share-buttons\\.com|free-social-buttons\\.com|traffic2money\\.com|buttons-for-website\\.com

#### Referral Spam 2

> seo-platform\\.com|sexyali\\.com|get-free-social-traffic\\.com|qualitymarketzone\\.com|site4\\.free-floating-buttons\\.com|bundlepost\\.com|site7\\.free-floating-buttons\\.com|site8\\.free-floating-buttons\\.com|chinese-amezon\\.com|site1\\.free-floating-buttons\\.com

#### Referral Spam 3

> www\\.event-tracking\\.com|www\\.Get-Free-Traffic-Now\\.com|site2\\.free-floating-buttons\\.com|videos-for-your-business\\.com

#### Referral Spam Catchall

This pattern was suggested by [Brian Clifton in this blog post](https://brianclifton.com/blog/2015/05/29/removing-referral-spam/).

> offer|free\-|share\-|mercedes|buy|cheap|semalt|googlsucks|benz|sl500|hulfington|buttons|
darodar|pistonheads|motor|money|blackhat|backlink|webrank|seo|phd|
crawler|anonymous|\d{3}.*forum|porn|webmaster|flipboard|fl\.ru|
mbca|ahrefs|game|\.io|^sex|^video


## More Reading

* https://www.distilled.net/resources/quick-fix-for-referral-spam-in-google-analytics/
* http://www.optimizesmart.com/geek-guide-removing-referrer-spam-google-analytics/
