# Migrate from Fuse v1 to Fuse v2

## What are the differences between V1 and V2?

On **Fuse V1,** the goal was to **identify** same users and **duplicate** for each visitor (cookie based) all the user data you could have on this person.\
For example, you collected data about a visitor A with a laptop and a visitor B with a mobile phone. If the Fuse algorithm noticed that visitor A = visitor B, it duplicates the information from visitor B to visitor A and vice-versa. So you can have an overview of visitors who shared the same information and are linked.

![](<../../.gitbook/assets/image (11).png>)

With **Fuse V2,** it goes further by **merging** these visitors in order to have a **unique user** with all the data collected. With Fuse V2, the goal is to detect with multiple reconciliation keys the same customer and unify all the data around 1 unique user in order to have a complete view of the customer across all devices and all channels.

![](<../../.gitbook/assets/image (12) (2) (1).png>)

With Fuse V2 your CDP become **user-centric** rather than cookie centric and that change the way you define your marketing campaigns: you don’t talk to devices anymore but to persons directly, to users.

##
