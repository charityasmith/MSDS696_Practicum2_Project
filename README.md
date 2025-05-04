
# The Three-Point Revolution: Is It Changing Basketball for Better or Worse?

## Overview

This project explores the rise of the three-point shot in the NBA and its implications for competitiveness, team success, and fan sentiment. By analyzing four decades of NBA game data alongside Reddit discussions, I set out to answer the central question: Has the three-point revolution made basketball better or worse?

 With recent headlines claiming that teams are shooting too many threes and quotes from legends like Michael Jordan criticizing the change, it felt timely to dig into the numbers and see what they really say.

---

## Data Sources

- NBA Statistics (1980–2024) from [Basketball Reference](https://www.basketball-reference.com/) and [NBA.com/stats](https://www.nba.com/stats)
  - Includes team-level data: win percentage, shooting efficiency, offensive metrics, etc.
- Reddit Sentiment (r/nba) using scraped posts related to three-point shooting from 2010–2024.
  - Cleaned and processed with Vader sentiment analysis.

---

## Key Questions

- How has the volume and accuracy of three-point shooting changed over time?
- Do teams that shoot more or shoot better from three win more?
- Can we group teams by their three-point shooting style and see clear patterns in success?
- What do fans think about the league’s shift to three-point-heavy play?

---

## Visual Trends & Commentary

Growth in Three-Pointers Attempted Over Time

![Total 3PA by Year](visualizations/total_3pa_by_year_2.png)

Three-pointers attempted per game has exploded — especially after 2015. Teams now average over 35 threes per game, compared to under 10 in the 1980s.

---

Three-Point Accuracy

![3P% Over Time](visualizations/3pt_percentage_overtime.png)

- Accuracy (three-point percentage) improved significantly from the 1980s to the early 2010s.
- Gains stabilized around 2015, suggesting that further volume growth isn’t necessarily tied to increased accuracy.

---

All-Time Three-Point Leaders

![Top 10 All-Time 3P Leaders](visualizations/top_10_3p_leaders.png)

Stephen Curry stands alone — redefining what’s possible from the arc. Most of the top 10 are modern players, a clear reflection of the league's evolving playstyle.

---

Team-Level Trends

![Team 3PA Over Time](visualizations/nba_team_3pa_over_time.png)

Every team is attempting more threes. The interactive version of this EDA lets users select individual teams to explore style differences across franchises and eras.

---

## Statistical Analysis

Regression: Does Three-Point Shooting Predict Wins?

Regression models by era show a shift:

- Early Era (2000–2010): Three-pointers attempted had a weak or negative relationship with win percentage.
- Modern Era (2017–2024): Three-point percentage became a statistically significant predictor. For instance:
  - 3P% coefficient = 6.89, p = 0.006
  - Model R² = 0.524

Conclusion: Shooting efficiently from deep matters more than simply increasing volume.

---

Clustering: Team Shooting Styles

![Clustered Teams](visualizations/team_clusters_labeled.png)

Using K-Means and PCA, I grouped teams into three styles:

- Efficient shooters with high win %
- High volume but moderate win %
- Low usage, low success

Exemplar teams:  
- Efficient: 2022 Cavaliers  
- Volume-heavy: 2002 Pistons  
- Low usage: 2007 Knicks

---

Which Style Wins?

![Win% by Cluster](visualizations/win_pct_boxplot_by_cluster.png)

Statistical testing (Tukey HSD):
- F-statistic = 183.4, p < 0.0001
- All pairwise differences between clusters were statistically significant
  - Efficient > Volume (Δ = 0.08, p < 0.001)
  - Efficient > Low Usage (Δ = 0.208, p < 0.001)

Efficiency beats volume every time.

---

## Fan Sentiment Analysis

![Reddit Word Cloud](visualizations/word_clouds.png)

Sentiment trend line showed no statistically significant trend over time (p = 0.35). Despite concerns, fan tone remains generally stable — and often positive after 2015.

---

## Machine Learning: Predicting Team Style

Random Forest classifier trained on shooting metrics achieved:
- Accuracy: ~85%
- Top predictors: three-pointers attempted rate, effective FG%, and assist %

Confusion matrix confirmed strong performance in classifying team style based on input metrics.

---



### Analytical Highlights

A regression analysis was run across three distinct NBA eras: early (2000–2010), middle (2011–2016), and modern (2017–2024). In the early years, 3-point shooting percentage was not significantly correlated with win percentage (p = 0.312). By the modern era, however, the relationship became statistically significant (p = 0.006), suggesting a shift in strategic value.

In addition, a Tukey HSD test confirmed that teams classified in the “efficient 3-point shooting” cluster significantly outperformed other styles in terms of win percentage (p < 0.001 for all comparisons). This supports the broader conclusion that shooting accuracy, not just volume, is what drives competitive success in today’s NBA.

Machine learning also reinforced this trend. A Random Forest classifier used team-level features to predict playstyle with strong accuracy. 3-point attempt rate was the top predictor of cluster category, followed by effective field goal percentage and 3-point shooting percentage.

Sentiment analysis on Reddit showed stable or slightly positive fan sentiment over time. This finding indicates that the rise in 3-pointers hasn’t alienated fans — despite increasing chatter and debate, the overall tone hasn’t soured.


## Conclusion

The three-point revolution has made the NBA faster, more dynamic, and skill-driven — but only when used wisely.

- Teams win more when they shoot better, not just more.
- Franchises differ in how quickly (or whether) they adapt to the trend.
- Fans are engaged, not alienated — even as three-point volume rises.

---

## What’s Next?

- Cluster individual players, not just teams
- Compare playoff vs regular season strategies
- Integrate video tracking and shot quality models
- Expand sentiment analysis to forums, interviews, and attendance
- Explore the link between blowouts and three-point strategy

---

## References

- Basketball Reference. (n.d.). *Basketball statistics and history*. Retrieved from https://www.basketball-reference.com/
- NBA.com. (n.d.). *NBA stats*. Retrieved from https://www.nba.com/stats
- Leff, J. (2024, October 30). *NBA teams are taking too many 3s and it’s becoming a problem*. USA Today For The Win.
- Kota, D. (n.d.). *Michael Jordan tried to warn the NBA about shooting too many 3-pointers*. Sports Illustrated FanNation.
