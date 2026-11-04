# Thurmond Amendment: Exploratory Data Analysis for Fair Housing Reform

A team **exploratory data analysis (EDA)** of drug-distribution conviction records across 7 U.S. states. We cleaned each state's data and produced descriptive statistics and visualizations to support a national campaign to repeal the Thurmond Amendment, a 1988 law that lets landlords permanently deny housing to anyone with a past drug-distribution conviction.

**[📊 Demo Day results deck](https://docs.google.com/presentation/d/19nsUTgT177lyC2wwmVLPI6tF6JNSBn3pQI6ZV4pnvr0)** · **[🖼 Project poster](https://docs.google.com/presentation/d/1SEd_IRdikWMxxKl4uHQzBU89ePsjm8mavedPaVsAgZk)**

> **Team project through BU Spark! (Fall 2024).**
>
> **Team:** Matthew Cheng, Manav Kandoi, Gayoung (Ellena) Ko and Ozgur Sen.
>
> Mentors: Oluwatamilore Ajibade (Project Manager), Ethan Chang (Technical Project Manager) and Professor Jessica Simes (Expert-in-Residence). We met regularly with the client and presented the results at BU Spark! Demo Day.

### My role

We split the work by state. I owned the EDA for **Wisconsin** and **North Carolina**, covering data review, cleaning, descriptive analysis and visualization. My teammates covered the remaining states.
- **Wisconsin (1990–2023):** I set a 3g-or-less threshold to separate small-scale from large-scale convictions, then built cocaine-specific quantity buckets because quantity thresholds differ by drug. I calculated the disparity ratios: **11.7× overall** and **15.9× for small-scale cases**, the highest of any state in the project. I also spotted a 2012 shift in racial patterns and explored a likely driver: a rise in small heroin cases.
- **North Carolina:** I cleaned 13 yearly felony-activity datasets and split the cases by court level to gauge severity. After cleaning, very few relevant records were left, so our team and the client decided to drop the state rather than report misleading results.

---

## The problem

Under the Thurmond Amendment, a drug-distribution conviction means a lifetime loss of fair-housing protections. This applies no matter how small the offense was or how long ago it happened.

Our client, [Yusuf Dahl](https://www.yusufdahl.com/), was convicted at 18. In the 25 years since, he has earned a Master's in Public Affairs from Princeton and become a real estate investor and affordable-housing advocate, and he is still denied housing. He is leading the campaign for the **Fair Future Act**, which would repeal the amendment.

**Our question:** who is actually affected? Is it the large-scale "kingpins" the law was meant to target, or small-scale offenders, and are some groups hit harder than others?

## Approach

We received conviction and disposition data from state agencies, researchers and the client. Every state recorded things differently, so we ran the same four-step EDA framework on each dataset:

1. **Scope:** what years does the data cover?
2. **Filter:** can we isolate drug *sale/distribution* convictions? (For example, keyword filters, or specific statutes such as New York's Article 220.)
3. **Severity:** can we separate small-scale from large-scale offenders? (We used drug-quantity thresholds, sentence length, or the type of court.)
4. **Disparity:** if race or ethnicity is recorded, compare each group's share of convictions to its share of the state population.

**How the disparity ratio works**
- *Likelihood factor* = a group's share of convictions ÷ its share of the state population (from Census data).
- *Disparity ratio* = Black likelihood factor ÷ white likelihood factor.

## Key findings

**Disparity ratios: how much more likely Black residents are than white residents to have a drug-distribution conviction, relative to population**

| State | Disparity ratio | Notes |
| --- | --- | --- |
| Wisconsin | **11.7×** (15.9× for ≤3g cases) | 1990–2023 |
| Pennsylvania | 5.4× | 2014–2022 |
| New York | 4.8× | ~99% of cases were small-scale |
| Massachusetts | 4.7× (Hispanic vs. white: 5.5×) | 2019–2024 |
| Nevada | 4.5× | Sentences of 1 year or less |
| Ohio | 3.9× (4.6× for marijuana-only cases) | 68,254 incidents, 1998–2024 |

**Most people affected are small-scale offenders, not kingpins**
- **New York:** about 99% of drug sale/manufacture convictions fell outside the "major trafficker" statute.
- **Virginia:** 49% of 90,094 convictions led to less than a year of incarceration or none, yet every one carries a lifetime housing ban. About 19% were marijuana-related.
- **Wisconsin:** 81% of people convicted of cocaine distribution were involved with 10g or less.
- **Ohio:** marijuana was the most common drug, with 24,907 incidents. 17,473 incidents involved *only* marijuana.

**Trends worth noting**
- **Wisconsin:** Black convictions outnumbered white convictions (for ≤3g) until 2012, when the pattern flipped. A rise in small heroin cases in 2010–2014 may have contributed.
- **Pennsylvania:** heroin cases fell sharply after fentanyl appeared in 2019. Cocaine's share is growing.

## Conclusion

This was descriptive, exploratory work, not causal analysis. Even so, the patterns were consistent. Tens of thousands of people in these states lose fair-housing protections for life under the Thurmond Amendment. The law falls hardest on Black and Hispanic communities, and it mostly reaches small-scale offenders instead of the high-level traffickers it was meant for.

## Challenges and limitations

- **Defining a "minor" drug conviction:** the hardest question was what quantity counts as small-scale. Each drug has its own threshold (a few grams of heroin is not comparable to a few grams of marijuana), and states record quantities in different units and buckets, when they record them at all. We had to set drug-specific thresholds, or use proxies such as sentence length or court type where quantities were missing, before we could say how many convictions were minor.
- **Inconsistent data:** every state recorded convictions differently, with different fields, drug categories and quantity buckets. A single shared framework let us compare them.
- **Data quality:** some records were clearly wrong (for example, one Ohio entry listed 470,000,000g of cocaine). We flagged these, verified them against the raw data, and applied cutoffs.
- **Missing fields:** Virginia had no demographic data. North Carolina's data was too sparse after cleaning, so we dropped it together with the client.
- **Next step:** higher-quality, more consistent data across all states.

## Tech stack

Python · pandas · Matplotlib · Seaborn

---

*Gayoung (Ellena) Ko, Matthew Cheng, Manav Kandoi and Ozgur Sen · BU Spark!, Boston University, Fall 2024*
