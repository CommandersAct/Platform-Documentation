# Compliance score formula

## Cookie Compliance Score: How Does It Work?

Your compliance score, out of 100, estimates the compliance level of cookie deposits observed during scans, based on GDPR and ePrivacy rules.\
Please note that it does not, by itself, cover all the criteria reviewed by data protection authorities, particularly certain aspects of the consent interface.

It starts at **100**, representing perfect compliance, and decreases according to the violations detected, taking into account their **actual impact**, based on their frequency of occurrence, their **severity**, based on when they are deposited, and their **category**, based on the cookie’s purpose.

#### Calculation rule: points lost

**Score = 100 − total points lost**\
The score never falls below 0.

For each problematic cookie, the following calculation is applied:

**Points lost = frequency in % × category weight × base rate**

* **Frequency**: percentage of the site’s pages on which the cookie is deposited, for example, 100% means all pages and 5% means very rare.
* **Base rate**:
  * Cookies deposited **before consent**, without prior validation: **0.10** points per percentage point of presence.
  * Cookies deposited **after a “refuse all” action**: **0.15** points per percentage point of presence, as this is more serious because it disregards an explicit refusal.
* **Category weight**, a multiplier based on the cookie’s purpose:
  * **Marketing / Advertising / Targeting / Remarketing**: ×2, as these cookies are subject to the most severe enforcement actions by data protection authorities.
  * **Analytics / Audience measurement**: ×1, as an exemption may be possible when processing is anonymised and limited, resulting in medium severity.
  * **Uncategorized**, meaning a cookie unknown to the scanner: ×1.5, due to the default risk associated with an unclassified cookie.
  * **Essential / Strictly necessary**: ×0.5. Until the user has confirmed that the cookie is exempt from consent by applying the “exempted” flag, points are deducted as a precaution. The system has classified the cookie as Essential, but this classification must still be validated.

The points lost displayed for each individual cookie are rounded to the nearest whole number.

However, the final score is calculated using the sum of the unrounded points lost for all cookies. The resulting final score is then rounded to the nearest whole number.

#### Complete formula

**Score = 100 − the sum of all problematic cookies of:**

```
frequency in % × category weight × 0.10 if deposited before consent, or 0.15 if deposited after “refuse all”.
```

The sum is calculated using the unrounded points lost for each cookie. The final result is then rounded to the nearest whole number.

#### Practical examples

| Situation                                                                               | Cookie type    | Category      | Frequency                 | Points lost               | Final score  | Colour | Comment                                                                                         |
| --------------------------------------------------------------------------------------- | -------------- | ------------- | ------------------------- | ------------------------- | ------------ | ------ | ----------------------------------------------------------------------------------------------- |
| No issue                                                                                | –              | –             | –                         | 0                         | **100**      | Green  | Excellent compliance, routine monitoring                                                        |
| One advertising cookie before consent on the checkout page, representing 20% of traffic | Before consent | Marketing     | 20%                       | 20 × 2 × 0.10 = **4**     | **96**       | Green  | Non-compliant advertising cookie, moderate risk, correct it quickly                             |
| One Meta Ads cookie before consent on 100% of pages                                     | Before consent | Marketing     | 100%                      | 100 × 2 × 0.10 = **20**   | **80**       | Yellow | Serious violation, targeting without prior consent, high regulatory audit risk, priority action |
| One Google Analytics cookie before consent on 100% of pages                             | Before consent | Analytics     | 100%                      | 100 × 1 × 0.10 = **10**   | **90**       | Green  | Violation detected, check anonymisation and possible exemption                                  |
| One Essential cookie before consent on 100% of pages, not yet confirmed as exempted     | Before consent | Essential     | 100%                      | 100 × 0.5 × 0.10 = **5**  | **95**       | Green  | Cookie classified as Essential by the system, flag it as “exempted” to validate it              |
| One unknown cookie deposited before consent on 100% of pages                            | Before consent | Uncategorized | 100%                      | 100 × 1.5 × 0.10 = **15** | **85**       | Yellow | Unknown cookie deposited before consent, high risk, classify or remove it                       |
| One advertising cookie after “refuse all” on 90% of pages                               | After refusal  | Marketing     | 90%                       | 90 × 2 × 0.15 = **27**    | **73**       | Yellow | Serious violation after explicit refusal, absolute priority                                     |
| Severe cumulative violations, including multiple advertising and analytics cookies      | Mixed          | Mixed         | High cumulative frequency | More than 70 points lost  | **Below 30** | Red    | Major non-compliance, regulatory audit emergency, consult a GDPR expert                         |

#### Why these weights and rates?

* **Marketing ×2**: regulatory authorities impose severe penalties for advertising and targeting cookies, including Meta, Google Ads, remarketing and similar technologies.
* **Analytics ×1**: an exemption may be possible when processing is anonymised and limited, resulting in a reduced penalty.
* **Uncategorized ×1.5**: an unidentified cookie represents a potential risk, resulting in an intermediate penalty intended to encourage review.
* **Essential ×0.5**: points are deducted until the user applies the “exempted” flag to confirm the cookie’s exemption. Essential cookies must be confirmed.
* **Reduced rates, 0.10 and 0.15**: these rates balance the introduction of category multipliers and prevent excessive overall penalties.

#### Colours and urgency levels

|  Score | Colour | Meaning                              | Recommended action    | Comment                                                                                                                                                                                                                                                               |
| -----: | :----: | ------------------------------------ | --------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 90–100 |  Green | Very good compliance                 | Verify and stabilise  | Good level, but not a free pass. Correct the remaining issues as soon as possible and perform checks after every production release. The objective is to remain consistently above 95.                                                                                |
|  70–89 | Yellow | Moderate issues                      | Correct quickly       | Actions should be planned immediately. Prioritise the issues responsible for the greatest loss of points. If the decrease is caused by marketing cookies before consent or deposits after “refuse all”, treat them as high priority even if the score remains yellow. |
|  50–69 | Orange | Significant violations               | Correct as a priority | High level of exposure. Start a remediation plan immediately. The recommended target is to return above 70 quickly, and then above 90 as soon as possible.                                                                                                            |
|   0–49 |   Red  | Serious or systematic non-compliance | Immediate action      | Critical level, with a high risk of findings during an audit. Correct the issues immediately. First eliminate marketing cookies deposited before consent and all cookies deposited after explicit refusal, then stabilise the score above 70.                         |

Your score is recalculated at least once a day, usually with the flow.

If you flag a cookie as “consent exempted”, for example an Essential cookie or a compliant Analytics cookie, the score will generally increase quickly.
