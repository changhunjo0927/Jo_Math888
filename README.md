# Welcome
This is a course project page for MATH 888: Causal inference (Topics in mathematical data science).

## About Me
I am a Ph. D. candidate in the department of Mathematics at University of Wisconsin-Madison.
My research interests lie in theoretical understanding of machine learning.
In specific, I have worked on matrix completion with graph side information, and data poisoning attacks on algorithmic fairness.
For the first topic, I fully characterized the optimal sample complexity required for reliable estimation and quantified the efficacy of graph side information under a highly general model.
For the second one, I found the lower and upper bounds on the minimum data perturbation, measured in total variation distance, required for successful poisoning attack against risk minimization with fairness constraints.

With my background, I would like to design practical machine learning models with theoretical performace guarantees.
I think understanding causality can greatly improve machine learning models, so I am interested in studying causal inference.

## HW 2
#### Problem of interest
Mobile health interventions to people in their everyday life is available due to wearables and digital technology. The micro-randomized trial (MRT), where each individual is repeatedly randomized among multiple intervention options over the course of the trial, has been increasingly used to provide data to inform the construction of these interventions. In "Estimating Time-Varying Causal Excursion Effect in Mobile Health with Binary Outcomes, Qian et al. (2021)," the authors proposed the definition of causal excursion effect that can be used in primary aim analysis for MRTs with binary outcomes.

#### Variables
For each individual, there are $T$ time points at which the treatment can be delivered ($T$ does not have to be the same for each individual). A binary variable $A_t$ is a treatment option at time $t$, where $1$ means treatment and $0$ means no treatment. We denote by $X_t$ the vector of observations collected after time $t-1$ and up to time $t$: $X_1$ includes baseline covariates; $X_t$ contains the availability indicator $I_t$, where $I_t = 1$ if the individual is available for treatment at time $t$ and $I_t = 0$ otherwise. If $I_t = 0$, randomization will not occur at time $t$ and then $A_t = 0$.

We use overbar to denote a sequence of variables up to a time point. For example, $\bar{A}_t = (A_1, \ldots, A_t)$. Information accrued up to time $t$ is represented by the history $H_t = (X_1, A_1, X_2, A_2, \ldots, X_{t-1}, A_{t-1}, X_t) = (\bar{X}_t, \bar{A}_{t-1})$. The observed data on a generic individual, ordered in time, is $O= (X_1, A_1, \ldots, X_T, A_T, X_{T+1})$.

The proximal outcome, $Y_{t,\Delta}$, following the treatment assignment at time $t$, is a known function of the individual's data within a subsequent window of length $\Delta$, where $\Delta \geq 1$ is a positive integer. That is, $Y_{t,\Delta} = y(X_{t+1}, A_{t+1}, \ldots, X_{t+\Delta-1}, A_{t+\Delta-1}, X_{t+\Delta})$ for some known function $y(\cdot)$.

#### Causal effects we want to study
For an individual, let $X_t(\bar{a}_{t-1})$ and $A_t(\bar{a}_{t-1})$ be the observation that would have been observed and the $t$th treatment that would have been assigned, respectively, if s/he were assigned the treatment sequence $\bar{a}_{t-1}$. Then the potential outcomes are defined as
$$\{X_1, A_1, X_2(a_1), A_2(a_1), X_3(\bar{a}_2),\ldots, A_T(\bar{a}_{T-1}), X_{T+1}(\bar{a}_{T}) \mbox{ for all } \bar{a}_T \in \{0,1\}^{T}\}.$$
The potential outcome for the proximal outcome is $Y_{t,\Delta}(\bar{a}_{t+\Delta - 1})$. The potential history under the observed treatment sequence at time $t$ is $H_t(\bar{A}_{t-1}) = (X_1, A_1, X_2(A_1), A_2, X_3(\bar{A}_2),\ldots, X_t(\bar{A}_{t-1}))$.

We define the causal effect of $A_t$ on $Y_{t,\Delta}$ using the log relative risk scale:
$$\beta_M\{t, S_t(\bar{A}_{t-1})\} = \log \frac{ E \{ Y_{t,\Delta}(\bar{A}_{t-1}, 1, \bar{0}) \mid S_t(\bar{A}_{t-1}), I_t(\bar{A}_{t-1}) = 1 \} }{E \{ Y_{t,\Delta}(\bar{A}_{t-1}, 0, \bar{0}) \mid S_t(\bar{A}_{t-1}), I_t(\bar{A}_{t-1}) = 1 \}},$$
where $S_t(\bar{A}_{t-1})$ is a vector of summary variables formed from $H_t(\bar{A}_{t-1})$, and $\bar{0}$ is a vector of length $\Delta - 1$.
This causal effect denotes the contrast of the expected outcome under two "excursions" from the current treatment protocol: treatment at time $t$ and no treatment for the next $\Delta - 1$ time points, versus no treatment at time $t$ and no treatment for the next $\Delta - 1$ time points.

#### Hypothesis
The causal excursion effect can be used in primary aim analysis for MRTs with binary outcomes.


