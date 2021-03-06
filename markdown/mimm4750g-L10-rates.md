# MIMM4750G
## Rates of evolution
![](https://imgs.xkcd.com/comics/evolving.png)

---

# Why do viruses and bacteria evolve so rapidly?

<table>
  <tr>
    <td style="font-size: 22pt;">
      <ul>
        <li>Pathogens tend to have faster rates of evolution than their host.</li>
        <li>Hosts have larger genomes, more genes: more potential for defense?</li>
        <li>An evolutionary arms race.</li>
      </ul>
    </td>
    <td width="50%">
      <img src="/img/duchene.png"/>
      <small>
      Image credit: based on data from Duchene and Holmes (2018) Virus Evol; Bulmer et al. (1991) PNAS.
      </small>
    </td>
  </tr>

</table>

---

# Substitution Rates

* We measure rate of evolution by the number of substitutions per site per unit time.
* A substitution occurs when a new mutation appears *and* increases in frequency until it is established in the population.
* **Individuals do not evolve, populations do.**
![](/img/fixation.png)
<small><small>
Simulations of allele frequency evolution in R.
</small></small>

---

# Mutation rates

* The rate of evolution is limited by the input of new mutations.
* RNA viruses encode a reverse transcriptase that lacks proof-reading ability.
* Not every mutation becomes fixed.

<img src="https://science.sciencemag.org/content/sci/323/5919/1308/F1.large.jpg?width=800&height=600" width="450px"/>

<small><small>
Image credit: Gago *et al.* Science 323. 10.1126/science.1169202
</small></small>


---

# Population size
* Pathogen populations are structured by their compartmentalization into different infected hosts.
* The total pathogen population evolves like a smaller population: the *effective population size*.
* Population size influences the influx of new mutations, and the probability a new mutation will "fix" (genetic drift).
* Pathogens often undergo [population bottlenecks](https://en.wikipedia.org/wiki/Population_bottleneck) on transmission to the next host.

> What else causes a bottleneck in pathogens?

---

# Generation times

* Pathogens produce more generations relative to their hosts.
* Does this affect the rate of evolution?
* More mutation (genome copied more frequently)

| Species |  Generation time |
|---------|------------------|
| Escherichia coli | 15 hours |
| Staphylococcus aureus | 2 hours |
| HIV-1   | about 1 day&ast; |

&ast; This is a coalescent estimate.

---

# Selection

* Positive selection drives the fixation of beneficial mutations.
* Response to selection is transient - once the population has adapted, it no longer increases the rate of evolution.
* Changing environments creates more positive selection.
  * *e.g.,* Moving from one host environment to another.

---

# Why do rates matter?

* Measure the adaptation potential of pathogens.
* Sites that evolve faster than others can reveal targets of host-specific selection (antigenic sites).
* Conserved sites might make good targets for vaccine development / drug treatment.
* We can use the rate of evolution to extrapolate back in time.

---

<section data-state="markov-slide">
    <h1>Modeling evolution</h1>
    <ul>
      <li>Recall that sequence evolution is often modeled as a *continuous-time Markov chain*</li>
      <li>Constant rate of evolution - exponential waiting times.</li>
    </ul>
    <center>
    <div id="markov" class="fig-container"
         data-fig-id="fig-markov"
         data-file="/include/markov-chain.html"
         style="height:300px">
    </div>
    <div></div>
    </center>
    <small>Based on JS by [Victor Powell](http://setosa.io/blog/2014/07/26/markov-chains/index.html)</small>
</section>

---

# Substitution models

* The Jukes-Cantor model can be expressed by the following rate matrix:

$$ \left( \begin{matrix}
  \ast & \mu & \mu & \mu \\\\
  \mu & \ast & \mu & \mu \\\\
  \mu & \mu & \ast & \mu \\\\
  \mu & \mu & \mu & \ast \\
  \end{matrix}\right)$$

* The diagonal entries $\ast$ are set to $-3\mu$ so that each row sums to 0.

<!--


# Rates into probabilities

* To convert this rate matrix into the probability that $X$ transitions into $Y$ after time $t$, we have to use *matrix exponentiation*.
* This is a computationally costly operation that accounts for all possible transitions that may occur in time $t$.
* For a rate matrix $Q$, the probability matrix is:

  $$P(t) = \exp^{Q t}$$
* This is where the confounding of rate and time appears.
-->

---

# Other models

* The Hasegawa-Kishino-Yano (HKY85) model allows for unequal base frequencies ($\pi_i$) and a transition/transversion rate bias ($\kappa$).

$$\begin{matrix}
 & \begin{matrix}A\hspace{1ex} & C \hspace{1ex} & G \hspace{1ex} & T \hspace{1ex} \end{matrix} \\\\
\begin{matrix}A\\\\C\\\\G\\\\T\end{matrix} &
  \begin{pmatrix}
    \ast & \kappa \pi_C & \pi_G & \kappa\pi_T\\\\
    \kappa\pi_A & \ast & \kappa\pi_G & \pi_T\\\\
    \pi_A & \kappa\pi_C & \ast & \kappa\pi_T\\\\
    \kappa\pi_A & \pi_C & \kappa\pi_G & \ast
  \end{pmatrix}
\end{matrix}$$

> What does &ast; equal for the top row?

---

# Generalized models

* In general, there are six rates for a time-reversible (symmetric rates) model:

  $$ \left( \begin{matrix}
  \ast & a & b & c \\\\
  a & \ast & d & e \\\\
  b & d & \ast & f \\\\
  c & e & f & \ast \\
  \end{matrix}\right)$$

  where these rates are assigned in alphabetical order &mdash; $a$ is the rate from `$A\leftrightarrow C$`, $b$ is `$A\leftrightarrow G$`, etc.

---

# Rate variation

* Rates of evolution vary among different sites of the genome.
* Letting every site have its own rate creates too many parameters!
* Assume that rates belong to one of multiple rate *categories*.
* [Ziheng Yang](https://en.wikipedia.org/wiki/Ziheng_Yang) used a discretized\* [gamma distribution](https://en.wikipedia.org/wiki/Gamma_distribution):
<img src="/img/discgamma.png" width="400px"/>
<small>
\* split into intervals of equal probability
</small>

---

# Model specification

* PAUP* was a popular commercial software package for reconstructing phylogenies.
* It used a six-digit number ($abcdef$) to represent any kind of time-reversible nucleotide substitution model:
* *e.g.,* HKY85 becomes `010010`.
* This scheme is still used by other software, such as HyPhy and PhyML.

> What is the PAUP* model string for TN93?

---

# Why does the model matter?

* There are an enormous number of possible time-reversible models of nucleotide substitution.
* Using the wrong model (*model misspecification*) can bias estimates of other model parameters, *e.g.,* reconstructing the correct tree.
* The process of figuring out which model is best supported by the data is called *model selection*.

---

# Model selection

* We want to choose the model that has the best fit to the data.
* Adding parameters to the model improves the fit.
* We need to justify additional parameters!

  ![](/img/xkcd-curves-crop.png)

---

# Likelihood ratio test

* The *likelihood ratio test* (LRT) is a method of model selection that applies when one model is a special case of another.
  * *e.g.,* the JC69 model is a special case of HKY85 where $\kappa=1$.
* If the likelihood of model 1 (less complex) is $L_1$ and model 2 (more complex) is $L_2$, then this test statistic:
  $$-2\log\left(\frac{L_1}{L_2}\right) = -2(\log L_1 - \log L_2)$$
  follows a $\chi^2_k$ distribution.
* $k$ is the difference in the number of parameters.

---

# $\chi^2$-squared distribution

<img src="/img/dchisq.png" width="400px"/>

```R
x <- seq(0, 10, length.out=100)
plot(x, dchisq(x, df=1), type='l', ylab='Probability density',
     xlab=expression(chi^2), cex.lab=1.2, ylim=c(0, 0.5), lwd=2)
```

---

# Nested models

* LRT requires that the models are *nested* - one model must be a special case of another.
* For example, HKY85 is a special case of TN93, where `$r_{AG}=r_{CT}$`.
* What if we want to select between models that are *not* nested?
* This is a basis for *hypothesis testing* - "Do the data support the addition of this parameter?"
> Briefly describe a biological problem where the LRT would be useful.

---

# Akaike information criterion

* What if the models are not nested?
* The Akaike information criterion (AIC) penalizes the model's likelihood by the number of parameters

* *There is no statistical distribution*!  **The best model minimizes the AIC.**

  $$\text{AIC} = 2k - 2\log(L)$$

---

![](https://www.google.com/logos/doodles/2017/hirotugu-akaikes-90th-birthday-5767291382792192.3-2x.png)
