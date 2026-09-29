# Vireo Audio — Task 1 V2 Submission

**What did you build, and what business outcome does it move? State the number and the money.**

Built an AI-assisted ticket categoriser using the customer opening message and agent closing note, plus monthly category/team reporting.

Business target: reduce Billing's first-response SLA breach rate from 19.7% to 10%. At the observed 2,425 Billing tickets, that is about 235 fewer breaches over 18 months. At Rs 350 per breach, that is approximately Rs 82,250 saved over 18 months, or Rs 54,800 annualised.

**What does one run cost, and what would a month cost at Vireo's volume (roughly 650 tickets a week)? Show the arithmetic. If you used no paid calls, say so.**

No paid model/API calls. Run cost for the submitted implementation: Rs 0 in paid inference/API charges.

The classifier runs locally using scikit-learn. At roughly 650 tickets/week, there would be about 2,817 tickets/month. Because inference is local rather than API-priced, incremental model-call cost remains Rs 0; compute cost depends on Vireo's machine.

**How do you know it works? Sample size, how you checked, error rate, and the kind of case it gets wrong.**

5-fold cross-validation against historical tags: 83.8% accuracy, SD about 0.4 percentage points.

Manual audit: 66 stratified tickets, 59 correct = 89.4% agreement.

Most manual-audit errors were historical “Other” tickets where the text/agent note clearly indicated cancellation or delivery. There were also isolated connectivity/billing classification errors.

**Did you change, narrow, or push back on the client's ask? What, when, and why?**

I kept the requested monthly category/team charts.

I pushed back on the automatic “largest team gets two hires” conclusion. Billing is the largest team in the stated window, but two hires cost about Rs 9 lakh/year and the data also shows a process signal: Billing has a 19.7% first-response breach rate. I would test an intake/routing/SLA intervention before committing the full hiring cost.

I also excluded Tier 2 from any volume-based staffing comparison because the support policy explicitly says Tier 2 is measured on resolution in days and should not be compared with Tier 1 on volume.

**What is wrong with what you are handing us? Be specific.**

- Historical category tags are noisy training labels.
- The manual audit is only 66 tickets and is model-assisted.
- Legacy transfer values are blank rather than zero.
- Some tickets have negative handle durations, so I did not use handle time for staffing-cost claims.
- The classifier is a local text model, not a production API.
- It does not automatically discover new categories.

**What did you deliberately leave out, and why that rather than something else?**

I left out a workforce-capacity simulation because the source timestamps are not reliable enough for a defensible staffing-hours calculation. I also left out a production web application because the five-hour constraint favours a small reproducible tool with a validation trail over UI polish.

**Anything you built or found that nobody asked for?**

I added a data-quality report and a manual-audit file. I also preserved the original category alongside the AI category so Vireo can inspect exactly where the intake bot and model disagree.

**What did you use AI for? Which tools and models, where they helped, where they wasted your time, what you threw away. Link your three-minute screen recording here.**

Used ChatGPT (GPT-5.6 Luna) for analysis planning, implementation assistance, review of the business logic, and drafting the client-facing memo.

The categorisation model itself is local scikit-learn TF-IDF + Linear SVM; no paid external model calls were used.

AI was useful for quickly testing alternative approaches and identifying data-quality traps. I discarded the idea of building a large dashboard/API first because it would add surface area without improving the core evidence.

Screen recording: **[PASTE PUBLIC GOOGLE DRIVE LINK]**

**Your Public Google Drive Link**

**[PASTE PUBLIC GOOGLE DRIVE LINK]**

**Someone picks this up on Monday and you are unreachable. The three things they need to know.**

1. Run `pip install -r requirements.txt`, then `python app.py --data-dir data --output-dir outputs`.
2. Treat `category` as the historical intake tag and `ai_category` as the model output; neither is an independently adjudicated truth set.
3. Do not use the existing handle-time fields for staffing-cost modelling without first fixing the timestamp inconsistencies.

**Honest hours spent.**

**[ENTER YOUR ACTUAL HOURS]**

**Github Repo Link**

**[PASTE PUBLIC GITHUB URL]**
