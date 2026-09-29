# To: Priya Raman, Head of Customer Experience
## Vireo Audio Support — Set E

### Decision in one line
Billing is the largest team in the stated Jan 2025–Jun 2026 window (2,425 tickets; 20.8%), ahead of Logistics (1,905; 16.4%), but the data does not by itself justify committing two hires. I would fix Billing's intake/SLA process first and measure the result.

### What I built
I built a small AI-assisted categorisation tool using the customer's opening message plus the agent's closing note. It preserves the existing intake tag and adds an independently generated category. It also produces monthly category and team breakdowns.

The historical tags are not treated as truth: the email says the bot sets them at ticket creation and agents rarely retag. The model therefore learns from a noisy operational label and the validation explicitly separates model agreement with historical tags from a small human audit.

### What the data says
Across 11,641 tickets in the requested 18-month window:
- Billing: 2,425 tickets (20.8%)
- Logistics: 1,905 (16.4%)
- Chat Frontline: 3,030 (26.0%)
- Email Frontline: 1,807 (15.5%)
- Returns Desk: 1,049 (9.0%)
- Voice Frontline: 900 (7.7%)
- Escalations & Warranty: 525 (4.5%)

Billing also has the highest first-response breach rate among the teams at 19.7%: 477 breaches. At the policy rate of Rs 350 per breach, that is Rs 166,950 in SLA credits over the window.

The recorded Billing transfer count is 632 where the transfer field exists, equivalent to Rs 192,760 at Rs 305 per transfer. Legacy rows have blank transfer values, so this is not an exhaustive transfer cost.

### Business target
**Reduce Billing's first-response breach rate from 19.7% to 10%.**

At the observed 2,425-ticket volume, moving to 10% implies roughly 235 fewer breaches over 18 months:

**235 × Rs 350 = about Rs 82,250 saved over 18 months, or about Rs 54,800 annualised.**

That is deliberately smaller than the stated Rs 9 lakh/year cost of two hires. The point is to test whether a process/routing fix can remove a material part of the problem before adding permanent cost.

### What I changed in the ask
I kept the requested monthly category/team charts. I did not, however, treat “largest queue = two hires” as a sufficient staffing conclusion. The email thread itself contains a competing operational signal: Logistics reports day-plus resolution times and hand-offs. The policy also says Tier 2 must not be compared with Tier 1 on volume metrics.

My recommendation is therefore: use Billing as the first investigation target because it is the largest Tier 1 queue and has the highest breach rate, but do not automatically approve two hires until the process experiment is measured.

### How I know the categoriser works
Five-fold cross-validation against the historical intake tags gives **83.8% accuracy** (standard deviation about 0.4 percentage points). This is not a true accuracy estimate because the tags are the thing we are questioning.

I therefore also manually reviewed a stratified sample of **66 tickets** across the predicted categories. The model output agreed with the manual review on **59/66 = 89.4%**. The main errors were “Other” tickets whose notes clearly described cancellations or delivery issues, plus a small number of connectivity/billing cases.

### Known data problems
- The export contains 139 rows outside the stated Jan 2025–Jun 2026 window; these are excluded.
- Transfers are blank on legacy rows by design and are not treated as zero.
- Some records have negative first-response-to-resolution durations; I did not use these for staffing-cost calculations.
- CSAT blanks are treated as no response, not zero.
- The model uses historical categories as training labels, so it can reproduce some historical tagging bias.
- The manual audit is small and model-assisted; it is not an independently adjudicated gold dataset.

### Scope deliberately left out
I did not build a workforce simulation or claim that handle time can support staffing capacity. The source contains timestamp inconsistencies that make that unsafe. I also did not build a full production service/API; for this five-hour exercise, a reproducible local tool and evidence trail are more useful.

