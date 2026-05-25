# Music Recommendation Project — Report

---

## Q1: What insights did you gain from your EDA? Were any columns highly correlated?

Most lyrical feature scores are heavily skewed toward 0, meaning the average song scores low on things like violence or gospel. Genre made a big difference — rock songs scored higher on violence and older pop songs scored higher on family/spiritual themes. I also noticed that romantic and dating scores moved together, which makes sense.

When I checked the correlation matrix, no two columns were above 0.85, so nothing needed to be dropped based on correlation.

---

## Q2: How did you determine which columns to drop or keep?

I dropped columns that weren't useful for numeric clustering:

- `Unnamed: 0` — just a row index
- `lyrics` — raw text, not a numeric feature
- `artist_name`, `track_name`, `release_date`, `genre`, `topic` — identifiers, not features

I also removed the top 1% of songs by word count since a handful of songs had unusually high counts that could skew the clusters. The correlation check confirmed no other columns needed to go.

---

## Q3: What was the optimal number of clusters?

I tested k from 2 to 12 using two methods:

1. **Elbow Method** — plotted inertia for each k. The curve was gradual with no sharp elbow.
2. **Silhouette Score** — picked the k with the highest score.

The silhouette score peaked at **k = 12**, so that's what I used for the final model. The scores were low overall (under 0.2), which is normal for high-dimensional data like this.

---

## Q4: Describe the clusters in human terms.

I looked at the average feature scores for each cluster to label them:

- **Cluster 0** — Sad, emotional songs with low violence
- **Cluster 1** — Lifestyle songs about money and status, low sadness
- **Cluster 2** — Night-life and time-themed songs
- **Cluster 3** — Romantic love songs, very low violence
- **Cluster 4** — Songs about travel and movement
- **Cluster 5** — Big-picture songs about the world and life
- **Cluster 6** — Spiritual and family-oriented songs
- **Cluster 7** — Very feelings-heavy and emotional songs
- **Cluster 8** — Aggressive, high-violence songs
- **Cluster 9** — Gospel songs
- **Cluster 10** — Provocative, hype-style songs
- **Cluster 11** — Songs that are literally about music

---

## Q5: Which songs would you recommend to this user?

The 10 test songs landed in 6 different clusters. Most fell into Cluster 8 (Aggressive, 3 songs), Cluster 0 (Sad/Emotional, 2 songs), and Cluster 2 (Night-Life, 2 songs). The user clearly likes intense, edgy music.

The model recommended 3 songs per cluster the user appeared in:

- **Cluster 8 (Aggressive):** a thousand faces — Creed, jericho — Sister Rosetta Tharpe, i've got you under my skin — Mel Tormé
- **Cluster 0 (Sad/Emotional):** photograph — Ringo Starr, all my life — Nate Millyunz, same old memories — Ray Price
- **Cluster 2 (Night-Life):** unchained melody — George Benson, aloysius — Cocteau Twins, wimoweh — The Kingston Trio
- **Cluster 10 (Provocative):** heatstrokes — Krokus, working for the weekend — Loverboy, the experimenter — Thee Oh Sees
- **Cluster 3 (Romantic):** pledging my love — Emmylou Harris, ever be — Aaron Shust, forever yours — Marty Robbins
- **Cluster 1 (Lifestyle):** mvp — Big L, liaison — Nite Flyte, evangelion — Vendetta Beats

These recommendations match the user's taste well. For example, Creed and Krokus fit the same aggressive energy as Godsmack and Rage Against the Machine.
