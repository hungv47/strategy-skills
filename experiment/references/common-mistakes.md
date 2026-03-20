# Common Experiment Mistakes

A phase-by-phase guide to mistakes that invalidate experiments, waste cycles, or lead to wrong conclusions. Each mistake includes what goes wrong, how to detect it, and what to do instead.

---

## Pre-Launch Mistakes

### 1. Testing Too Low on the Impact Hierarchy

**What it is:** Teams spend weeks A/B testing button colors or CTA copy when the headline, angle, or offer hasn't been validated.

**Impact hierarchy (highest to lowest):**
1. Concept / angle / offer
2. Hook / headline
3. Visual style / layout
4. Body copy
5. CTA text, button color, font size

**Detection:** Your test variants differ only at level 4 or 5. You haven't validated levels 1-3 yet.

**Fix:** Start at the top. A headline change can move conversion 50-200%. A button color change moves it 1-3%. Test the big swings first.

---

### 2. No Baseline Measurement

**What it is:** Launching a test without knowing the current value of the metric you're trying to improve.

**Detection:** The experiment doc says "improve conversions" but has no current conversion rate. Sample size calculation is blank or hand-waved.

**Why it kills you:** Without a baseline, you can't calculate required sample size, expected lift, or whether the result is meaningful. A "3% conversion rate" result means nothing if you don't know whether you started at 2% or 4%.

**Fix:** Measure the baseline for at least 7 days (ideally 14) before designing the test. Put the number in the experiment doc. If you can't get a baseline, you're not ready to experiment. You're ready to instrument.

---

### 3. Success Criteria Defined After Seeing Results (HARKing)

**What it is:** Hypothesizing After Results are Known. You run the test, see the data, then define what "success" means to match what happened.

**Detection:** Decision rules are blank when the test launches. The team discusses "what counts as a win" after seeing the numbers. Success criteria shift between the launch doc and the results doc.

**Why it kills you:** You can always find a metric that went up. Post-hoc success criteria turn experiments into confirmation exercises.

**Fix:** Write decision rules (Success / Iterate / Kill thresholds) before launching. Lock them. If you didn't pre-define it, it's an observation, not a conclusion.

---

### 4. Testing During Anomalous Periods

**What it is:** Running experiments during holidays, outages, product launches, press coverage, or any period where traffic patterns differ from normal.

**Detection:** Test period overlaps with Black Friday, a major product release, a viral social post, or a site incident. Traffic volume or composition during the test differs significantly from the baseline period.

**Why it kills you:** Results don't generalize. Your "winning" variant may only win during a traffic spike from a specific source that won't recur.

**Fix:** Check the calendar before launching. Avoid major holidays, planned launches, and seasonal peaks. If an external event hits mid-test, extend the test or discard the contaminated window.

---

### 5. Contaminated Audiences

**What it is:** Your test group is exposed to other changes happening simultaneously, such as a different experiment, a marketing campaign, a product update.

**Detection:** Multiple experiments running on overlapping audiences. Marketing launched a new campaign targeting the same segment during your test. A product change shipped to all users mid-test.

**Why it kills you:** You can't attribute results to your change. The "lift" might be from the other campaign, the product update, or the interaction between them.

**Fix:** Maintain an experiment calendar. Check for audience overlap before launching. If overlap is unavoidable, document it and interpret results with caution.

---

## During-Test Mistakes

### 6. Peeking and Early Stopping

**What it is:** Checking results daily and stopping the test as soon as you see statistical significance.

**The math problem:** At a 95% confidence level, each peek is an independent test. If you peek 20 times during a test, the probability of seeing at least one false positive is 1 - 0.95^20 = 64%. Daily peeking at 95% CI inflates your actual false positive rate to roughly 25-30%.

**Detection:** Someone says "It's already significant after 3 days!" The test was planned for 14 days but stopped on day 5. Results are checked and discussed at every standup.

**Fix:** Set a check date based on sample size calculation and don't look until then. If you must monitor (e.g., to catch bugs), use sequential testing methods (Bayesian, alpha-spending functions) that adjust for multiple looks. Or define a single interim check at 50% of sample size with a stricter significance threshold (e.g., p < 0.01).

---

### 7. Changing the Test Mid-Flight

