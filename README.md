# wyda-learner-churn-mvp
> Minimal-viable pipeline to **predict which Wyda learners will fall behind within 7 days** and surface actionable insights.


## Overview

1. **Data**  
   * Four Wyda CSV exports (`Users`, `ScenariosAttempts`, `ScenariosResponses`, `ReflectionsResponses`).  
   * 47 learners, 1 100+ scenario attempts.

2. **Feature engineering highlights**  
   * Core metrics (`n_attempts`, `mean_gap_hours`, …).  
   * “Struggle” flag: scenarios retried > 1 × with **no pass**.  
   * 12 behavioural features (pass-rate, streak length, well-being, etc.).  
   * Label **`fall_behind`** = inactive ≥ 7 days **and** not yet module-complete.

3. **Models**  
   * Logistic-regression baseline (F1 ≈ 0.91 on 25 % hold-out).  
   * Gradient-Boosting trees (perfect on tiny hold-out; cross-val F1 ≈ 1.0 → flagged for possible over-fit).  
   * Feature importance points to **engagement volume and score variance** as top drivers.
