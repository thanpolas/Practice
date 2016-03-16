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

> .\*(trafficmonetizer|4webmasters|webmonetizer|dailyrank)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 2

> .\*(success\\-seo|floating\\-share\\-buttons|social\\-buttons|simple\\-share\\-buttons|free\\-share\\-buttons|free\\-social\\-buttons|traffic2money|buttons\\-for\\-website)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 3

> .\*(seo-platform|sexyali|get\\-free\\-social\\-traffic|qualitymarketzone|free\\-floating\\-buttons|bundlepost|chinese\\-amezon)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 4

> .\*(event\\-tracking|Get\\-Free\\-Traffic\\-Now|videos\\-for\\-your\\-business|ranksonic|rankings\\-analytics|copyrightclaims)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 5

> .\*(googlemare|quit\\-smoking|trafficgenius|2your.site|for\\-your|yeartwit|годом)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua|рф).\*

#### Referral Spam 6

> .\*(semalt|buttons\\-for\\-your\\-website|best\\-seo\\-solution|best\\-seo\\-offer|100dollars\\-seo|semaltmedia|video--production)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 7

> .\*(blackhatworth|7makemoneyonline|ilovevitaly|priceg|prodvigator|resellerclub|savetubevideo|screentoolkit|kambasoft|socialseet|superiends|vodkoved|iskalko|luxup|myftpupload|websocial|ykecwqlixx)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 8

> .\*(slftsdybbg|seoexperimenty|darodar|econom|edakgfvwql|adcash|adviceforum|hulfingtonpost|europages|gobongo|cenoval|cityadspix|cenokos|lomb|lumb|srecorder|see\\-your\\-website\\-here|76brighton)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 9

> .\*(anticrawler|medispainstitute|offers\\.bycontext|sitevaluation|paparazzistudios|powitania|sharebutton|tasteidea|descargar\\-musica\\-gratis|torontoplumbinggroup|54\\.186\\.60\\.77|ekatalog)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam 10

> .\*(rankscanner|sharemyfile|justprofit|127\\.0\\.0\\.1|search\\-helper|dbutton|o00|wordpress\\-crew|fast\\-wordpress\\-start|top1\\-seo\\-service|uptimechecker|uptimebot)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*

#### Referral Spam Catchall

This pattern was suggested by [Brian Clifton in this blog post](https://brianclifton.com/blog/2015/05/29/removing-referral-spam/).

> offer|free\\-|share\\-|mercedes|buy|cheap|semalt|googlsucks|benz|sl500|hulfington|buttons|
darodar|pistonheads|motor|money|blackhat|backlink|webrank|seo|phd|
crawler|anonymous|\\d{3}.*forum|porn|webmaster|flipboard|fl\\.ru|
mbca|ahrefs|game|^sex|^video

#### Referral Spam 2016

An update for 2016

> .\*(website\\-analyzer|boost\\-my\\-site|traffic2cash|santasgift|o\\-o\\-8\\-o\\-o|snip)\\.(com|org|net|ml|tw|info|xyz|to|website|co|ru|ro|au|ua).\*


## More Reading

* https://www.distilled.net/resources/quick-fix-for-referral-spam-in-google-analytics/
* http://www.optimizesmart.com/geek-guide-removing-referrer-spam-google-analytics/
