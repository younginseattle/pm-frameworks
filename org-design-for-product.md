# Org Design for Product

How I structure PM orgs at different scales, job ladders, and what I've learned about hiring.

This is the framework I've built from building and leading PM orgs at Domotz (2x team growth, 0-to-1 structure), Puppet (multi-PM org through single-to-multi-product transition), and VMware Wavefront (cross-functional org across PM, engineering, and design). The specifics change with company stage and product complexity. The underlying principles don't.

---

## The core tension in PM org design

PM orgs are constantly pulled between two failure modes:

**Too product-aligned:** PMs own individual product areas and optimize them independently. Roadmaps diverge. Customer experience fragments. Platform decisions get made locally and create technical debt. PMs become feature owners, not product owners.

**Too function-aligned:** PMs are generalists attached to engineering teams without clear product ownership. Accountability diffuses. Nobody owns the customer experience end to end. PMs become project managers.

The org design question is always: where do you draw the ownership boundaries to get clear accountability without creating fragmentation?

There's no universal answer. The right structure depends on product architecture, customer segment complexity, and company stage. But the way I think about it is consistent.

---

## Structure by stage

### Early stage (1-3 PMs)

At this stage, structure is the wrong thing to optimize. The question is: do you have the right people covering the right problems?

One PM should own the core product loop: acquisition, activation, retention. If there's a second PM, they should own either platform/API (if technical depth is the differentiator) or GTM integration (if the sales and customer success motion is complex). A third PM usually means you're starting to have a portfolio problem worth organizing around.

At Domotz when I joined, the product org was underbuilt relative to the product's complexity. The first thing I did was not restructure -- it was hire. Get people who can own outcomes, not tasks, before you worry about org chart.

**What breaks at this stage:** Absence of structure means everything flows to the most senior PM (or the VP of Product). This is fine until it isn't. When you hit 15 to 20 engineers and are shipping multiple workstreams simultaneously, ad-hoc allocation starts causing problems. Build lightweight structure (clear ownership by product area, documented responsibilities) before you need it.

---

### Growth stage (4-8 PMs)

This is where structure starts to matter and where most orgs get it wrong.

The common mistake: hire PMs into specific engineering team slots and let the engineering org structure drive the PM org structure. This produces PMs who are highly aligned to engineering output and poorly aligned to customer problems.

The right approach: design PM ownership around customer problems and product surfaces, then map those to engineering team structures. The PM owns the customer problem. The engineering team is the resource they work with to solve it.

At Domotz, the structure I built organized PM ownership around:
- Core product (monitoring, alerting, device management) -- the primary customer workflow
- Platform and integrations (API, MCP, partner integrations) -- the extensibility surface
- Growth and commercial (trial, activation, pricing, packaging) -- the revenue mechanics

Each owned a clear problem space with measurable outcomes. Engineering team composition was secondary to problem space clarity.

**The job ladder at this stage:** Needs to exist before you have the hiring pressure that makes it feel urgent. A job ladder is not just about levels -- it's a communication tool that tells PMs what good looks like at each stage of their career and what they need to demonstrate to grow. Without it, performance conversations are arbitrary and retention suffers.

My job ladder for product management has four levels in the IC track:

- **PM:** Owns a feature area. Ships reliably. Clear on customer problems and product tradeoffs within their area. Executes well with direction.
- **Senior PM:** Owns a product surface. Defines the roadmap for their area, not just the backlog. Understands the commercial context of their decisions. Can drive alignment across engineering, design, and stakeholders.
- **Staff PM / Principal PM:** Owns a product or significant platform component. Sets strategy, not just roadmap. Influences beyond their immediate team. Makes calls that trade off across areas, not just within one.
- **Group PM / Director:** Owns a portfolio or product line with revenue accountability. Manages other PMs. Sets the operating model for their team. Represents product externally (customers, partners, investors).

---

### Scale stage (8+ PMs)

At this stage, the org design question shifts from structure to operating model. How do you maintain coherent product strategy when you have multiple teams with legitimate autonomy over their areas?

The answer I've found is: strong shared context, explicit coordination mechanisms, and ruthless clarity about what decisions belong where.

**Shared context** means every PM knows the company strategy, the revenue model, and the customer problems that matter most -- not just the ones in their area. This requires intentional communication: strategy reviews, customer research sharing, cross-team roadmap reviews. It doesn't happen on its own.

**Coordination mechanisms** means structured ways for teams that have dependencies to resolve them without escalating everything. At Puppet, this was a weekly cross-team roadmap review focused on dependencies and blockers, not status updates. At VMware, it was a shared prioritization framework that gave teams a common way to evaluate tradeoffs.

**Decision rights clarity** means explicit answers to: who can make this decision unilaterally, who needs to be consulted, and who needs to approve? The failure mode at scale is every important decision becoming a consensus process. Some decisions should be consensus. Most should not. Be explicit.

---

## What I look for when hiring PMs

The three things that predict PM success more than anything else:

**1. Evidence of taste.** Can they tell a good product from a bad one and explain why? Not in abstract terms but in specific, concrete observations. Good PMs notice things -- a confusing UI pattern, a metric that doesn't match the mental model, a feature that solves the wrong problem. This is partly native and partly trained, but it's visible in how someone talks about products they've used.

**2. Comfort with ambiguity and tradeoffs.** The job is constant prioritization under uncertainty. I give candidates a real prioritization scenario with incomplete information and conflicting constraints. I'm not looking for the "right" answer -- there isn't one. I'm looking for how they think through it: do they clarify the constraints, acknowledge the tradeoffs, and make a defensible call? Or do they look for a framework to follow?

**3. Commercial instinct.** PMs who don't think about revenue aren't running the full product job. I look for evidence that candidates understand how the products they've worked on made money, and that they made decisions with that in mind. Not every PM needs P&L ownership, but every PM should understand the commercial model well enough to know how their work affects it.

**What I've learned to discount:** Resume brand. Former Google and Facebook PMs can be excellent or average, same as anyone else. The brand tells you they passed a bar somewhere; it doesn't tell you much about how they'll perform in a different environment. Ask about specific decisions they made, not the companies they worked for.

---

## The biggest org mistakes I've made

**Promoting too early.** The temptation when you have a strong junior PM and an open senior role is to promote. Sometimes that's right. More often it creates a performance problem that's harder to manage than the open headcount. Be honest about readiness, not just potential.

**Underinvesting in onboarding.** Every PM I've hired took longer to be productive than I thought they would, and a significant part of that was my responsibility. The product context, the customer context, the commercial context -- these take time to absorb. Build structured onboarding (customer calls in week one, shadowing key workflows, explicit context documents) before you need it, not when you're trying to ramp a new hire under deadline pressure.

**Letting structure substitute for culture.** The right job ladder, the right team structure, the right OKR system -- none of it substitutes for the day-to-day work of building a team that trusts each other, has high standards, and gives each other honest feedback. Structure is the skeleton. Culture is everything else.

---

## A note on OKRs

OKRs work when they're used as a shared context tool and a prioritization forcing function. They fail when they become a performance management system or a reporting mechanism.

The questions OKRs should answer: what are we trying to accomplish this quarter? How will we know if we succeeded? What won't we do in order to focus on this?

The questions OKRs should not answer: is this person doing their job? Is this team on track? These require manager judgment, not a metric dashboard.

I use OKRs at the team level, not the individual level. Individual performance is managed through direct feedback, coaching, and performance conversations -- not through whether someone hit their key results. A PM who consistently hits key results through sandbagging is a worse performer than one who misses ambitious targets while doing genuinely important work. OKRs can't distinguish between these. Managers can.
