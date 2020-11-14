Fall 2018 
DSBA 5122
Final Project Report: Workers’ Compensation Analysis for a NC Insurance Company
by Kaci Allen, P. Marie Barrier, Maithili Shahane 

Data Overview 
The data files for this project came from one of the clients of a North Carolina company that manages workers’ compensation claims. Client name and location specifics were not provided to us because it was protected for purposes of confidentiality. 
The client insurance company is interested in using data analytics in order to become more efficient and responsive to their claimants. We used a strong cost analysis to drive a lot of our exploration. During our investigation we chose to add a component of preventative analysis, offering a couple proactive suggestions for our client rather than staying strictly response-only. 
The gist of workers’ compensation is as follows: When a worker of a participating company is injured in performance of her/his job, she/he can file a claim for the medical expenses and loss of wages related to the injury. When a claim is filed for the first time, a unique claim identifier is created and the details of the claims are recorded. The claim details are updated as payments are made to settle the claim.  Payments can be made for various activities related "to a claim, such as doctor visit, pharmacy, etc." 
The claim information we analyze here is for incidents occurring between 1967 and 2014. We gave particular focus to variables relating to reporting timeframes, itemization of claim cost, recovered money (subrogation), and how injury specifics tied into these variables. 
We had 3 databases, which we merged, all containing information from the prospective of the insurance company’s records of worker compensation claims. This does cause some redundancy within the variables but often there was a difference in reporting format (i.e. “SubrogationPayment” is negative values which are effectively the same as “TotalRecovery” which is represented as positive values). We chose to keep all variables, even when similar, because it allowed for some nice variation in graphing perspective. Note that some graphs will use different variables for things like claim cost without loss of general patterns. For example: “TotalIncurredCost” represents all money paid, not accounting for money recovered, while “TotalPaid” is the final amount paid out by the insurance company after they have subrogated (recovered) as much money as possible from any other liable parties. Also, note that the variable “Indemnity” is not representing what the official insurance definition would suggest (lost time from work, medical costs, and additional living expenses). Our client has stored “Indeminity” in their database to represent only costs pertaining to payment for time missed from work. Medical costs (“MEDPayment”) and additional living expenses (“ALEPayment”) were tracked separately in their database.

Data Prep AND Exploratory Data Analysis (R and SAS details)   
Because our dataset was large, over 5MB, and originated as three distinct databases we first merged our databases into one. We found SAS to be useful in this merger. 
Image illustration database merger via SAS (below):
 


Following this merger, it was important to understand our variables and data a little better. Below find the list of variables and the data summary provided using R:

 
  

In addition to cleaning, merging, and investigating our data, we also reached out to a couple of insurance professionals in our quest to better understand the basics of how workers’ compensation claims work.  It was important to understand how different fields related before getting too involved with our data. 
Total Cost=Reserves+Indemnity+Other Paid-Total Recovery
Total Paid=Indemnity+Other Paid
Indemnity=Compensation for Lost Work Time
Other Paid=Medical+ALE (additional living expenses)
While we didn’t need to use these relationships too directly within our final graphs, these relationships did help us to better understand the variables. 
Other clarification that we found useful was that litigation cost was from the perspective of the insurance company, and doesn’t necessarily mean a court case occurred. Often this can be money paid outside of court to make a client “happy”. Also, reporting dates were tracked including when the incident occurred, when the employer was notified of the accident, when the employer told their insurance company about the accident, and how long it took for the insurance company to begin responding to the claim. “ClaimReceivalTurnAround” gives the number of days between the actual incident until the insurance company started working on the claim officially. We relied on this variable when tracking late reporting problems caused by the insurance company since there is a direct correlation between the time it takes for the insurance company to start a claim and the lapse of days between when the incident occurred and when the claim was assigned to an adjuster.

Descriptive Statistics
We focused on connections that could help our client save money. Specifically, this included graphs about injury type (cost and frequency), investigating which part of the claim generally costs the most, observing likely predictors connected to litigation costs, and looking closely at money recovered via subrogation. There was some curiosity about claimant demographics, and we have included a few graphs at the end of this report regarding gender specifically. We do not include any information about demographics in our main study, because we were advised that doing so for workers’ comp coverage is illegal and considered discriminatory.
Below are images giving an overview of what our graphs discovered:
 
 
 
 
 
Looking through these graphs (above) we focused on general trends. We noticed that, generally, higher claim cost was associated with time out of work. We also noted that strains and contusions consistently keep claimants away from work longer, cost more overall, and tend to accrue more litigation fees. However, there were a few discrepancies. For instance, we see from the graphs that, while mental stress is one of our highest average claim costs, it does not keep claimants out of work for a lot of time compared to other injuries. While this is a small contradiction, it should be noted that the general patterns do not lose value or meaning. The key pattern is that missing a lot of work is the most costly thing that can happen to a claimant. Our client insurance company requested ways to be more efficient, so our graphs on litigation costs and subrogation served to let us know if there was anything they could improve. We noticed that while some litigation can likely not be avoided for injuries (typically those slower to heal), it does look like late reported is a strong predictor of amount of litigation. If a claim is not being processed within about 12 months of the initial incident, we see that legal fees greater than $10,000 are expected. Further we can see that as time passes beyond the 1 year mark, litigation costs increase substantially. Regarding subrogation, we note that the rate of money recovered compared to total claim cost is generally close to 0%.

Conclusions
From our visual observations we advise our client to be proactive. Late reporting needs to be eliminated or minimized, with the goal of never exceeding 12 months. Legal costs increase rapidly from the 12 month point on. While there are some injuries that are costly on the medical expense side only such as trunk, lower extremities, and mental stress, the worst thing that can happen is for the insured to be missing work for too long. A lot of cost is accrued in the category of lost wages, with particular concern for contusions and strains. We recommend strong safety precautions to be required for all insured customers. In addition to requiring protective back braces, hard hats, eye wear and other items that could specifically help reduce strains and contusions, we noticed that using a lot of man-power to file and collect subrogation fees may not be the best use of time. We recommend, instead, having more random auditing done to insure that safety precautions are being observed by those being insured.

Appendix Comments (i.e. gender - graphs but why we avoided the topic)
While we were advised that workers’ compensation benefits must legally be based on job type, not individual demographics, we spent some time looking at gender demographics. There is not a strong connection between gender and claim cost or injury type, but we were curious and wanted to share. See our gender comparison graphs below:
 
 
 
