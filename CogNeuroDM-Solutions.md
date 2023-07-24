# Solutions to Exercises for the 26th IrBO Summer Camp lecture "The Neuroscience of Decision Making"

## Exercise 1

**Assuming a 0.5 probability of signal presence, show $$\mathbb{P}(\mathrm{correct})=\frac{\beta(z)+1-\alpha(z)}{2}$$**

We decompose the probability of a correct response to the probability of a correct response in the presence of signal and the probability of a correct response given the absence of signal:
$$
\begin{aligned}
\mathbb{P}(\mathrm{correct}) &= \mathbb{P}(+)\mathbb{P}(r\geq z|+) + \mathbb{P}(-)\mathbb{P}(r<z|-)\\
&= \mathbb{P}(+)\mathbb{P}(r\geq z|+) + \mathbb{P}(-)\big[ 1-\mathbb{P}(r\geq z|-)\big] \\
&= \frac{1}{2}\beta(z) + \frac{1}{2}\big[ 1-\alpha(z)\big] \\
&= \frac{\beta(z)+1-\alpha(z)}{2}
\end{aligned}
$$

## Exercise 2

**Show that the area under a ROC curve is precisely equal to the probability of a correct response. $$\mathbb{P}(\mathrm{correct})=\int_0^1\beta \mathop{\mathrm{d}{\alpha}}$$**

We prove this equality by considering the 2-armed forced choice (2AFC) task in order to have a well-defined probability for each threshold value. Assuming equal probabilities for the $(+)$ or $(-)$ stimulus on the first arm, the probability of a correct response when the first arm stimulus is $(+)$ is equal to the probability of a correct response on the whole.

This probability is the sum of hit rates for every possible threshold multiplied by the possibility of that threshold (keep in mind that the threshold in a 2AFC task is the response to the second arm: $z=r_2$):

$$
\mathbb{P}(\mathrm{correct})=\int_{-\infty}^{\infty} \beta(z)\mathbb{P}(z|-)\mathop{\mathrm{d}{z}}
$$

Additionally, the probability of a false alarm, which is the probability of response $r=r_1$ being greater than $z=r_2$ given stimulus $(-)$, should be written as

$$
\alpha(z)= \int_z^{\infty}\mathbb{P}(r|-)\mathop{\mathrm{d}{r}}
$$

Differentiating both sides with respect to $z$ we have

$$
\begin{aligned}
\frac{\mathrm{d}\alpha(z)}{\mathrm{d}z}&=\frac{\mathrm{d}}{\mathrm{d}z}\int_z^{\infty}\mathbb{P}(r|-)\mathop{\mathrm{d}{r}}
\\ &= \mathbb{P}(\infty|-)-\mathbb{P}(z|-)
\\ &= - \mathbb{P}(z|-)
\end{aligned}
$$

Making the replacement $\mathbb{P}(z|-)\mathrm{d}z \to -\mathrm{d}\alpha$ in the first equation of this exercise we have

$$
\begin{aligned}
\mathbb{P}(\mathrm{correct})&=-\int_{1}^{0} \beta\mathop{\mathrm{d}{\alpha}}
\\ &= \int_{0}^{1} \beta\mathop{\mathrm{d}{\alpha}}
\end{aligned}
$$

## Exercise 3

**Show that the slope of the ROC curve is the likelihood ratio of the threshold. $$\frac{\mathrm{d}\beta}{\mathrm{d}\alpha}=\mathrm{LR}(z)$$**

We already saw that $\alpha$ could be written as the sum of the probabilities of a range of responses given a $(-)$ stimulus: $\alpha(z)= \int_z^{\infty}\mathbb{P}(r|-)\mathop{\mathrm{d}{r}}$. The hit rate can also be written in the same way by inverting the stimulus sign:

$$
\beta(z)= \int_z^{\infty}\mathbb{P}(r|+)\mathop{\mathrm{d}{r}}
$$

Now let us calculate the slope of the ROC curve.

$$
\begin{aligned}
\frac{\mathrm{d}\beta}{\mathrm{d}\alpha} &= \frac{\mathrm{d}\beta}{\mathrm{d}z} \cdot \frac{\mathrm{d}z}{\mathrm{d}\alpha}
\\ &= \frac{\mathbb{P}(z|+)}{\mathbb{P}(z|-)}
\\ &= \mathrm{LR}(z)
\end{aligned}
$$

## Exercise 4

**What is $\alpha$'s sign?**

To determine $\alpha$'s sign, we will go through the process of transforming the equation describing the dynamics of population 1's potential in time ($\frac{\mathrm{d}h_{\mathrm{E,1}}}{\mathrm{d}t}$) from the three population model to the two population model.

Let's write our two assumptions.

