# MIMM4750G
## Molecular clocks

![](https://imgs.xkcd.com/comics/estimating_time.png)

---

# What is a molecular clock?

<table>
  <tr>
  <td style="font-size: 18pt"><ul>
    <li>The molecular clock is a hypothesis that evolution at a molecular level (*e.g.,* proteins) occurs at a constant rate.</li>
    <li>Based on linear relationship between the time that species diverged from their common ancestor, and the number of amino acid differences in homologous proteins (*right*).</li>
    <li>The molecular clock does *not* "tick".</li>
  </ul></td>
  <td width="50%">
    <img src="/img/Dickerson.png"/>
  <small>Figure from RE Dickerson (1971) J Mol Evol 1: 26.</small>
  </td>
  </tr>
</table>


---

# Neutral theory

<table>
  <tr>
  <td style="font-size: 18pt"><ul>
    <li>The <a href="https://en.wikipedia.org/wiki/Neutral_theory_of_molecular_evolution">neutral theory</a>: "the great majority of evolutionary changes at the molecular level [...] are caused not by Darwinian selection but by random drift"</li>
    <li>Without selection, nucleotide substitutions should be a random process at a constant rate.</li>
    <li>Today, this model is denoted the "strict" clock and is seldom supported by sufficient data.</li>
  </ul></td>
  <td width="35%">
    <img src="https://www.genetics.org/content/genetics/202/4/1243/F1.medium.gif"/>
  <small>
  Motoo Kimura and James F. Crow
  <small>Image credit: Museum of Genetics, Federal University of Rio Grande do Sul, Brazil</small>
  </small>
  </td>
  </tr>
</table>

---

# Testing for a clock

<table>
  <tr>
  <td style="font-size: 18pt"><ul>
    <li>If a clock exists, then sequences should become more distant from the common ancestor as a *linear trend* over time.</li>
    <li>If the rate of evolution increases (decreases) over time, we expect this trend to be concave up (down).</li>
    <li>If the rate varies from one lineage to the next, the trend should be noisier.</li>
  </ul></td>
  <td width="55%">
    <img src="http://currents.plos.org/outbreaks/files/2014/04/EBOV_cds_mb_path.png"/>
  <small>
  Root-to-tip regression of a Bayesian tree for concatenated coding regions of Ebola virus.
  <small>Image credit: Dudas and Rambaut (2014) PLOS Currents Outbreaks</small>
  </small>
  </td>
  </tr>
</table>

---

# Clocks and trees

* When we reconstruct a tree by fitting a model of evolution, the lengths of branches are measured in units of *expected numbers of substitutions*.

* This weird unit exists because most models are scaled to $\mu\times t$ (the rate of evolution multiplied by time).

* We say that the rate and time are *confounded* - it is impossible to estimate one parameter without knowing the true value of the other.

---

# Confound it!

<img src="/img/timetree.png" width="500px"/>

* A tree can be stretched back in time ($\uparrow t$) and explain the data with *exactly the same likelihood* if we decrease the rate ($\downarrow \mu$).
* Conversely, if we compress the tree forward in time ($\downarrow t$), we obtain the same likelihood by speeding up the rate ($\uparrow \mu$).

---

# Estimating the clock

* For infectious diseases, measurable evolution can occur on a time scale of weeks.
* This means that a branch of the tree can "grow" in the time between sampling different infections.
<img src="/img/timetree-scaled.png" width="400px"/>
* We can use sampling times to "pin down" the tree and prevent the free-scaling problem.

---

>Q1: Why doesn't this approach of "pinning down" tips of a molecular phylogeny in time work for animals like humans?

---

# Rooting the tree

* If we are directly measuring *time*, then we must impose a direction of time's flow on the tree.
* This means that we must locate the tree's *root* (the earliest point in time).
* Rooting trees is difficult!  By definition, it is the point that is the most distant in time &mdash; it cannot be directly observed.


---

# Outgroup rooting

* An *outgroup* is a species or infection that is not closely related to the sample set.
* We place the root at the point where the branch leading to the outgroup intersects the tree.
* If the outgroup is too *close*, then the root is too influenced by sampling bias (our choice of outgroup).
* If the outgroup is too *distant*, then where it intersects the tree is subject to random variation.

---

# Choosing an outgroup

* There is no objective framework to select an "optimal" outgroup.
* We often reach an informal consensus about which outgroup to use, without any other rationale.
  * *e.g.*, HIV-1 subtype D is a conventional outgroup for subtype B.
* If an early isolate of the pathogen is available, it is sometimes used as an outgroup.
  * *e.g.,* West Nile virus isolate B956 ([isolated in 1940](https://www.ajtmh.org/content/journals/10.4269/ajtmh.1940.s1-20.471)).
* **Use different outgroups to see how robust your conclusions are to choice of outgroup!**

---



<table>
  <tr>
    <td style="vertical-align:middle">
      <h1>Root-to-tip regression</h1>
      <ul>
        <li>We can simultaneously estimate the clock (rate of evolution) *and* locate the root.</li>
        <li>Try different placements of the root and look at the plot that results.</li>
        <li>The "best" root should give the cleanest (positive) linear trend.</li>
        <li>(*right*) Phylogeny and root-to-tip plot for Ebolavirus isolates from 2013-2016 epidemic in West Africa.</li>
      </ul>
      <small>
      Image credit: Holmes <i>et al.</i> (2016) Nature 538. https://doi.org/10.1038/nature19790
      </small>
    </td>
    <td width="35%">
      <img src="/img/nature19790.png" width="300px"/>
    </td>
  </tr>
</table>

---

<iframe src="/include/rtt.html" width="1000px" height="500px">
</iframe>

---

# Origin of HIV-1

* This concept was first used to estimate the origin date of HIV-1.

  <img src="/img/li-tanimura-sharp.png" width="600px"/>

<small>
Tree from Li, Tanimura and Sharp (1988) Mol Biol Evol 5: 313.
</small>

---

# Origin of HIV-1

<img src="/img/korber-fig1.png" width="400px"/>

<small>
Figure from B Korber *et al.* (2000) Science 288.
</small>

---

<img src="/img/inca-rtt.png" width="400px"/>

> Q2.  In the "root to tip" plot above, write down which letters correspond to: (i) $t$; (2) $\mu t$; (3) $\mu$, (4) time of the root.

<small>
Figure taken from an analysis of respiratory syncytial virus by C Agoti *et al.* 2014, Emerg Infect Dis 20: 957.
</small>

---

# Problems with RTT

* RTT assumes that:
  * every point is an independent observation
  * the clock is constant (strict)
* Tips share common ancestry - the distance of a tip from the root is largely shared with neighbouring tips
* Not a reliable method for dating the root, but a decent rough estimate.
* A good, quick check to see if your data are "clock-like"

---

# Clocks on trees

* Fitting a clock model to a tree explicitly accounts for common ancestry of data
* The length of each branch estimates, $t$, can be directly estimated from dated tips or dated nodes ("fossil record").
* Strict clock assumes constant rate of evolution, $\mu$, throughout entire tree.

---

# Separation of SIV at end of last ice age
<img src="/img/bioko.png" width="750px"/>
<small>
M Worobey *et al.* (2010) Science 329. doi://10.1126/science.1193550
</small>

---

# Relaxing the clock

* Relax the strict clock by modeling how the rate changes along branches of the tree.
* Allowing every branch to have its own rate would create too many parameters!
* There are generally four categories of relaxed clocks:
  1. autocorrelated
  2. uncorrelated
  3. discrete multi-rate
  4. local multi-rate

---

# Autocorrelated clocks

* The clock rate is an evolving characteristic along the tree.
* Rate at branch $i$ is drawn from a distribution centered at the rate of the previous branch:

$$\mu_i \sim \mathcal{N}(\mu_j, \sigma^2 t)$$

<img src="/img/autocorrelated-clock.png" width="300px"/>

<small>
Image credit: S Ho and S Duchene (2014) Molecular Ecology, doi: 10.1111/mec.12953
</small>

---

# Uncorrelated clocks

* The clock rate of each branch is sampled from a continuous probability distribution, with parameters to estimate:

<table>
<thead>
<tr><th>Lognormal</th><th>Gamma</th></tr>
</thead>
<tbody>
<tr>
<td style="height: 350px">
<iframe src="http://learnbayes.org/demo/stat-distributions-js/distributionDisplay.html?dist=lognormal" width="500px" height="400px">
</iframe>
</td>
<td style="height: 350px">
<iframe src="http://learnbayes.org/demo/stat-distributions-js/distributionDisplay.html?dist=gamma" width="500px" height="400px">
</iframe>
</td>
</tr>
</tbody>
</table>

<small>
Source: Richard Morey, <a href="https://github.com/richarddmorey/stat-distributions-js">stat-distributions-js</a>
</small>

---

# Discrete and local multi-rate clocks

<table>
<tr>
<td>
  <ul>
    <li>A discrete clock model is like FEL: it assumes there are $k$ rate categories and tries to assign each branch to one of them.</li>
    <li>A local clock model assumes there are $k$ rate categories that are spread across different parts of the tree.</li>
    <li>The local clock was developed by Anne Yoder and Ziheng Yang&ast; to accommodate different evolutionary rates in mtDNA among mammalian species.</li>
  </ul>
</td>
<td width="50%">
  <img src="/img/worobey-flu.png" width="450px"/>
  <small>
  Image credit: Worobey <i>et al.</i> (2014) Nature 508. https://doi.org/10.1038/nature13016
  
  &ast; Yoder and Yang (2000) Mol Biol Evol 17: 1081, https://doi.org/10.1093/oxfordjournals.molbev.a026389
  </small>
</td>
</tr>

---

# Ebolavirus outbreak in West Africa

![](/img/gire-ebola.svg)

<small>
SK Gire *et al.* 2014. Genomic surveillance elucidates Ebola virus origin and transmission during the 2014 outbreak. *Science* 345: 1369-1372.
</small>

---

# Further readings

* [Phylogenetic Analysis of Guinea 2014 EBOV Ebolavirus Outbreak](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC4024086/)
* [Timing the Ancestor of the HIV-1 Pandemic Strains](https://science.sciencemag.org/content/288/5472/1789)
* [Island Biogeography Reveals the Deep History of SIV](https://science.sciencemag.org/content/329/5998/1487)
* [Molecular-clock methods for estimating evolutionary rates and timescales](https://onlinelibrary.wiley.com/doi/full/10.1111/mec.12953)
* [A synchronized global sweep of the internal genes of modern avian influenza virus](https://www.nature.com/articles/nature13016)

