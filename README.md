# Optimized Routes to China: AS9929 vs CN2 GIA, Which SixtyNet Plan Fits, and What the Price Table Doesn't Say Upfront

SixtyNet sells its China-optimized routing under a single label: **China Unicom's AS9929**. The plans that actually name that route are residential-IP VPS, and those ship with ports 80 and 443 closed, so they cannot serve a public website. If you want a China-facing site on this provider, the plans you'd really order are the DDoS-protected LAX series from **$200/year**, and the China route those ride is not spelled out in the product copy.

Both facts matter before you pay, because "optimized routes to China" is a category, not a specification. It can mean a Telecom line, a Unicom line, a Mobile line, all three, or a marketing sticker on a Los Angeles box that goes wherever it goes. Below is SixtyNet's full price list, what AS9929 does and does not cover, the annual-prepay math, and a test you can run before committing.

> **Quick pick:** If your workload is scraping, social accounts, or ad verification and you need a US IP that doesn't look like a datacenter, take a residential AS9929 plan and accept that it can't host a site. If you need a public site or API, take **LAX-STARTER at $200/year** (2 vCPU, 2 GB RAM, 40 GB NVMe, 5 TB traffic, DDoS protection) and get support to confirm the China route on the LAX line in writing first.
> 👉 [See the current SixtyNet VPS price list](https://sixtynet.net/aff.php?aff=39)

## Every plan on SixtyNet's price list

All prices below are USD, billed annually, exactly as shown on the VPS hosting page. The struck-through figure is SixtyNet's own list price; the "Save 17%" style discount is a prepay discount, not a coupon.

**DDoS-protected LAX series (datacenter IP, public web hosting)**

| Plan | vCPU / RAM / NVMe | Traffic / port | Price (USD/year) | Order |
| --- | --- | --- | --- | --- |
| LAX-STARTER | 2 / 2 GB / 40 GB | 5 TB / 2 Gbps | **$200** (list $240) | [ Order LAX-STARTER](https://sixtynet.net/aff.php?aff=39) |
| LAX-MICRO | 4 / 4 GB / 80 GB | 10 TB / 4 Gbps | **$400** (list $480) | [ Order LAX-MICRO](https://sixtynet.net/aff.php?aff=39) |
| LAX-MEDIUM | 8 / 8 GB / 160 GB | 20 TB / 10 Gbps | **$800** (list $960) | [ Order LAX-MEDIUM](https://sixtynet.net/aff.php?aff=39) |
| LAX-LARGE | 8 / 16 GB / 320 GB | 40 TB / 10 Gbps | **$1,600** (list $1,920) | [ Order LAX-LARGE](https://sixtynet.net/aff.php?aff=39) |

**Residential-IP plans and the Unicom BGP product**

| Plan | vCPU / RAM / NVMe | Traffic | China route named | Price (USD/year) | Order |
| --- | --- | --- | --- | --- | --- |
| Residential-STARTER | 2 / 2 GB / 40 GB | 5 TB | none | **$260** (list $300) | [ Order Residential-STARTER](https://sixtynet.net/aff.php?aff=39) |
| Residential-MEDIUM | 8 / 8 GB / 160 GB | 20 TB | none | **$860** (list $1,020) | [ Order Residential-MEDIUM](https://sixtynet.net/aff.php?aff=39) |
| Residential AS9929, 2 vCPU | 2 / 2 GB / 40 GB | 5 TB | AS9929 | not shown on the listing | [ Order the AS9929 residential plan](https://sixtynet.net/aff.php?aff=39) |
| Residential AS9929, 4 vCPU | 4 / 4 GB / 80 GB | 10 TB | AS9929 | not shown on the listing | [ Order the AS9929 4-core plan](https://sixtynet.net/aff.php?aff=39) |
| Los Angeles China Unicom-Premium | BGP session, 100 Mbps base, 3× burst | 95th-percentile billing | AS9929 | **$2,500** (list $3,000) | [ Order China Unicom-Premium](https://sixtynet.net/aff.php?aff=39) |

Two things about that second table. Every residential plan carries the same notice: **ports 80 and 443 are closed for "IP risk control" reasons**, so no public web service. The two AS9929 residential rows show the full spec block on the page, but the price fields for those specific SKUs did not render in the listing, and their refund note says refunds are issued as account credit only. If either of those is the one you want, ask for the price and the current refund terms in writing before checkout.

The top row of the table is not a VPS in the usual sense. Free BGP session setup, a 100 Mbps base rate with 3× burst, and 95th-percentile billing describe a bandwidth or BGP announcement product for someone with their own IP space and an ASN. Small hosting buyers should skip it.

## AS9929 is Unicom's premium line. CN2 GIA is Telecom's.

The naming is where most buyers get lost, and where several third-party write-ups about SixtyNet get it wrong.

**CN2 GIA** is China Telecom's second-generation carrier-grade network, AS4809. The part that matters is "end to end": GIA keeps traffic on the CN2 backbone in both directions, while the older CN2 GT only uses CN2 for part of the path. When a host advertises "three-network CN2 GIA return," it means the return path to all three Chinese carriers rides CN2 GIA; plenty of providers cover only one direction, or only one carrier, and still use the phrase.

**AS9929** is China Unicom's premium backbone. SixtyNet's own product pages name "China Unicom Premium AS9929" and "AS9929 Optimize for China," which is a Unicom-side product. At least one widely circulated English review of SixtyNet describes the network as "optimized routes for China Telecom CN2 GIA" across the lineup. The vendor's price list does not support that claim: the only China route it names anywhere is Unicom's.

Why you should care which one it is: China Telecom, China Unicom and China Mobile run largely separate networks, and a premium route on one carrier does nothing for users on another. If two-thirds of your audience is on Telecom and Mobile, a Unicom-only optimization covers the smallest slice of them. That distinction is also why providers who do offer all three tend to be explicit about it: V.PS, for example, names CTGNet for Telecom, CUP for Unicom and CMIN2 for Mobile as three separate products on the same plan, and notes in its own FAQ that the three behave differently because the carriers operate separate networks. SixtyNet's listing gives you one carrier and no per-carrier detail.

## What latency to actually expect

SixtyNet publishes no latency figures at all, so use the market benchmark for US West Coast premium routing: **roughly 160–180 ms to Beijing or Shanghai** on a good China Telecom route. That is a stable, usable number for web apps and SSH. It is not a local-feeling connection, and no route changes it, because the distance is the distance.

Be equally skeptical of any claim that an optimized route evens out performance across China. V.PS's own announcement for its China-optimized Tokyo and Singapore line states plainly that the routing does not change physical distance, will not make every region inside China behave identically, and cannot compensate for an undersized server. That is the most useful calibration sentence in this whole category, and it applies to SixtyNet by default: a $200 box with a good route is still a 2-core box.

## The money: annual prepay, no coupon codes, three-day refund

There are no SixtyNet coupon codes. The discount you see is baked into the billing cycle: pay for a year, get roughly 13–17% off the list price. That makes the year-one to year-two comparison simple in one direction and unknown in the other. LAX-STARTER costs $200 in year one and $200 in year two if renewal stays at the discounted annual rate; SixtyNet doesn't publish renewal pricing separately, so treat the list price of $240 as the ceiling you might be charged later.

Refunds deserve more attention than the discount. A third-party write-up puts SixtyNet's money-back window at **three days**, which is short next to the 30 days most hosts offer, and the AS9929 residential plans carry an additional restriction: refunds land as account credit, not back on your card. Neither restriction is hidden, but both are easy to miss when you're comparing headline prices. Confirm the current terms on the checkout page.

One more practical snag from the same third-party account: credit card payments were reported as suspended for fraud prevention at the time of writing. Check which payment methods are live before you plan around a card payment.

👉 [Check SixtyNet's current plans and checkout options](https://sixtynet.net/aff.php?aff=39)

## Who should not buy SixtyNet

Skip it if you need a server outside Los Angeles. The footprint is LA-only, with the datacenter described in third-party reviews as Coresite LA2 with Any2 peering; expansion has been talked about but nothing else is orderable. Skip it if you need managed support or hand-holding, and skip it if monthly billing matters, because every plan on the page is annual. Also skip it if what you want is documented three-carrier China routing for a website, because that is the one thing the lineup doesn't clearly sell.

For context, here is how the two most common alternatives in this niche are positioned. Information only, no endorsement implied:

| Provider | Locations | China route as documented | Entry price |
| --- | --- | --- | --- |
| V.PS | Tokyo, Singapore (Performance KVM line only) | CTGNet (Telecom), CUP (Unicom), CMIN2 (Mobile), all three included, no surcharge | Not published in the 2026-08-22 announcement |
| AkkoCloud | San Jose, Frankfurt, London | Triple-network CN2 GIA return, vendor's own description on an undated page | From ¥449/year for 1 vCPU / 1 GB / 15 GB / 800 GB in San Jose |
| SixtyNet | Los Angeles only | AS9929 (China Unicom) on named plans; no route named on the LAX line | $200/year (LAX-STARTER), $260/year (Residential-STARTER) |

The honest read: V.PS covers the most carriers but publishes no price, AkkoCloud competes on CN2 GIA at a lower entry point with dated-at-best pricing, and SixtyNet's differentiator is cheap residential IPs in Los Angeles rather than route breadth.

## How to check the route yourself

Ask support for a test IP before you order, then run a traceroute to it from a Chinese connection, ideally between 20:00 and 23:00 Beijing time when congestion peaks. Compare the hop count and the latency spread against a plain international route to the same city. A genuinely optimized path shows fewer hops and tighter variance, not necessarily a lower average.

If you do order, keep in mind that the IP you're assigned may differ from any test IP you were given, so re-run the traceroute on your own instance within the refund window. Three days is not much time, which is exactly why the test should be the first thing you do after delivery.

## FAQ

**Does every SixtyNet plan include a China-optimized route?**
No. Only the plans whose product name or spec list says AS9929 carry a named China route. The LAX series lists DDoS protection and a premium port but names no China route, despite what third-party reviews imply.

**Can I host a website on a residential plan?**
Not on standard ports. Ports 80 and 443 are closed on all residential plans by policy, so anything that has to answer on HTTP or HTTPS needs the LAX series instead.

**Can I specify which carrier's route I get?**
No. There is one named route, Unicom's AS9929. Telecom and Mobile users take whatever path the network gives them.

**Is there a promo code?**
No. Discounts come from paying annually, and the "Save 17%" labels are the gap between list price and the prepay price.

**What's the refund window?**
Three days according to third-party reporting, with AS9929 residential refunds paid as account credit. Verify on the checkout page before paying.

## Which one to order

Static site, API, or app backend with users in mainland China: **LAX-STARTER at $200/year** covers a small production workload, and LAX-MICRO at $400/year is the sensible step up if you need 4 cores and 10 TB. Get the China route confirmed in writing before you pay, because the LAX listing doesn't name one.

Scraping, social account management, ad verification, or anything that needs an IP that doesn't look like a datacenter: take one of the **AS9929 residential plans** and plan around the closed web ports. Ask for the price of those two SKUs directly, since the listing doesn't render it.

Own IP space and an ASN, announcing to China Unicom: the **China Unicom-Premium** product at $2,500/year is the one built for that, with free BGP session setup and 95th-percentile billing on a 100 Mbps base with 3× burst.

Before checkout, confirm two things: the current refund terms in writing, and which payment methods are actually live.

👉 [Start with the SixtyNet plan that matches your workload](https://sixtynet.net/aff.php?aff=39)
