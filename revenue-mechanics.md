# Revenue Mechanics

Unit economics, expansion loops, and how logo growth and ARR growth diverge.

This is the framework I use when I'm thinking about revenue architecture -- not just "what's the pricing model" but how the different parts of the revenue system connect and reinforce each other. Built from running commercial models at Domotz and VMware Wavefront with direct P&L accountability.

---

## Logo growth vs. ARR growth

These are different businesses with different product strategies. Most teams treat them as the same thing and end up with a muddled approach to both.

**Logo growth** is about acquisition and conversion. New customers. New logos. The product strategy question is: how do we get the right customers in the door, get them to first value fast, and convert them to paid?

**ARR growth** is about expansion and retention. Existing customers. The product strategy question is: how do we make the product more valuable to customers who are already paying, and how do we capture that value?

The two diverge in interesting ways:

A product can have strong logo growth and weak ARR growth. This usually means: good acquisition and activation, poor expansion mechanics, high churn offsetting new logo revenue. The revenue treadmill. You're running fast and staying in place.

A product can have weak logo growth and strong ARR growth. This usually means: the product is deeply embedded with existing customers who are expanding, but the self-serve or PLG motion isn't working for new acquisition. Common in enterprise products that grew through direct sales.

The goal is both, but most products need to solve one before they can effectively solve the other. At Domotz, we had the logo growth but the ARR growth was underpowered because the expansion motion wasn't designed in. Fixing the pricing model (site to device) and building the expansion instrumentation unlocked ARR growth that the logo growth had been setting up but not capturing.

---

## The unit economics that actually matter

Not all unit economics are equally useful for product decisions. Here's the hierarchy I use:

### CAC payback period

How long does it take to recover the cost of acquiring a customer? This matters for product decisions because it tells you how much you can invest in onboarding and activation before the economics break.

If your CAC payback period is 18 months, you have 18 months of customer lifetime to work with before you've broken even. An onboarding process that takes 3 weeks to get to value is expensive in that context. An onboarding process that gets to value in 2 hours changes the math significantly.

At Domotz, cutting T1V from 2+ hours to under 30 minutes in the enterprise segment directly reduced effective CAC by compressing time-to-productivity and reducing the CSM hours required per new customer.

### Net Revenue Retention (NRR)

The single most important metric for understanding whether your revenue model is working. NRR above 100% means your existing customer base is growing -- expansion is outpacing churn. Below 100% means you're losing ground in your existing base regardless of what new logos you're adding.

NRR is a product metric as much as a sales metric. The expansion it captures comes from:
- Customers hitting plan limits and upgrading (requires usage-aligned pricing)
- Customers adopting new features that cost more (requires a clear upgrade path)
- Customers expanding to more seats, sites, or units (requires embedded value)

All three are product design decisions. If your NRR is below 100%, the first diagnostic question is: which of these three is failing?

At VMware Wavefront, NRR improvement from churn reduction (20% to 7%) was the primary revenue lever. At Domotz, NRR improvement from expansion (device growth, plan upgrades) was the primary lever. Same metric, different root cause, different product intervention.

### Gross margin by segment

Not all revenue is equal. A segment with high support volume, frequent customization requests, and low expansion rate generates less profitable revenue than a segment that self-serves, expands predictably, and rarely needs intervention.

This matters for product prioritization: investing in the high-margin segment generates more durable value than investing in the low-margin segment, even if the low-margin segment is larger by revenue.

At Domotz, MSP customers and enterprise IT customers had meaningfully different support costs and expansion rates. Understanding that shaped which segment got product investment priority.

---

## Expansion loops

An expansion loop is a mechanism where using the product more generates more value, which drives more usage, which drives more revenue. This is the product design version of the land-and-expand model.

Expansion loops require:

**1. A value driver that scales with usage.** The product has to be more valuable when it's used more. In network monitoring, more devices under management means more comprehensive visibility. In observability, more signals means better incident correlation. In infrastructure automation, more endpoints means broader coverage. The product has to be designed around a value metric that naturally grows.

**2. A pricing model aligned to that value metric.** If you're charging per site and value scales with devices, you've broken the expansion loop. The customer can double their value without increasing their spending. The pricing transformation at Domotz was specifically about reconnecting the pricing unit (site) to the actual value driver (device count).

**3. An expansion signal that triggers an upgrade conversation.** The loop doesn't close automatically. Someone has to initiate the upgrade conversation at the right moment. That requires instrumentation (know when a customer is approaching capacity), a CSM or automated motion (initiate the conversation), and a clear upgrade path (make the ask obvious and low-friction).

**4. A product experience that makes expansion natural.** Adding a device to Domotz should feel like using the product, not like a purchasing decision. The more you can make expansion feel like product adoption rather than commercial negotiation, the higher your conversion rate.

---

## The churn equation

Churn is not one thing. Distinguishing the types matters for product intervention:

**Involuntary churn:** Payment failures, credit card expiry. Addressed with dunning flows, payment retry logic, payment method updates. This is an ops problem, not a product problem.

**Time-to-value churn:** Customers who signed up, didn't get to first value fast enough, and left before they had a reason to stay. Addressed by T1V reduction and activation intervention. This is a product problem.

**Value gap churn:** Customers who got to first value but found the product's ongoing value insufficient relative to cost. Addressed by product investment and pricing calibration. This is a product and pricing problem.

**Relationship churn:** Key champion left the company, new stakeholder brought in a competing product, company was acquired. Limited product intervention available. Addressed by multi-threading relationships and embedding the product deeply enough that no single stakeholder departure is catastrophic.

**Budget churn:** Customers who valued the product but couldn't justify the cost. Addressed by demonstrating ROI clearly and building ROI calculators into the product experience.

The distribution matters. At Domotz, the churn we cut was primarily T1V churn and value gap churn. At Wavefront, it was a combination of T1V churn (customers who couldn't get the platform integrated into their workflow) and relationship churn (the VMware acquisition caused some customer uncertainty). Different distributions require different interventions.

---

## The revenue architecture diagnostic

When I'm looking at a product's revenue mechanics for the first time, here are the questions I ask in sequence:

1. What's the NRR? Is expansion outpacing churn?
2. What's the CAC payback period? Is acquisition economics sustainable?
3. Where is churn concentrated? T1V, value gap, relationship, or budget?
4. Does the pricing unit align with the primary value driver?
5. Is there a functioning expansion loop? Where does it break?
6. What's the gross margin by segment? Which segments are worth investing in?
7. What's the distribution of revenue between logo growth and expansion? Is the balance right for the stage of the business?

The answers to these seven questions tell you more about what to do with the product than almost any other diagnostic.

---

## What I've learned

**Revenue mechanics are product decisions.** The pricing model, the expansion loop, the upgrade path -- these are designed in the product, not just in the commercial terms. PMs who treat revenue mechanics as a finance or sales problem own less of the outcome than they should.

**NRR is the most honest signal.** Logo growth can mask a broken retention and expansion model for years. NRR can't be gamed. If it's below 100%, something in the product or pricing is wrong.

**Align the pricing unit before you build the expansion motion.** It's very hard to build an expansion loop when the pricing doesn't capture the value driver. Fix the model first, then build the motion on top of it.
