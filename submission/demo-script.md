# Three-minute screen-recording script

0:00–0:25 — Show the README and the run command.
Say: “The tool starts from the README and takes the supplied CSVs. I restricted the analysis to Jan 2025 through Jun 2026 because that is the brief's stated window.”

0:25–1:05 — Show the input data and model code.
Say: “The historical category is an intake-bot tag, so I kept it as the baseline but did not call it ground truth. The model combines the opening customer message and closing agent note, then uses TF-IDF plus a linear SVM to produce a second category.”

1:05–1:40 — Show the monthly category chart and monthly team chart.
Say: “Billing is 2,425 tickets, 20.8% of the window. Logistics is 1,905, 16.4%. The charts are generated from the same run.”

1:40–2:15 — Show validation outputs.
Say: “Five-fold validation against historical tags is 83.8%. That number is not the final correctness claim because the tags are noisy. I manually reviewed 66 stratified predictions: 59 agreed, or 89.4%. Most failures were ‘Other’ tickets that actually described cancellations or delivery problems.”

2:15–2:45 — Show the memo.
Say: “I pushed back on the automatic two-hire conclusion. Billing is the largest team and has a 19.7% first-response breach rate, but two hires cost about Rs 9 lakh a year. I would first target a reduction to 10%, worth about Rs 82,250 over the 18-month observed period in SLA credits.”

2:45–3:00 — Show limitations.
Say: “I deliberately did not build a workforce-capacity model because the source contains negative handle times and legacy transfer gaps. I would rather leave that out than produce a precise-looking but unreliable staffing number.”
