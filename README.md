# Central Limit Theorem Visualisation

An interactive, browser-based tool for exploring one of the most important results in probability and statistics: the Central Limit Theorem (CLT). Pick any distribution — uniform, exponential, wildly skewed, even one you draw yourself — sample from it repeatedly, and watch the distribution of sample means converge to a Gaussian in real time.

### [Launch App](https://brendanjameslynskey.github.io/Central_Limit_Theorem/)

---

## What is this?

The Central Limit Theorem says that if you take a large enough sample from *any* distribution with finite mean and variance, the average of that sample will be approximately normally distributed — no matter how non-normal the original distribution looks. More precisely, if $X_1, X_2, \ldots, X_n$ are independent and identically distributed random variables with mean $\mu$ and variance $\sigma^2$, then the standardised sample mean converges in distribution to a standard normal:

$$\frac{\sqrt{n}\,(\bar{X}_n - \mu)}{\sigma} \xrightarrow{d} N(0, 1) \quad \text{as } n \to \infty$$

This is why the bell curve appears everywhere: measurement errors, test scores, polling averages, manufacturing tolerances, stock returns over short horizons. Whenever you are averaging many small, independent effects, the CLT is at work. It is also the theoretical foundation for confidence intervals, hypothesis tests, and much of quality control — any time a procedure says "for large $n$, assume normality", it is invoking the CLT.

This app makes the theorem tangible. You choose a source distribution (including some very non-normal ones), set a sample size $n$, and draw thousands of sample means. Three plots update live: a histogram of the means with a theoretical Gaussian overlay, a Q-Q plot that tests normality visually, and a side-by-side convergence comparison strip for $n = 1$, $n = 5$, and $n = 30$. A real-time statistics panel tracks skewness, excess kurtosis, and a Kolmogorov–Smirnov test p-value so you can watch the sample means become "more normal" as you increase $n$ or accumulate more trials.

## Distributions

The app ships with seven parametric distributions and a free-form custom editor. Each one is chosen to illustrate a different aspect of the CLT.

| Distribution | Parameters | Properties | Why it's interesting |
|---|---|---|---|
| **Uniform** | $a$ (min), $b$ (max) | Mean $(a+b)/2$, variance $(b-a)^2/12$. Symmetric, zero skew. | Already symmetric, so convergence is fast — even $n = 2$ looks fairly Gaussian. A good baseline. |
| **Exponential** | $\lambda$ (rate) | Mean $1/\lambda$, variance $1/\lambda^2$. Right-skewed, memoryless. | Heavily skewed; demonstrates that the CLT still works, though convergence is noticeably slower than for the uniform. |
| **Bernoulli** | $p$ (success probability) | Mean $p$, variance $p(1-p)$. Discrete, takes values 0 or 1. | The simplest non-trivial distribution. At $p = 0.5$ it's symmetric and converges quickly; at extreme $p$ (e.g. 0.05) the skew slows convergence considerably. |
| **Poisson** | $\lambda$ (mean) | Mean $= \lambda$, variance $= \lambda$. Discrete, right-skewed for small $\lambda$. | A natural model for count data (arrivals, defects). At small $\lambda$ it is visibly asymmetric; the CLT smooths this out as $n$ grows. |
| **Beta** | $\alpha$, $\beta$ | Mean $\alpha/(\alpha+\beta)$, variance $\alpha\beta/[(\alpha+\beta)^2(\alpha+\beta+1)]$. Bounded on $[0, 1]$. | Endlessly flexible — U-shaped ($\alpha = \beta = 0.5$), uniform ($\alpha = \beta = 1$), right-skewed, left-skewed. Great for stress-testing the CLT with unusual shapes. |
| **Geometric** | $p$ (success probability) | Mean $(1-p)/p$, variance $(1-p)/p^2$. Discrete, always right-skewed. | Models the number of failures before the first success. Very heavy right tail at small $p$, so you need a larger $n$ to see convergence. |
| **Chi-squared** | $k$ (degrees of freedom) | Mean $k$, variance $2k$. Continuous, right-skewed (especially for small $k$). | Appears in every goodness-of-fit and variance test. At $k = 1$ or $2$ the shape is far from normal; the CLT tames it. |
| **Custom** | Draggable bars (20 bins) | Mean and variance computed on the fly from the bar heights. | Draw literally any discrete distribution — bimodal, flat, spiky — and watch the CLT still deliver a Gaussian for the sample means. |

## Features

- **8 source distributions** — seven parametric families plus a draw-your-own custom editor, all with adjustable parameters via sliders.
- **Custom distribution editor** — click and drag bars on a canvas to sculpt any shape; probabilities are normalised automatically.
- **Source PDF/PMF plot** — see the shape of the population you are sampling from, updated instantly as you tweak parameters.
- **Live histogram of sample means** — accumulates trial-by-trial with a dashed Gaussian $N(\mu, \sigma^2/n)$ overlay so you can see the fit improve.
- **Q-Q plot** — sample quantiles vs. theoretical normal quantiles; points hug the $y = x$ line as normality improves.
- **Convergence comparison strip** — three side-by-side histograms for $n = 1$, $n = 5$, and $n = 30$ (2 000 trials each) so you can see convergence at a glance.
- **Real-time statistics panel** — displays sample mean, theoretical mean, sample std, theoretical std (i.e. $\sigma/\sqrt{n}$), skewness, excess kurtosis, and a one-sample Kolmogorov–Smirnov test p-value against the predicted normal. Values are colour-coded green (close to normal) or amber (still converging).
- **Sampling controls** — sample size $n$ (1–100), trials per batch (100–50 000), and animation speed, all adjustable on the fly.
- **Animation mode** — press *Run* for continuous sampling at the chosen speed; press *Sample* for a single batch; press *Reset* to clear.
- **Responsive dark-theme UI** — works on desktop and mobile; sidebar collapses to a single column on narrow screens.

## Built with

- [Plotly.js](https://plotly.com/javascript/) — interactive, GPU-accelerated charting
- Vanilla JavaScript — no frameworks, no build step, single `index.html` file
- Hosted on [GitHub Pages](https://pages.github.com/)
