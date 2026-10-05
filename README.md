# proxy residential: How to Read $/GB Pricing, Pick Rotating or Sticky Sessions, and Stop Paying for Traffic You Never Use

Most "proxy residential" searches end the same way: you land on a pricing page, see a number like $1/GB, get excited, then reach a checkout that wants a different amount, on a plan that expires monthly whether you used the traffic or not.

The headline rate is usually real. It's just real at a volume you weren't planning to buy, or on a billing cycle that quietly eats whatever you don't consume. So before comparing vendors, it helps to know which three things actually move your bill.

## The three numbers that decide what you really pay

**Entry minimum.** A vendor can advertise $1.40/GB and charge $3.50 for the single gigabyte you want to test with. Third-party price audits of this market have documented that pattern repeatedly: the advertised floor sits at a tier far above the smallest purchasable amount. The only rate that matters is the one attached to your first realistic purchase.

**Expiry.** Monthly subscription models reset. Buy 100 GB, use 30, and 70 GB disappears on the first of the month. You paid for bandwidth you'll never transmit. Pay-as-you-go traffic that doesn't expire behaves differently: the unused gigabyte sits in your account until a project needs it.

**Plan granularity.** A vendor whose smallest plan is 125 GB doesn't have a 10 GB option, no matter what their marketing says. If your workload is 20 GB a month, you're buying 105 GB of dead weight every cycle. This is why "cheapest provider" is a meaningless phrase on its own — the answer flips depending on whether you're moving 5 GB or 5 TB.

Residential proxies in particular are priced per gigabyte rather than per IP, which makes all three of these levers visible at once. That's also why the same network can look like a bargain to one team and an expensive habit to another.

## What you're actually buying with a residential proxy

A residential proxy routes your request through an IP address assigned by a consumer ISP to a real household connection. The target site sees an ordinary home user, not a server in a Frankfurt datacenter. That's the whole point: datacenter IPs are cheap and fast, but they're also easy for anti-bot systems to fingerprint and block in bulk.

Those household IPs come from people who opted into a bandwidth-sharing app and get paid for it. That acquisition model matters more than pool size claims. When a provider resells IPs sourced from third-party networks, those addresses carry an abuse history accumulated across every previous user of every reseller connected to that supply. A first-party pool starts cleaner, which tends to show up in block rates rather than in a spec sheet.

One provider worth examining through that lens is DataImpulse, which sells residential traffic at **$1/GB** on a pool it says it builds itself through its own bandwidth-sharing apps rather than reselling someone else's network. It advertises 90M+ IPs across 195 countries, HTTP/HTTPS and SOCKS5 support, and country-level targeting included at the base rate.

## What DataImpulse charges, tier by tier

The pricing model is a top-up, not a subscription. You add funds, you get traffic, and the traffic doesn't expire. The minimum purchase is **$5**, which translates to different volumes depending on which product you're pointing it at.

Here's how the current product line breaks down. Rates are per gigabyte; the volume discount kicks in at the 1 TB tier.

