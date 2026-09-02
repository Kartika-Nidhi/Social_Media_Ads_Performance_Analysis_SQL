# INTRODUCTION

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">

Digital marketing strategies rely heavily on granular tracking to optimize advertising spend, target precise demographics, and drive conversions across platforms like Meta (Facebook and Instagram). This project analyzes a relational database of a synthetic social media advertising campaign containing detailed logs for users, campaigns, targeting parameters, and transactional ad events (impressions, clicks, and purchases). Using SQL, this analysis evaluates end-to-end campaign performance, uncovers key demographic patterns, and identifies conversion bottlenecks across the user journey.



# OBJECTIVES:

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">

<ul>
<li>Conversion Funnel Efficiency: Track user progression from impression to click and final purchase to calculate Click-Through Rates (CTR), Conversion Rates (CR), and identify key drop-off stages.

<li>Demographic & Behavioral Segmentation: Analyze user engagement patterns across age groups, genders, and geographic locations to evaluate ad targeting effectiveness.

<li>Campaign & Strategic ROI Performance: Measure key financial and performance metrics (cost per click, return on ad spend, and overall yield) across different campaign structures and duration windows.

<li>Ad Asset & Targeting Analysis: Evaluate individual creative assets against their defined target parameters to pinpoint high-performing audience-ad combinations.
</ul>

## Database Schema

<div>

## Dashboard

<div>

# 1. Getting Ready With Data

<div>

# 2. Individual Table Inspection

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Normalized users table into First Normal Form, such that interest field now contains atomic value, instead of comma separated values. 

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">No duplicate campaings.

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Normalized ads table into First Normal Form, so that target_interest contains atomic values.

<div>

<div>

# 3. High-Level Performance and ROI Analysis

## 3.1 Which campaigns achieve the lowest Cost-Per-Acquisition (CPA) and highest estimated ROAS (Return On Ads Spend)?


<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Campaing_42_Summer has lowest CPA and highest ROAS.<br>
Note: Since, the dataset doesn't mention purchase amount, purchase count has been multiplie by 50$ to estimate ROAS.

<div>

## 3.2 What is the step-by-step conversion funnel drop-off rate from Impression to Click to Purchase across all campaigns?


<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Massive Initial Drop-Off: Out of 339,812 ad impressions, only 11.79% convert into clicks (CTR), resulting in an 88.21% loss of audience.
<br>From the 40,079 users who clicked the ad, only 5.07% completed a purchase (CR), reflecting a high 94.93% drop-off on the landing page or checkout workflow.
<br>Overall conversion efficiency stands at 0.60% (2,031 purchases from 339,812 impressions). The largest total loss of users occurs between viewing the ad and clicking, while the steepest relative drop-off occurs between clicking and completing a purchase.

<div>

## 3.3 Does campaign duration (duration_days) correlate with budget utilization rate and overall conversion volume?


<div>

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">All the campaings in the dataset have duration of more than a month, with average daily spending of $802.22, and average purchase per campaing of $61.12.

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Report To: Chief Marketing Officer (CMO), VP of Marketing, Executive Leadership

<div>

# 4. Tactical Ad Operations & Platform Optimization

## 4.1 Which combinations of ad_platform and ad_type generate the highest Click-Through Rate (CTR) and conversion rates?



<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Image ads on Instagram has highest click through rate, while stories ads on Facebook has highest click to purchase rate.

<div>

## 4.2 Are target demographic parameters (target_gender, target_age_group) in the ads table effectively capturing matching user profiles in users?


Description: Joins ads, ad_events, and users. Compares ads.target_gender against users.user_gender, and ads.target_age_group against users.age_group for users who triggered 'Purchase' events to evaluate targeting alignment vs. off-target conversions.

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Ads targeted at Female users drive 2,495 purchases, whereas actual buyers are predominantly Male (3,435 purchases vs. 2,134 female buyers). This indicates ad spend is heavily directed toward female audiences while male audiences deliver higher actual conversion volume.
<br>
Actual purchases peak in the 25-34 age demographic (2,507 purchases), followed by 18-24 (2,007 purchases). However, ad targeting allocates significant budget to 35-44 (1,684 purchases) and All (1,509 purchases), resulting in a slight targeting misalignment relative to peak conversion age brackets.

<div>

## 4.3 Which specific ad creative assets (ad_id) are underperforming (high impressions, zero to low purchases) and driving up overall cost?




<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Based on digital advertising industry standard, conv_per <0.20% - <0.30% is considered very ineffective. For this dataset, out of 200 ads, three ads are ineffective, indicating mismatched target or poor creativity leading to budget burn.

<div>

<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Report To: Paid Media Specialists, Campaign Managers, Media Buyers

<div>

# 5. Behavioral Analytics & Demographic Segmentation

## 5.1 How do conversion rates vary across different user age_group categories, user_gender, and geographic country locations?



<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">India (55-65, Other) leads top-of-funnel engagement with a 20.00% CTR.
<br>France (45-54, Other) leads bottom-of-funnel purchases with a 33.33% click-to-purchase conversion rate.
<br> India (55-65, Other) is the only demographic segment that ranks in the top 5 for both click-through rate (20.00%) and purchase conversion rate (16.67%).

<div>

## 5.2 What specific days of the week (day_of_week) and times of day (time_of_day) record the highest purchase frequency?




<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Friday (Afternoon) leads with 1,508 clicks, followed by Tuesday (Evening) at 1,495 clicks.
<br>
Thursday (Morning) generates the highest number of purchases (87), despite not being in the top 5 for total click volume.
<br>
Friday (Afternoon) and Friday (Night) appear in the top 5 for both click engagement and total purchases.

<div>

## 5.3 Which user interest categories (users.interests) demonstrate the highest engagement propensity relative to the ad targeting parameters (ads.target_interests)?




<div style = "background-color:lightblue; color:green; font-size:20px; text-align:justify">Top Performing Pair: art-->finance leads all cross-interest categories with 57 purchases.
<br>
High-Converting Target Domain: finance is the most frequent high-converting target interest overall, appearing at ranks 1 (art --> finance, 57), 2 (travel --> finance, 53), and 4 (finance --> finance, 52).
<br>Cross-Category Alignment: technology --> fashion and art --> health both show strong conversion volume with 52 purchases each.

<div>

# 6. Recommendations and Suggestions