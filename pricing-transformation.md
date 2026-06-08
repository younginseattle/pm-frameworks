# Pricing Transformation Playbook

How to replace a broken pricing model without burning your customer base.

This is the framework I built running a pricing transformation at Domotz -- moving from a site-based model to a device-based model across a customer base of MSPs and enterprise IT teams. Churn dropped to sub-2% and ARR grew double digits through the transition. It did not go smoothly at first.

---

## The problem pricing transformation is actually solving

Most SaaS pricing discussions focus on the model itself: per seat, per usage, per outcome. That's the wrong starting point.

The real question is: **does your pricing unit align with the value your customer actually receives?**

When it doesn't, you get one of two failure modes:

**Failure mode 1: You're leaving money on the table.** Customers are getting significantly more value than they're paying for. They renew easily but you can't grow revenue without adding logos. Expansion is invisible.

**Failure mode 2: You're extracting value that customers don't feel.** Customers are paying for something that doesn't map to how they experience the product. Renewals require justification conversations. Churn is a pricing problem disguised as a product problem.

The Domotz situation was failure mode 1. The site-based model meant a customer managing 50 devices on one site paid the same as a customer managing 500 devices on the same site. No expansion motion. No way to grow ARR without winning new logos.

The switch to device-based pricing fixed the alignment problem. But the transition is where the real work is.

---

## The framework

### Phase 1: Diagnose before you design

Before deciding on the new model, understand three things:

**1. What does value actually look like for your best customers?**
Not what you think it is. Talk to your highest-NPS, lowest-churn, highest-expansion customers. Ask them: when do you feel like this product is earning its cost? What would have to break for you to start evaluating alternatives?

At Domotz, the answer was consistent: value scaled with the number of devices under management, not with the number of sites. A customer who doubled their device count felt twice the value. A customer who opened a second site didn't necessarily feel more value -- they felt more complexity.

**2. What does your customer segmentation look like under the new model?**
Run the math before you commit. Segment your existing customers into winners, neutrals, and losers under the proposed new model. Winners (customers who will pay less or the same) are easy. Neutrals need a clean migration path. Losers are the risk.

At Domotz, a subset of customers had very high device density relative to their site count. They were going to see material price increases. Knowing this in advance shaped the migration approach.

**3. What's your competitive exposure?**
If you reprice up and a competitor doesn't, you've handed them a sales argument. Understand your competitive pricing position before you move.

---

### Phase 2: Design the migration, not just the model

The new pricing model is the easy part. The migration is where most transformations fail.

**Grandfather strategically, not universally.**
The instinct is to grandfather all existing customers to protect churn. Don't. Universal grandfathering kills the revenue upside and signals that the new model is negotiable. Grandfather selectively: customers who would face genuinely punishing increases, long-tenure customers with strong relationships, customers in key segments you can't afford to lose.

Be explicit about the criteria internally. Grandfathering decisions made case-by-case by the sales team become inconsistent and create customer perception problems later.

**Set a migration timeline and hold it.**
Indefinite grandfathering is the worst outcome. It splits your customer base permanently and creates a growing gap between your "real" pricing and your effective pricing. Set a timeline -- 12 to 24 months is typical -- and communicate it clearly at the time of the transition.

**Design the upsell motion before you flip the switch.**
Device-based pricing only drives expansion revenue if your customer success and sales teams have a motion for it. What's the trigger to have an expansion conversation? What does the conversation sound like? What's the objection handling? This needs to exist before the model goes live, not after.

---

### Phase 3: Instrument the transition

Pricing transformations generate unusual signals that your standard metrics won't capture cleanly. You need to watch for them explicitly.

**Churn attribution during transition.** Some customers will churn during a pricing change who would have churned anyway. Don't let the sales team attribute all transition-period churn to pricing -- it will distort your read on the model's performance. Build a churn attribution process that separates pricing-related churn from underlying product or relationship churn.

**Expansion rate by cohort.** The whole point of moving to a value-aligned model is to unlock expansion. Measure expansion ARR by customer cohort from migration date. If you don't see expansion motion within 6 months of migration, something is broken -- either the model, the motion, or the instrumentation.

**NPS delta by customer segment.** Run NPS before and after the transition for each segment: winners, neutrals, losers. Losers who stay are at risk. Understand why they stayed and whether their NPS recovers over time.

**Customer support volume.** A pricing change should generate a spike in support contacts. If it doesn't, customers didn't understand the change. If the spike is larger than expected, the change wasn't communicated clearly enough.

---

### Phase 4: Communicate like a human

Pricing change communication fails in two ways: it's too corporate (customers feel managed) or it's too apologetic (customers feel like they're being asked to accept something unfair).

The right framing is direct and honest:

- Here's what's changing and when
- Here's why (explain the value alignment argument -- customers respect it more than you'd expect)
- Here's what it means for your account specifically
- Here's who to talk to if you have questions

Do not hide the change in a terms update email. Do not let customers find out at renewal. Do not have the first conversation about pricing happen when a customer is already frustrated.

At Domotz, the customers who churned during the transition almost universally had one thing in common: they felt surprised. The customers who stayed -- including some who faced significant price increases -- had been talked to directly before the change landed.

---

## What broke

**We underestimated the density outliers.** A small number of customers had extreme device-to-site ratios that we hadn't fully modeled. The price increase for those customers was larger than we'd anticipated and the conversations were harder than they needed to be. Run the tail more carefully than the median.

**The expansion motion wasn't ready when the model launched.** We changed the pricing before we had a fully designed expansion conversation for customer success to run. The model was right but the revenue motion lagged by about a quarter. Don't let the pricing change get ahead of the GTM readiness.

**Grandfathering criteria drifted.** We set clear criteria internally but the decisions started being made ad hoc by account managers under pressure. By month three we had inconsistent treatment across similar accounts. We had to rebuild the criteria and communicate more explicitly about who had been grandfathered and why.

---

## What I'd do differently

Start the migration motion design six months before the pricing change, not two weeks before. The model change is a one-time decision. The motion that extracts value from the new model runs for years.

Build the customer segmentation model before you finalize the pricing structure. The right model depends on what the transition looks like for your specific customer base. Generic best practices are a starting point, not an answer.

Run a pilot. Pick a cohort of 20 to 30 customers -- a mix of segments -- and migrate them first. You will learn things that change how you approach the full rollout. The cost of a pilot is low. The cost of a flawed full rollout is not.

---

## The result

Sub-2% churn through and after the transition. Double-digit ARR growth. Expansion motion that didn't exist under the site model became a meaningful part of the revenue picture within two quarters of migration completion.

The model was right. The transition was harder than it needed to be. Both things are true.