| Plan (by volume) | Proxy type | Rate | Entry cost | Notes | Buy |
| --- | --- | --- | --- | --- | --- |
| 5 GB intro | Residential | $1.00/GB | $5 minimum | Traffic never expires; 7-day refund on card payments | [Start with the $5 residential intro](https://bit.ly/dataimPulse) |
| 25 GB | Residential | $1.00/GB | $25 | Same rate as entry — no bundle discount below 1 TB | [Top up 25 GB of residential traffic](https://bit.ly/dataimPulse) |
| 100 GB | Residential | $1.00/GB | $100 | Flat rate, country targeting included | [Add 100 GB to your balance](https://bit.ly/dataimPulse) |
| 1 TB | Residential | $0.80/GB | $800 | 20% volume discount | [Take the 1 TB residential rate](https://bit.ly/dataimPulse) |
| 10 GB | Datacenter | $0.50/GB | $5 minimum | 99.99% uptime, low latency, 123 locations | [Check datacenter rates](https://bit.ly/dataimPulse) |
| 100 GB | Datacenter | $0.50/GB | $50 | For targets that don't require residential legitimacy | [Load 100 GB of datacenter traffic](https://bit.ly/dataimPulse) |
| 1 TB | Datacenter | $0.45/GB | $450 | 10% volume discount | [See the 1 TB datacenter tier](https://bit.ly/dataimPulse) |
| 2.5 GB | Mobile | $2.00/GB | $5 minimum | 5G/4G/3G/LTE carrier IPs, 191 locations | [Test mobile proxies from $5](https://bit.ly/dataimPulse) |
| 50 GB | Mobile | $2.00/GB | $100 | Rotating and sticky sessions | [Add 50 GB of mobile traffic](https://bit.ly/dataimPulse) |
| 1 TB | Mobile | $1.60/GB | $1,600 | 20% volume discount | [View the 1 TB mobile tier](https://bit.ly/dataimPulse) |
| 1 GB | Premium residential | $5.00/GB | $5 minimum | Dedicated account manager, all targeting options at no surcharge | [Try premium residential](https://bit.ly/dataimPulse) |
| 10 GB | Premium residential | $5.00/GB | $50 | Faster pool for defended targets | [Buy 10 GB of premium residential](https://bit.ly/dataimPulse) |
| 5 TB+ | Premium residential | Custom quote | From $20,000 | Enterprise volume and negotiated terms | [Request premium residential pricing](https://bit.ly/dataimPulse) |

A few things about that table are worth saying out loud.

The residential grid is unusually flat. From the smallest purchase to roughly the 850 GB mark, the rate stays at $1/GB, and the only step down happens at 1 TB. So buying a "bigger plan" below a terabyte doesn't earn you a discount — it just makes the invoice larger. If you need 200 GB a month, you pay $200. There's no intermediate tier that rewards commitment, which is either refreshingly honest or useless, depending on whether you wanted a loyalty discount.

Mobile is the exception worth knowing about, because $2/GB is genuinely low for carrier IPs. Equivalent access from the enterprise-heavy vendors routinely runs several times that.

And the $5 minimum spreads differently across products: 5 GB of residential, 10 GB of datacenter, 2.5 GB of mobile, or 1 GB of premium residential. Nothing is charged automatically, and there's no card-on-file requirement forcing a renewal.

If you'd rather scope the dashboard before committing money, 👉 [open an account and look at the per-country IP counts first](https://bit.ly/dataimPulse) — the resource list is public, which is more than most vendors offer.

## Rotating or sticky: the setting that breaks more scrapers than IP quality

DataImpulse splits connections into two modes, and picking wrong causes failures that look like the proxy's fault when they aren't.

**Rotating** assigns a new IP on every request. HTTP/HTTPS traffic goes through port 823; SOCKS5 rotates on port 824. This is the default for high-volume crawling, SERP monitoring, price collection, or anything where you want requests distributed across thousands of exit nodes without managing a proxy list.

**Sticky** binds one IP to a specific port for a set window, so a sequence of requests looks like one consistent visitor. Ports sit in the 10000–20000 range. Documented session windows run from 1 minute up to 120 minutes, with 30 minutes as the default if you don't specify an interval.

The failure mode is predictable. Log into an account through a rotating gateway and you'll get bounced on the second request. Push high-volume crawling through sticky sessions and you'll burn through your exit nodes' reputations in an afternoon. Match the mode to the job, not to whatever the tutorial used.

## Targeting: what's free and what isn't

Country selection and country exclusion are included in the base residential rate. That covers most geotargeting needs — pulling Amazon.de pricing, checking local SERPs, verifying a campaign in Brazil.

State, city, ZIP, and specific-ASN selection are tiered differently, and here's where you should verify before budgeting: third-party write-ups on this topic disagree about whether those filters are billed at a 2× rate on standard residential plans or included at no surcharge. Some reviews say the surcharge applies; at least one says geotargeting is bundled. That's a genuine discrepancy in published material, not a rounding error, so treat precision targeting as a cost question to confirm with support rather than an assumption.

Premium residential is the tier where the targeting question stops mattering — the account manager and targeting options are part of the product.

## Where this stops being the right answer

The $1/GB rate is not a universal win, and pretending otherwise would make this useless.

**You need a managed scraping API.** DataImpulse is developer-first infrastructure. TechRadar's review notes there's no web unblocker or scraper API in the product — you write the request logic, the retries, and the CAPTCHA handling yourself. Integrations exist for Scrapy, Puppeteer, Playwright, Selenium, and a long list of antidetect browsers, plus code samples in Python, Node.js, PHP, C#, Go, Ruby, and cURL. If you want a vendor to solve unblocking for you, look at the enterprise names and pay their rates.

**Your volume is high and steady.** The discount only lands at 1 TB. Below that, a flat-rate competitor priced at $0.50/GB on a $50 bundle beats $1/GB the moment your monthly usage crosses roughly 50 GB, and keeps beating it. DataImpulse is strongest for irregular workloads, testing, and anything under that crossover.

**You need Tier-3 geographic depth.** Coverage in headline markets — US, UK, Germany, Japan, Brazil — is fine. Sub-Saharan Africa and Central Asia are thinner than what the ten-year veterans ship. Pull the published per-country IP counts before you buy if those regions are on your list.

**Enterprise procurement needs certifications.** This is a young company, founded in 2022. If your security review requires a documented audit trail and vendor history, that's a real constraint.

**You want a free trial.** There isn't one. The $5 intro is a paid test, not a giveaway. The trade-off is that it comes without business verification, automatic charging, or a three-day clock running down while you read documentation.

On the refund side: new users get a 7-day money-back guarantee on intro plans when paying by card, provided less than 80% of the traffic has been consumed. Cryptocurrency purchases aren't refundable. Read that condition against your test plan — 80% of 5 GB goes faster than people expect when they point a scraper at a JavaScript-heavy target.

## How to test it without wasting the $5

Five gigabytes is enough for a real evaluation if you spend it deliberately.

Write down your target list first. Then measure what actually matters: success rate per target, block rate, whether the exit IP geolocates where it claims, and latency on your specific sites. Run the same requests through the residential gateway with country targeting, checking whether your success rate justifies residential pricing over the $0.50/GB datacenter tier for each target class.

Most projects discover that only two or three of their targets genuinely need residential IPs. Routing the rest through datacenter traffic cuts the bill by half without touching success rates. That's the cost-per-successful-request calculation that matters; per-gigabyte pricing is just the input.

For context on where the market sits: Oxylabs publishes a residential ladder of 5 GB at $6/GB, 20 GB at $5/GB, 125 GB at $4/GB, and 1 TB at $2.50/GB. Those tiers multiply out exactly, which makes them a clean benchmark. The wider band of enterprise residential pricing runs somewhere between $3 and $8 per gigabyte depending on commitment — well above $1/GB, and well above the flat-rate competitors sitting near $0.50/GB at volume. DataImpulse occupies the low end of the pay-as-you-go segment rather than the cheapest slot overall.

## Questions people ask before buying

**Is this a subscription?** No. You top up a balance. There's no monthly minimum and no automatic charge.

**Does unused traffic expire?** No. Buy 100 GB, use 15, and the remaining 85 GB stays in your account until you consume it. This is the single biggest structural difference from subscription-based providers.

**What protocols are supported?** HTTP, HTTPS, and SOCKS5. Authentication works via username/password or IP whitelisting.

**Does it cover all four proxy types on one account?** Yes. Residential, datacenter, mobile, and premium residential sit behind the same pay-as-you-go balance, so you can route different jobs to different tiers without opening a second account.

**What are the published success rates?** The company publishes 99.51%. Independent review coverage reports Google SERP success near 99.7%, Amazon around 98%, and Cloudflare-fronted targets closer to 93%. Latency sits in the mid-tier band, with reported P50 around 740 ms. Cloudflare and social platforms are where residential boutiques pull ahead.

**How is support?** 24/7 human support via chat, email, and Telegram, plus setup tutorials. The G2 rating sits at 4.8/5.

## The short version

If you're searching "proxy residential" to buy rotating traffic at a predictable per-gigabyte rate for intermittent work, the pay-as-you-go model with non-expiring traffic solves the problem most subscription providers create: paying for bandwidth you don't use. The $5 entry lets you test against your real targets before committing, and the $1/GB rate holds from there until 1 TB.

If you're running above roughly 50 GB every month with no gaps, or you need a managed unblocking API, the flat-rate competitors and enterprise vendors earn their higher invoice. DataImpulse is the better tool for uneven workloads, tight budgets, and developer teams writing their own collection code — and a worse one for buying a solved scraping pipeline.

👉 [Check the current residential rates and start with $5](https://bit.ly/dataimPulse)
