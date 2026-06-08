# Activation Metric Hierarchy

What to measure, in what order, and what to stop measuring.

This is the framework I use to cut through metric sprawl and identify the handful of numbers that actually tell you whether a product is working. Most product teams measure too many things and act on too few. The hierarchy is how I figure out which metrics deserve attention and in what sequence.

---

## The problem with metric lists

Most product teams have a dashboard with 20 to 40 metrics on it. They review it weekly. They notice when things move. They have limited ability to explain why things moved and even less ability to predict what to do about it.

The root cause is that the metrics aren't organized into a causal model. A list of numbers isn't a framework. A causal model -- where changing X causes Y, which causes Z -- is a framework.

The activation metric hierarchy is how I build that causal model for any product.

---

## The hierarchy

### Tier 1: The retention anchor

Start here, not at the top of the funnel.

The retention anchor is the behavior that most strongly predicts a customer still paying 12 months from now. Everything else in your metric hierarchy either leads to this behavior (and therefore matters) or doesn't (and therefore is noise).

Finding your retention anchor requires data. Pull your cohort of customers who churned in year one and your cohort of customers who renewed. What did the renewers do in their first 30 days that churners didn't? The intersection of high-frequency behaviors in the renewal cohort and low-frequency behaviors in the churn cohort is where your retention anchor lives.

At Domotz, the retention anchor was having at least one active alert rule per monitored site within the first 30 days. Customers who had that churned at under 2%. Customers who didn't churned at over 20%. Everything in our activation instrumentation pointed toward getting customers to that milestone.

At VMware Wavefront, the retention anchor was integrating the platform into an existing on-call workflow -- specifically, having at least one alert trigger a PagerDuty or OpsGenie notification within the first 60 days. SRE teams that did that didn't churn. SRE teams that used Wavefront as a monitoring dashboard without integrating it into their incident workflow churned at significantly higher rates.

**Action:** If you don't know your retention anchor, finding it is the first product analytics project. Everything downstream depends on it.

---

### Tier 2: Leading indicators of the retention anchor

Once you have the retention anchor, work backwards. What has to happen before a customer reaches it?

For each step in the path, you want to know:
- What percentage of customers complete this step?
- How long does it take?
- What happens to customers who skip it?

This gives you a funnel with real causal structure. Not "signups to activations to conversions" (which is descriptive) but "setup completion to first device connected to first alert configured to first alert triggered" (which is causal and actionable).

At Domotz:
- Setup completion (created account, connected first device): ~85% of trials
- First alert configured: ~55% of trials
- First alert triggered: ~40% of trials
- Retention anchor achieved (alert rule per site): ~35% of trials

The biggest drop was between "first alert configured" and "first alert triggered." That told us customers were setting up alerting correctly but their devices weren't generating the kind of events that would trigger alerts. The fix was in onboarding: we added a guided "test your first alert" step that simulated a device event, which moved that conversion rate from 40% to 58%.

---

### Tier 3: Engagement quality indicators

Not all usage is equal. Tier 3 metrics tell you whether customers who are using the product are getting deep value or surface value.

Depth indicators:
- Feature breadth (how many distinct features has a customer used?)
- Integration count (how many external systems has the product connected to?)
- Configuration depth (how customized is their setup?)
- Return visit frequency without prompting (are they coming back on their own?)

The distinction between engagement quantity and engagement quality matters for churn prediction. A customer who logs in daily to check a single dashboard is less sticky than a customer who logs in three times a week but has configured complex alerting rules, integrated with their ticketing system, and invited three teammates. The second customer is embedded. The first customer is at risk.

**What to avoid:** Measuring session count, page views, or login frequency as quality signals. These measure activity, not value.

---

### Tier 4: Expansion signals

The behaviors that indicate a customer is growing into the product, not just using it.

These are the signals that drive expansion revenue conversations. They're worth tracking separately from general engagement because they require different action: a CSM conversation about a higher-tier plan, a check-in about additional use cases, an offer to do a deeper product review.

Strong expansion signals are product-specific but generally fall into three categories:

**Capacity expansion:** Using more of the product's core unit (more devices, more seats, more data volume). Approaching or exceeding limits on current plan.

**Capability expansion:** Adopting features in the product that they weren't originally using. This is especially meaningful when the features adopted are in a higher pricing tier.

**Ecosystem expansion:** Connecting the product to more external systems, adding more team members, building integrations. The product is becoming part of their infrastructure rather than a standalone tool.

At Domotz, the strongest single expansion signal was device count crossing 80% of plan capacity. That triggered an automated notification to the CSM and a suggested outreach template. Accounts that were contacted before they hit 100% capacity expanded at significantly higher rates than accounts that were contacted after they hit the limit (and received a disruptive "you've exceeded your plan" message).

---

### Tier 5: Health indicators

These are the canary metrics -- early warning signals that something is wrong before churn shows up in the data.

**Support volume per account:** A spike in support tickets, especially for basic functionality questions, often precedes churn by 30 to 60 days. It's a signal that the customer is struggling and hasn't found a self-serve path to resolution.

**Feature regression:** A customer who was using 5 features last month and is now using 2 is at risk. Regression in usage depth is a reliable churn predictor.

**Admin login frequency:** In B2B products, the admin is usually the buyer. If the admin stops logging in, the renewal is at risk regardless of what other users are doing.

**Integration disconnection:** If a customer disconnects an integration they previously had, something changed -- either in their workflow, their team, or their evaluation of the product. It warrants a check-in.

---

## What to stop measuring

**Vanity metrics to cut from your dashboard:**

- Total registered users (measures signups, not value)
- Page views and session duration (measures engagement quantity, not quality)
- Feature release count (measures output, not outcome)
- NPS in isolation (useful only when paired with verbatims and segmented by cohort)
- Social shares and referral clicks that don't convert to T1V

The test: if a metric went up and you can't describe the product decision you'd make differently, it doesn't belong on your core dashboard. Put it in a secondary view for context, but don't let it compete for attention with your Tier 1 through 3 metrics.

---

## The sequencing principle

This is the most important thing in the hierarchy: sequence matters.

Fix Tier 1 before you invest in Tier 2. Know your retention anchor before you optimize leading indicators. The leading indicators only matter if they actually lead to the retention anchor -- and you can't know that without first identifying what the anchor is.

Teams that skip this and go straight to optimizing signup flow, email onboarding sequences, and feature tooltips are optimizing unknown variables against an unmeasured outcome. That's how you get three quarters of A/B tests that move the measured metric in the right direction but don't affect retention.

Start with retention. Work backwards. Optimize in that order.