**What it is:** Adding new variants, altering traffic split, modifying the variant, or changing the metric definition while the test is running.

**Detection:** A third variant was added on day 4. The traffic split changed from 50/50 to 70/30 because "we want to limit exposure." The variant copy was tweaked mid-test because someone spotted a typo (that wasn't actually a typo).

**Why it kills you:** The data before and after the change aren't comparable. You've effectively started a new experiment but are analyzing it as if it's one continuous test.

**Fix:** If you need to change anything material, stop the test, discard the data, and restart. Fixing a genuine bug (broken link, crashed page) is fine. Document when it happened and exclude the affected data.

---

### 8. Insufficient Test Duration

**What it is:** Running a test for too few days, missing day-of-week effects, payday cycles, or novelty decay.

**Detection:** Test ran Monday-Friday only (weekday bias). Test ran for 3 days on a product with a weekly usage cycle. Test declared a winner before novelty effect could normalize (typically 7-14 days).

**Why it kills you:** Weekday and weekend visitors often behave differently. B2B traffic patterns differ Monday vs. Friday. Novelty effects inflate early results that won't sustain.

**Fix:** Run tests for at least one full week (ideally two) to capture day-of-week variation. For subscription products, run through at least one billing cycle. If your sample size says 4 days is enough, still run 7. The extra days protect against temporal bias.

---

### 9. Sample Ratio Mismatch (SRM)

**What it is:** Your test was configured for 50/50 split, but the actual data shows 48/52 or worse. This indicates an implementation bug, not natural variation.

**Detection:** Run a chi-squared test on the traffic split. A 50/50 test with 10,000 visitors showing 4,800/5,200 has a p-value of ~0.0001. That's not random, something is broken. Common causes: redirect failures, bot filtering affecting one variant, caching issues, assignment logic bugs.

**Why it kills you:** SRM means the randomization is compromised. Your groups aren't comparable. Any result (positive, negative, or neutral) is unreliable.

**Fix:** Check sample ratios before analyzing results. If SRM is detected, stop the test, find and fix the implementation bug, and restart. Do not interpret results from a test with SRM.

---

### 10. External Event Contamination

**What it is:** An unplanned external event changes behavior during your test (competitor launch, press mention, algorithm change, market event).

**Detection:** A sudden shift in traffic volume, composition, or behavior mid-test that doesn't correlate with your change. One variant's performance changes abruptly on the same day as the external event.

**Fix:** Monitor for traffic anomalies throughout the test. If a significant external event occurs, either extend the test to dilute the anomaly, segment out the affected period, or restart.

---

## Post-Test Mistakes

### 11. Declaring Winners on Secondary Metrics

**What it is:** The primary metric didn't move, but a secondary metric improved, so you declare success on the secondary metric instead.

**Detection:** The results section leads with a secondary metric. The primary metric result is buried or described as "inconclusive." Phrases like "While the primary metric didn't reach significance, we saw a promising signal in..." appear in the writeup.

**Why it kills you:** If you measure 10 secondary metrics, one will likely show significance by chance (multiple comparisons problem). Switching to whichever metric "won" is a form of HARKing.

**Fix:** Pre-register one primary metric. Secondary metrics are observations for future hypotheses, not conclusions. If a secondary metric is genuinely interesting, design a new experiment with it as the primary metric.

---

### 12. Ignoring Segment-Level Differences

**What it is:** The overall result is neutral or slightly positive, but one segment gained +40% while another lost -30%. The effects cancelled out.

**Detection:** Overall results look flat but segment cuts (device, source, new vs. returning, geography) show divergent patterns.

**Why it kills you:** Rolling out to all users means you're hurting one segment to help another. The net effect hides a real problem.

**Fix:** Always check major segments: device type, traffic source, new vs. returning users, and any segments relevant to your business. If segments diverge sharply, consider a targeted rollout.

---

### 13. Not Checking for Novelty Effect

**What it is:** The variant "wins" in week 1 but performance regresses toward the control by week 2-3. The initial lift was curiosity, not lasting improvement.

**Detection:** Plot daily conversion by variant. If the variant shows a spike in the first few days that steadily declines toward the control, that's novelty effect.

**Fix:** Compare week 1 vs. week 2 performance for the variant. If there's a clear decay trend, extend the test or discount the early data. For UI changes, novelty is especially common. Users click on new things because they're new, not because they're better.

---

### 14. Survivorship Bias in Iteration

**What it is:** You only iterate on winners and ignore what failures teach. Killed experiments are archived without extracting learnings.

**Detection:** The experiment backlog is full of "next version of winner" tests. No one can articulate what the last three killed experiments revealed. Post-mortems are skipped for killed tests.

**Fix:** Every killed experiment should answer: "What did we learn about the customer?" Feed failures back to `solution-design`. The failure mechanism often reveals a better approach than incremental optimization of a winner.

---

### 15. Assuming Correlation Is Causation in Before-After Tests

**What it is:** You made a change, metrics improved, so you conclude the change caused the improvement. But other things changed too: seasonality, a marketing campaign, a competitor outage.

**Detection:** The test type is Before-After (no control group). Other changes happened during the same period. The improvement aligns suspiciously well with an external factor.

**Fix:** Before-After tests are inherently weaker on causality. Acknowledge this in the results. Check corroborating evidence: did non-affected metrics stay stable? Did the change reverse when you temporarily rolled back? Consider using a holdout group (10% of traffic sees the old version) for important Before-After tests.

---

### 16. Confusing Statistical Significance with Practical Significance

**What it is:** A result is statistically significant (p < 0.05) but the actual effect size is too small to matter. A 0.1 percentage point lift from 2.0% to 2.1% can be "significant" with enough traffic, but it's not worth shipping.

**Detection:** The p-value passes your threshold but the absolute lift is tiny. The team celebrates "significance" without asking "is this worth the engineering cost to maintain?"

**Fix:** Define a minimum practical effect size before the test starts. "We need at least a 10% relative lift (2.0% → 2.2%) to justify the complexity." If the result is significant but below the practical threshold, treat it as a null result. Report both statistical significance and practical significance in the results.

---

### 17. Not Documenting Learnings for Killed Experiments

**What it is:** The test failed, so the team moves on without recording why. Six months later, someone proposes the same test.

**Detection:** No Post-Mortem section in the experiment file. Killed experiments have "Results: Failed" and nothing else. The same hypothesis appears in the backlog repeatedly.

**Fix:** Fill in the Post-Mortem for every kill: what you tested, why it failed, what you learned, and what to try instead. This is required. See the experiment artifact template.

---

## Mistakes by Test Type

### A/B Test Mistakes

**Too many variants:** Each variant needs full sample size. Four variants means 4x the traffic and 4x the duration. With limited traffic, two variants (control + one challenger) is almost always the right choice.

**Not accounting for multiple comparisons:** Testing variant A, B, and C against control means three simultaneous comparisons. At 95% confidence, the probability of at least one false positive is 1 - 0.95^3 = 14%. Use Bonferroni correction (divide alpha by number of comparisons) or stick to fewer variants.

### Before-After Mistakes

**Attributing change to intervention when external factors shifted:** Seasonality, marketing campaigns, competitor actions, and organic trends all create noise. A Before-After test without a control group cannot separate your intervention from everything else.

**Seasonality confusion:** Comparing January to February ignores that February is naturally different. If possible, compare against the same period last year, or use a metric that's historically stable.

### Cohort Mistakes

**Selection bias:** Testing on your most engaged users, power users, or users who opted in. These users aren't representative. They'd probably succeed with any intervention.

**Generalization errors:** A pilot with 50 hand-picked enterprise clients tells you nothing about how the feature will work for 5,000 self-serve users.

### Pilot Mistakes

**Over-indexing on qualitative signal:** Three enthusiastic users in a pilot of 10 feels like validation but is statistically meaningless. Qualitative signal is useful for generating hypotheses, not for confirming them.

**Small-N conclusions:** Drawing firm conclusions from pilot groups of 10-30 users. At this scale, one or two outliers swing the result entirely.

---

## Decision Rule Mistakes

### 18. Moving Goalposts After Results

**What it is:** The pre-defined success threshold was 20% lift. You got 12% lift. Someone suggests "12% is still pretty good, let's call it a win."

**Fix:** If you pre-defined 20%, hold to it. 12% is an "Iterate" result, not success. If you think 12% is actually sufficient, that's a lesson for next time. Set the threshold lower upfront.

### 19. "One More Week" Fishing

**What it is:** Results are negative but not yet significant. The team extends the test hoping significance will appear. It rarely does. This is fishing for a result.

**Detection:** The test has been extended twice. Each extension is justified as "we're almost there." The trend isn't improving with more data.

**Fix:** If you've reached your pre-calculated sample size and the result is negative, that IS your result. An underpowered negative result after full sample is a genuine negative. Stop extending.

### 20. Killing Tests Before Reaching Sample Size

**What it is:** Results look bad on day 3, so you kill the test. But you haven't collected enough data to distinguish a real effect from noise.

**Fix:** Unless a guardrail metric is severely breached (crash rate spikes, revenue drops sharply), let the test run to the pre-calculated sample size. Define kill criteria upfront: specific guardrail thresholds that trigger early termination.

### 21. No Kill Criteria Defined Upfront

**What it is:** There's no pre-defined line for when a test should be stopped early due to harm.

**Fix:** Before launching, define guardrail thresholds for early termination. Example: "Kill immediately if error rate exceeds 5% or support ticket rate doubles." Without kill criteria, harmful tests run too long; with vague criteria, good tests get killed too early.

### 22. Ignoring Guardrail Breaches

**What it is:** The primary metric looks great, so you ignore that support tickets doubled or error rates spiked.

**Detection:** Guardrail metrics are defined but not checked in the results. Or they're checked, the breach is noted, and the team decides to ship anyway because the primary looks good.

**Fix:** Guardrail breaches are not optional. Follow the guardrail response protocol: slight breach → reduce scope and retest; severe breach → iterate on implementation; inherent breach → kill.

---

## Quick-Reference Table

| Mistake | Detection Signal | Fix |
|---------|-----------------|-----|
| Testing too low on impact hierarchy | Variants differ only in CTA/button details | Test concept or headline first |
| No baseline measurement | Sample size calculation is blank | Measure baseline for 7-14 days first |
| HARKing (post-hoc success criteria) | Decision rules written after test ends | Lock Success/Iterate/Kill thresholds before launch |
| Testing during anomalous periods | Test overlaps holidays, launches, outages | Check calendar; avoid atypical windows |
| Contaminated audiences | Multiple tests on same audience | Maintain experiment calendar; check overlap |
| Peeking and early stopping | "It's significant after 3 days!" | Set one check date; use sequential methods if monitoring |
| Changing test mid-flight | Variants or splits modified during test | Stop, discard data, restart |
| Insufficient duration | Test ran < 7 days or weekdays only | Run at least one full week minimum |
| Sample ratio mismatch | Expected 50/50, got 48/52 or worse | Stop test, fix implementation bug, restart |
| External event contamination | Sudden behavior shift mid-test | Extend test, segment out affected period, or restart |
| Declaring winners on secondary metrics | Primary failed, secondary highlighted | Pre-register one primary metric; secondaries are hypotheses |
| Ignoring segment differences | Overall flat but segments diverge | Check device, source, new/returning segments |
| Not checking novelty effect | Week 1 spike, week 2 decline | Compare week 1 vs. week 2; extend if decaying |
| Survivorship bias in iteration | Only iterating on winners | Document and learn from every killed experiment |
| Correlation as causation (Before-After) | No control group; other changes co-occurred | Acknowledge weakness; use holdout group for important tests |
| Statistical ≠ practical significance | p < 0.05 but lift is 0.1% absolute | Define minimum practical effect size before test |
| Not documenting killed experiments | No Post-Mortem section filled in | Complete Post-Mortem for every kill decision |
| Moving goalposts | Success threshold changed after results | Hold to pre-defined thresholds |
| "One more week" fishing | Test extended multiple times when negative | Accept the result at pre-calculated sample size |
| Killing too early | Test stopped before reaching sample size | Run to sample size unless guardrail breached |
| No kill criteria upfront | No guardrail thresholds for early termination | Define specific early-stop thresholds before launch |
| Ignoring guardrail breaches | Guardrails breached but test shipped anyway | Follow guardrail response protocol, no exceptions |
