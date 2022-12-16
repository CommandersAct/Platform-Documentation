# Identify a churn risk with RFM segmentation

## Use case description

🎯  Goal:

Detect customers with a churn risk and activate them.

Use RFM segmentation to build a churn risk audience segment and send a dedicated campaign (‘miss you’ campaign, survey…)

🔧  Complexity: 2/5

💰  ROI: Low

## Use case setup

Step 1: create a segment with conditions representing a churn risk (use Augmented User Attributes feature to create score/ratio/flag/Boolean representing a churn, like for example number of orders in the last 6 months, number of visits, clicks…)

Step 2: create a stream to send users in segment previously created to an emailing solution
