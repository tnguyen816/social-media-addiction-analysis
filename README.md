# Social Media Addiction Analysis

An end-to-end data analysis project exploring how social media usage habits relate to mental health among 1 million users aged 13 to 27. The analysis was done in **MySQL** and visualized in an interactive **Tableau Public** dashboard.

🔗 **Live dashboard:** https://public.tableau.com/views/SocialMediaAddiction_17905464244050/Dashboard1?:language=en-US&:sid=&:redirect=auth&:display_count=n&:origin=viz_share_link
📁 **Dataset:** (https://www.kaggle.com/datasets/sharmajicoder/gen-z-social-media-usage-dataset/data)


## Overview

The goal of this project is to understand who uses social media, how they use it, and whether heavier use is associated with lower well-being. The dashboard covers usage by country and platform, demographics, purpose of use, and mental health outcomes by addiction level.

## Dataset

- **Size:** 1,000,000 user records
- **Countries:** 7 (Australia, Brazil, Canada, Germany, India, UK, US)
- **Age range:** 13 to 27
- **Primary platforms:** Instagram, Snapchat, TikTok, Twitter (X), YouTube

| Column | Description |
|---|---|
| `age` | Age of the user (13 to 27) |
| `gender` | Male, Female, Other |
| `country` | Country of residence |
| `daily_usage_hours` | Average daily time on social media (hours) |
| `primary_platform` | Most frequently used platform |
| `num_platforms_used` | Number of platforms actively used |
| `purpose` | Primary reason for use (Entertainment, Education, Socializing, News, Content Creation) |
| `avg_session_minutes` | Average duration of a single session |
| `night_usage` | Whether the user is active during late-night hours (Yes/No) |
| `mental_health_score` | Proxy score (1 to 10) indicating mental well-being |
| `addiction_level` | Usage intensity category (Low, Medium, High) |
| `screen_time_before_sleep` | Minutes spent on social media before sleep |

## Tools

- **MySQL Workbench:** data import, cleaning, and aggregation
- **Tableau Public:** interactive dashboard
- **GitHub:** version control and project documentation

## Approach

1. **Loaded** the 1M-row CSV into MySQL.
2. **Explored and aggregated** the data with SQL (`GROUP BY`, `AVG`, `COUNT`, `CASE WHEN` for bucketing and relabeling), so the heavy lifting happened in the database rather than in the visualization tool.
3. **Exported summarized results** as small CSVs. Tableau Public cannot connect live to MySQL, and pre-aggregating keeps the published workbook fast.
4. **Built the dashboard** in Tableau Public from those summaries.

## Key Findings

**1. Addiction level is the clearest driver of mental health outcomes.**
Average mental health score falls from **8.611 (Low)** to **7.042 (Medium)** to **5.371 (High)**, a gap of about **3.2 points** on a 10-point scale.

**2. Demographics show almost no difference.**
Across genders and countries there is no meaningful difference in number of platforms used, daily usage, screen time before sleep, or purpose of use. Mental health score is also flat across ages 13 to 27, at roughly 7.2.

**3. Usage habits are highly consistent.**
On average, users spend about **3.5 hours a day** on social media, with sessions of about **25 minutes**.

**4. Instagram, YouTube, and TikTok lead.**
These are the three most used primary platforms. Medium is the most common addiction level on every platform, followed by Low and then High.

**5. Entertainment is the top purpose.**
Roughly 40% of users say they use social media mainly for entertainment. Content Creation and News are the least common purposes.

**6. Night usage makes no visible difference.**
Users active late at night have essentially the same mental health scores as those who are not, within each addiction level.

Because most users fall into the Medium addiction group, the overall average mental health score (**7.17**) sits close to the Medium score (7.042).

## Limitations

- **Correlation, not causation.** The data cannot show whether heavy use lowers well-being or whether lower well-being leads to heavier use.
- **Proxy metric.** The mental health score is a proxy on a 1 to 10 scale, not a clinical measure.
- **Possibly synthetic data.** The near-identical averages across gender, country, age, and night usage suggest the dataset may be simulated, so real-world patterns could differ.
- **Small differences on the map.** Country shading exaggerates very small differences in average usage; check the actual values before drawing conclusions.

```

> The raw 1M-row dataset is not included in this repo because of its size. Download it from the Kaggle link above.

## Possible Next Steps

- Check whether the link between usage hours and mental health holds after controlling for addiction level.
- Compare countries on mental health score, not just usage.
- Explore whether session length matters more than total daily time.

## Disclaimer

This project is for portfolio purposes only and is not intended to inform clinical or medical conclusions.