1. $\tau_{\mathrm{I}}/\tau_{\mathrm{E}} \to 0$, and therefore the dynamics of the inhibitory population is instantaneous, and its potential is always at the fixed point: $h_\mathrm{I}=w_\mathrm{IE}\big[g_\mathrm{E}(h_{\mathrm{E,1}})+g_\mathrm{E}(h_{\mathrm{E,2}})\big]$
2. $g_{\mathrm{I}}(h_{\mathrm{I}})=\gamma h_{\mathrm{I}}$ where $\gamma>0$.

Now let's rewrite the three population model's equation.

$$
\begin{aligned}
\tau_\mathrm{E}\frac{\mathrm{d}h_{\mathrm{E,1}}}{\mathrm{d}t}&=-h_{\mathrm{E,1}}+w_\mathrm{EE}\,g_\mathrm{E}(h_{\mathrm{E,1}})+w_\mathrm{EI}\,g_\mathrm{I}(h_{\mathrm{I}})+RI_1
\\ &= -h_{\mathrm{E,1}}+w_\mathrm{EE}\,g_\mathrm{E}(h_{\mathrm{E,1}})+w_\mathrm{EI}\,\gamma w_\mathrm{IE}\big[g_\mathrm{E}(h_{\mathrm{E,1}})+g_\mathrm{E}(h_{\mathrm{E,2}})\big]+RI_1
\\&=-h_{\mathrm{E,1}}+\big[w_\mathrm{EE}+\gamma w_\mathrm{EI}w_\mathrm{IE}\big]g_\mathrm{E}(h_{\mathrm{E,1}})+\gamma w_\mathrm{EI}w_\mathrm{IE}g_{\mathrm{E}}(h_{\mathrm{E,2}})+RI_1
\end{aligned}
$$

By comparing this final equation to the equation provided for the two population model, $\tau_\mathrm{E}\frac{\mathrm{d}h_{\mathrm{E,1}}}{\mathrm{d}t}=-h_{\mathrm{E,1}}+\big(w_\mathrm{EE}-\alpha\big)g_\mathrm{E}(h_{\mathrm{E,1}})-\alpha g_{\mathrm{E}}(h_{\mathrm{E,2}})+RI_1$, we can see that $\alpha=-\gamma w_\mathrm{EI}w_\mathrm{IE}$. Since $\gamma>0$, $w_\mathrm{EI}<0$ (is an inhibitory connection), and $w_\mathrm{IE}>0$ (is an excitatory connection), $\alpha$'s sign is positive. $$\alpha>0$$

## Exercise 5

**Assuming only the product rule for probabilities, show that when random variables X and Y are independent given Z, then $$\mathbb{P}(x,y|z)=\mathbb{P}(x|z)\mathbb{P}(y|z)$$**

The independence of $X$ and $Y$ given $Z$ can be written as $$\mathbb{P}(x|y,z)=\mathbb{P}(x|z)$$ This means that whether or not $Y$ is given is irrelevant for the calculation of the conditional probability of $X$ given $Z$.
Now let's write the product rule for these three random variables $$\mathbb{P}(x,y|z)=\mathbb{P}(x|y,z)\mathbb{P}(y|z)$$
We can readily see that we can arrive at our desired expression by simply replacing $\mathbb{P}(x|y,z)$: $$\mathbb{P}(x,y|z)=\mathbb{P}(x|z)\mathbb{P}(y|z)$$

## Exercise 6

**Why is the variance of the posterior never larger than that of either component?**

The variance of the posterior is $\frac{1}{J_1+J_2}$. Since the precision of a distribution is the inverse of its variance, we can write  
$$
\begin{aligned}
\sigma^2_{\mathrm{post}}&=\frac{1}{\frac{1}{\sigma^2_1}+\frac{1}{\sigma^2_2}}
\\ &= \frac{\sigma_1^2\sigma_2^2}{\sigma_1^2+\sigma_2^2}
\end{aligned}
$$
Subtracting this value by either of the two prior variances, we see that the result is lesser than or equal to 0.
$$
\begin{aligned}
\sigma^2_{\mathrm{post}}-{\sigma^2_1}&=\frac{\sigma_1^2\sigma_2^2}{\sigma_1^2+\sigma_2^2}-{\sigma^2_1}
\\ &= \frac{\sigma_1^2\big[\sigma_2^2-(\sigma_1^2+\sigma_2^2)\big]}{\sigma_1^2+\sigma_2^2}
\\ &= \frac{-\sigma_1^4}{\sigma_1^2+\sigma_2^2} \leq 0
\end{aligned}
$$ and similarly
$$
\begin{aligned}
\sigma^2_{\mathrm{post}}-{\sigma^2_2}
= \frac{-\sigma_2^4}{\sigma_1^2+\sigma_2^2} \leq 0
\end{aligned}
$$
Combining these two inequalities we can readliy see that $$ \begin{aligned}\sigma_\mathrm{post}^2 &\leq \sigma_1^2 \\ &\leq \sigma_2^2\end{aligned}$$
