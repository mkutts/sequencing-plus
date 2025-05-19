# Research Proposal: Sequencing+ – A Contextual Pitch Sequencing Metric

## 1. Project Title
**Sequencing+: Quantifying Pitch Sequencing Effectiveness Beyond Traditional Stuff-Based Models**

## 2. Executive Summary
Current pitch quality metrics such as Stuff+ focus on evaluating individual pitch characteristics like velocity, movement, and release, often relative to a pitcher's fastball. However, these models overlook the strategic sequencing of pitches and how pitch-to-pitch interactions can enhance effectiveness.

This research proposes a new metric, **Sequencing+**, designed to quantify the *effectiveness of pitch sequences*, regardless of which pitch type anchors the arsenal. Sequencing+ aims to evaluate how the outcome of a pitch is affected by the pitch that preceded it—offering insight into sequencing tactics such as “setting up a fastball with a changeup” or “using a slider to change eye level before a high fastball.”

## 3. Research Goals
- Develop a new pitcher-level metric that captures the value of sequencing.
- Account for unconventional sequencing patterns (e.g., changeup-first, cutter-slider setups).
- Identify which pitch pairs produce better-than-expected outcomes.
- Provide a complementary tool to Stuff+, Pitching+ and run value metrics.

## 4. Hypothesis
> Pitchers who use intentional sequencing strategies—especially those who deviate from fastball-centric arsenals—create run value advantages that are not reflected in Stuff+ or velocity-based models. These advantages can be measured using pitch pair outcomes compared to league norms.

## 5. Metric Design: Sequencing+

### a. Core Idea
Measure the change in performance of Pitch B when it is preceded by Pitch A, compared to:
- League-average performance for that sequence.
- Pitcher’s own performance with Pitch B independent of sequencing.

### b. Formula Sketch
```
Sequencing+(A → B) = 
100 * [Pitcher's outcome metric for (A → B)] / [League average for (A → B)]
```

Outcome metrics can include:
- Whiff%
- xwOBA
- Called Strike + Whiff Rate (CSW%)
- Run value per pitch

The final Sequencing+ score can be:
- Aggregated by pitcher
- Split by pitch pair type
- Normalized to a 100-point scale (like wRC+, Stuff+)

## 6. Data Requirements
- Statcast pitch-level data (via Baseball Savant or `pybaseball`)
- Key columns: `pitch_type`, `description`, `events`, `release_speed`, `xwOBA`, `batter_hand`, `pitch_number`, `at_bat_number`
- Groupings: Pitcher, Game, At-Bat, Pitch Sequence

## 7. Methodology
1. **Data Collection** – Pull Statcast pitch-by-pitch data for MLB pitchers from 2020–2024.
2. **Data Engineering** – Create sequential pitch pairs (e.g., Pitch N−1 → Pitch N) and calculate outcome metrics.
3. **Baseline Modeling** – Calculate league-average metrics for all pitch-pair combinations.
4. **Metric Calculation** – Compare individual pitcher pitch-pair performance to league baseline.
5. **Scoring System** – Normalize to a 100-scale, highlight Sequencing+ > 100 as “above average.”

## 8. Case Studies
- **Kyle Hendricks** – Changeup → Fastball setups
- **Devin Williams** – Off-speed-dominant sequencing
- **Lance Lynn** – Cutter-heavy sequences
- **Spencer Strider** – Fastball-slider dominance

These will be used to validate whether Sequencing+ captures sequencing value missed by Stuff+.

## 9. Deliverables
- A fully documented metric definition
- Jupyter notebook or Python script to compute Sequencing+ from raw data
- Data visualizations (e.g., pitch pair performance heatmaps)
- A short white paper or blog-ready research summary
- Optionally: A dashboard or web app for querying Sequencing+ by pitcher

## 10. Timeline & Milestones

| Phase                         | Milestone Description                                   | Timeline           |
|-------------------------------|----------------------------------------------------------|--------------------|
| **Phase 1: Setup**            | Define pipeline architecture and collect Statcast data   | Week 1             |
| **Phase 2: Engineering**      | Construct pitch sequences, engineer lag features         | Week 2–3           |
| **Phase 3: Modeling**         | Calculate baseline metrics and Sequencing+ scores        | Week 4–5           |
| **Phase 4: Case Studies**     | Apply metric to selected pitchers and analyze results    | Week 6             |
| **Phase 5: Validation**       | Correlate Sequencing+ with run value, ERA-, FIP- etc.    | Week 7             |
| **Phase 6: Deliverables**     | Write paper, build dashboard (optional), finalize visuals| Week 8–9           |
| **Phase 7: Submission**       | Publish paper or pitch to MLB teams, analysts, or media  | Week 10+           |

## 11. Comparative Context

| Metric          | Focus Area                              | Limitation in Context of Sequencing             |
|-----------------|------------------------------------------|-------------------------------------------------|
| **Stuff+**      | Raw pitch characteristics vs MLB avg     | Anchored to fastball, ignores sequence context  |
| **Pitching+**   | Combines Stuff+ with location and context| Still largely pitch-isolated                    |
| **Run Value**   | Run prevention on per-pitch basis        | Captures value, not pitch interaction mechanics |
| **Tunneling Index** | Similarity of pitch trajectories       | Ignores pitch order and intent                  |
| **CSW%**        | Strike-generating ability                | Doesn’t consider what pitch came before         |

**Sequencing+** differs by explicitly capturing how the *order* of pitches contributes to outcome effectiveness — offering a novel way to evaluate deception, setup quality, and pitch strategy.

## 12. Future Work
- Extend to minor leagues, college, or spring training
- Incorporate tunneling and deception metrics
- Use machine learning to identify sequencing clusters or optimal patterns
