# Validation summary

## Historical-tag cross-validation
5-fold stratified CV against the historical `category` tag:

- Accuracy: **83.8%**
- Standard deviation: **0.4%**
- Interpretation: this measures reproducibility against the existing intake tags, not true category correctness.

## Manual audit
- Sample: 66 tickets
- Sampling: 6 per model-predicted category
- Manual review: customer message + agent note
- Correct: 59
- Error: 7
- Agreement: **89.4%**

### Error pattern
The largest issue is historical `Other`. Several examples are clearly cancellation or delivery cases even though the original tag remained `Other`. There were also isolated connectivity/billing boundary errors.

## Business validation
Billing:
- 2,425 tickets
- 20.8% of the stated window
- 477 first-response breaches
- 19.7% breach rate
- 477 × Rs 350 = **Rs 166,950** SLA credits

Target:
- 10% Billing breach rate
- Approx. 235 fewer breaches over the observed window
- 235 × Rs 350 = **Rs 82,250** potential SLA-credit reduction
