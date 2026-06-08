# PLG Funnel Model

How I instrument product-led growth: activation hierarchy, trial mechanics, and expansion signals.

This is the framework I use when I'm thinking about a PLG motion from scratch or diagnosing one that isn't working. Built from work at Domotz (network monitoring SaaS, MSP and enterprise buyers) and VMware Wavefront (observability platform, SRE and platform engineering buyers). The specifics differ but the underlying structure is the same.

---

## The core problem with most PLG instrumentation

Most teams instrument their funnel top-down: signups, activations, conversions. They measure what's easy to measure, not what actually predicts retention.

The result is a dashboard full of vanity metrics and a genuine mystery about why trial-to-paid conversion is stuck at 8%.

The right approach is to work backwards from retention. Ask: what behavior in the first 30 days predicts a customer who's still paying 12 months later? Then instrument for that. Everything else is noise until you've answered that question.

---

## The funnel I actually use

### Layer 1: Acquisition signal quality

Before you touch activation, understand where your paying customers actually came from. Not your trial signups -- your paying customers.

The gap between "where trials come from" and "where paying customers come from" tells you a lot. If 40% of your trials come from paid search but 80% of your paying customers came from organic or word of mouth, you're spending acquisition budget on the wrong channel and optimizing activation for the wrong intent signal.

At Domotz, the highest-quality acquisition signal was peer referral from other MSPs. Those customers activated faster, churned less, and expanded more. Understanding that shaped how we weighted acquisition investments.

**What to track:** Source-to-paying-customer rate by channel, not source-to-trial rate. Time-to-first-payment by acquisition source. ACV by acquisition source.

---

### Layer 2: Time to first value (T1V)

The single most predictive metric in early trial behavior. How long does it take a new user to get to the moment where the product has done something useful for them?

"Useful" is product-specific and has to be defined explicitly. It is not "completed onboarding." It is not "created an account." It is the first moment when the product has delivered something the user actually needed.

At Domotz, first value was defined as: first time a user received an alert on a device they had connected. Not "connected a device" (that's setup completion, not value). Not "viewed the dashboard" (that's engagement, not value). The alert moment was the first time the product was doing its job.

We cut enterprise T1V from over 2 hours to under 30 minutes by working backwards from that definition and removing every step between signup and first alert that wasn't necessary.

**What to track:** Median T1V, T1V by segment and acquisition source, T1V by plan type, percentage of trials that never reach T1V (this is your biggest churn predictor).

---

### Layer 3: Activation milestone hierarchy

Not all product usage predicts retention equally. There's a hierarchy of behaviors, and you need to know which ones matter.

The framework I use:

**Level 1 -- Setup completion:** Did they complete the basic configuration to get the product working? This is table stakes. Trials that don't reach setup completion within 48 hours have very low conversion rates. Optimize this first.

**Level 2 -- First value event:** Defined above. Did they get the product to do the thing it's supposed to do?

**Level 3 -- Habit formation events:** Did they return on day 3, day 7, and day 14? Retention in SaaS products almost always follows a pattern: if a user comes back on their own within the first week without a prompt, conversion probability goes up significantly. If they don't, no amount of email nudging fully recovers it.

**Level 4 -- Expansion signal events:** Did they connect more devices, invite a teammate, integrate with another system? These behaviors indicate the product is becoming embedded. They're the leading indicator of expansion revenue and a strong churn predictor in the opposite direction.

The key insight: you need to know the conversion rate at each level transition, not just the overall trial-to-paid rate. If 80% of trials reach setup completion but only 40% reach first value, your problem is in the T1V gap. If 80% reach first value but only 30% show habit formation, your problem is in the return visit experience. These are completely different problems requiring different solutions.

**What to track:** Conversion rate at each level transition, time-in-level before transition, percentage that stall at each level, and the downstream conversion rate for users who pass each level vs. those who don't.

---

### Layer 4: Trial outcome segmentation

Not all trials should be treated the same during the trial period. Segment them and treat them differently.

**High intent, high activation:** They're moving through the funnel on their own. Don't over-communicate. A check-in at day 7 is enough. Over-emailing this segment trains them to ignore your emails.

**High intent, low activation:** They signed up for a real reason but got stuck. These are your highest-value intervention targets. Identify the stall point and intervene specifically. "I noticed you connected your first device but haven't set up alerting yet -- here's how" converts better than a generic "tips for getting started."

**Low intent, high activation:** They're using the product but you're not sure why. These often come from viral or accidental acquisition. Watch them -- some convert to paid, many don't.

**Low intent, low activation:** Don't spend much on these. They signed up and left. Move on.

**What to track:** Segment distribution at day 3, day 7, and day 14. Conversion rate by segment. Email engagement rate by segment (used to refine segmentation rules).

---

### Layer 5: Expansion signals

In B2B SaaS, the trial-to-paid conversion is often not where the real revenue growth lives. Expansion within paying accounts is. Most PLG teams underinstrument this.

The expansion signals that matter most are the ones that indicate the product is becoming load-bearing -- embedded in a workflow that would be painful to remove.

At Domotz, the strongest expansion signals were: number of devices under management (correlated with both plan tier and renewal rate), number of integrations connected (correlated with renewal rate), and whether the account had created custom alerting rules (correlated with expansion ARR).

These weren't just nice-to-know metrics. They were built into the CSM motion: accounts above certain thresholds on these signals got proactive outreach about higher-tier plans. Accounts below them got different outreach focused on driving depth.

**What to track:** Expansion signal events by account, time from conversion to first expansion signal, correlation between expansion signals and renewal rate, expansion ARR as a percentage of total ARR.

---

## What breaks in practice

**Defining first value poorly.** The most common mistake. Teams define first value as "completed onboarding" or "logged in twice" because it's easy to measure. That's not value, that's activity. Get specific about what the product actually has to do for the user to have received value, and instrument that.

**Ignoring the segment distribution.** You can have a 15% trial-to-paid conversion rate that looks fine in aggregate but masks a serious problem: if 50% of your trials are high-intent and you're only converting 30% of them, something is broken. Segment before you evaluate conversion rates.

**Optimizing the top of the funnel before fixing the bottom.** More trials into a broken activation experience just generates more churn. Before you invest in acquisition, make sure you know your T1V and your level-transition conversion rates. The ROI on fixing activation almost always beats the ROI on increasing trial volume.

**Treating expansion as a sales problem.** Expansion signals are a product instrumentation problem first. If your product isn't generating the data that tells CSMs and sales when an account is ready to expand, you're leaving revenue on the table regardless of how good your sales team is.

---

## What I'd do differently

Build the expansion instrumentation before you launch the PLG motion, not after you've hit your first 1,000 paying customers. Retrofitting expansion signal tracking into an established product is significantly harder than building it in from the start.

Define T1V before you write the first line of onboarding code. It shapes every decision about what the onboarding flow needs to do. Teams that define it after onboarding is built usually end up with onboarding optimized for setup completion, not for value delivery.

---

## The result at Domotz

Sub-2% churn. T1V cut by 50% in the enterprise segment. Expansion motion that contributed meaningfully to double-digit ARR growth within two quarters of full instrumentation.

The instrumentation didn't drive those results by itself. But it made every other decision -- where to invest engineering, which CSM motions to prioritize, where the roadmap needed to go -- significantly more defensible.
