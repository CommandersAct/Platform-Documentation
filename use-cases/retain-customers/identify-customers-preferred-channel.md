# Identify customers’ preferred channel

## Use case description

🎯  Goal:

Detect when customers are not reacting anymore to your communication and change to the most preferred channel.

In order to personalize the communication with customers, identify preferred channel. For example, if customers didn’t react to any of your email, try to send an SMS or push notification instead.

🔧  Complexity: 2/5

💰  ROI: Low

## Use case setup

Step 1: create new Augmented User Attributes to add new metrics related to customers activities: number of orders in the last 2 months, number of visits, email opened, clicks…

Step 2: create a segment to target customers without email opened in the last 2 months for example

Step 3: create a stream to send users in segment previously created to an SMS or push notification solution
