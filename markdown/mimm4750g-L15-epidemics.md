# MIMM4750G
## Reconstructing past epidemics

![](https://imgs.xkcd.com/comics/outbreak.png)

---

# Limitations of the Coalescent

* Sample size should be much smaller than the entire population
  * Some local outbreaks may be nearly completely sampled.
* Difficult to handle selection.
  * [Coalescent models with selection](https://www.genetics.org/content/145/2/519.short) are theoretically possible but almost never used in practice.
* Not originally designed for epidemics.
  * Changes in population size are difficult to interpret (effective number of infections).  However, this is an [active area of work](https://www.genetics.org/content/183/4/1421.short).

---

# Birth-death models

* Instead of tracing branches of the tree back in time, imaging growing a tree forward in time from the root.
  * A branch has a constant **birth** rate $(\lambda)$ of splitting into two  branches.
  * A branch has a constant **death** rate $(\delta)$ of terminating (going extinct).
* If $\lambda>\delta$, the number of tips should increase exponentially over time.
* A model with no death is a "pure birth" model.

---

# Birth-death models

* A birth-death model describes a tree.
<img src="/img/birth-death.png" width="350px"/>
* The transmission of a pathogen to a new host is a *lineage birth*.
* The recovery or death of an infected individual is a *lineage death*.
* A more natural model for epidemics.

---

# Limitations of birth-death models

* Birth and death rates are constant over time - lineages do not age.
* We cannot use sampling times as data.  Sampling means the termination of a lineage, so it is a death rate.
  * This means that sampling is a process with a constant rate.
* Calculating the probability of a tree generally involves solving a system of differential equations, which may be difficult.

---

# Coalescent and birth-death

* Both are models of how trees are shaped by population-level processes.

| Coalescent | Birth-death |
|------------|-------------|
| Reverse time | Forward time |
| Assumes sample size $n<<N$ | Robust to large $n$ |
| Sampling times are data | Sampling must be modeled |
| No selection | Can handle selection naturally |

* Both models can be used as **tree priors** - if you have enough data, it shouldn't really matter which one you use.

---

# Modeling an epidemic

* Suppose a single infected individual enters a population.
  * Let $I$ be the number of **infected** people.
  * Let $S$ be the number of uninfected people **susceptible** to infection.
  * Let $\beta$ be the **transmission rate**, where a susceptible person who comes in contact with an infected person becomes infected.
* The rate of new infections is:

$$\beta S I = \beta (N-I)I$$

---

# SI dynamics
* This model is known as the susceptible-infected (SI) model.
* $I$ increases at the fastest rate when $S=I$, *i.e.*, $I=N/2$.
![](/img/SI-animate.gif)

---

# Compartmental models

* The SI model belongs to a class of epidemic models known as [compartmental models](https://en.wikipedia.org/wiki/Compartmental_models_in_epidemiology).
* A compartment is a sub-population with distinct numbers and rate parameters.
* These models are generally represented by systems of differential equations.
* For example, the SI model can be written as:

$$\frac{dS}{dt}=-\beta S I, \; \frac{dI}{dt} = \beta S I$$

---

# Assumptions

1. The population is "well mixed".  Any one person is equally likely to come into contact with any other person.

2. The transmission rate $\beta$ is the same for everybody, *forever*.

3. The size of the total population does not change.

---

# Compartmental models

* It's easier to visualize these models as flow chrarts:

<img src="/img/compartmental-models.png" width="600px"/>

* An unlimited number of combinations!

---

# Basic reproduction number

* "R naught" is the expected number of secondary cases from the index case (all other individuals are susceptible).
* If $R_0<1$, then we expect the infection to die out.  If $R_0>1$, then we expect it to spread.
* For the SIR model (with death rate $\gamma$),

  $$R_0 = \frac{\beta N}{\gamma}$$

* Increases with transmission rate ($\beta$), and declines with death rate $\gamma$.

---

# Fitting compartmental models to trees

* Either birth-death or coalescent models can be used to represent a compartmental model.
* Birth-death models were adapted to epidemics by linking rates to population sizes ([K&uuml;hnert *et al.* 2014](https://royalsocietypublishing.org/doi/full/10.1098/rsif.2013.1106)).
* Coalescent models were adapted by [Volz *et al.* 2009](https://www.genetics.org/content/183/4/1421.short).
* Both approaches are implemented in the same software!

---

# Bringing it all together

* Trees ([lecture 9](http://slides.filogeneti.ca/html/mimm4750g-L9.html#/)); substitution models ([lecture 10](http://slides.filogeneti.ca/html/mimm4750g-L10.html#/)); molecular clocks ([lecture 12](http://slides.filogeneti.ca/html/mimm4750g-L12.html#/)); Bayesian inference ([lecture 13](http://slides.filogeneti.ca/html/mimm4750g-L13.html#/))

![](/img/duPlessis.png)

<small>Image credit: Louis duPlessis, [Taming the BEAST lectures](https://github.com/Taming-the-BEAST/Taming-the-BEAST-2019-Eh-Lectures)</small>

---

# BEAST

<img src="https://beast.community/images/beast-banner.png" width="600px"/>

* Primarily developed by Alexei Drummond and Andrew Rambaut in the <a href="https://en.wikipedia.org/wiki/Java_(programming_language)">Java programming language</a>.
* BEAST has become one of the most influential software packages in infectious disease research in the last decade.
* Over 10,000 citations, including over 40 Nature papers and over 20 Science papers since 2007.

---

# BEAST

* Can use the coalescent or birth-death model as a prior over trees.
* Rearranges and rescales parts of the tree to perform a *random walk* over the posterior distribution of trees.
* At the same time, samples parameters of a model of evolution that is needed to reconstruct the tree from sequences.
* Outputs trace logs of posterior, likelihood, prior and model parameters &mdash; trees are written to a separate log.

---

# XML

* A BEAST analysis is set up in an XML file
* eXtensible Markup Language

```xml
<?xml version="1.0"?>
<beast>
	<alignment>
		<sequence dataType="nucleotide">
			<taxon id="Brazi82"/>
			ATGATCGTAGTATCGTAGCTCGGTTTTTACGATCGGAC
		</sequence>
		<sequence dataType="nucleotide">
			<taxon id="ElSal83"/>
			ATGATCGTAGTATCGTAGCTCGGTTTTTACGATCGGAC
		</sequence>
	</alignment>
</beast>
```

---

# Generating XML

* Most users set up an analysis with the GUI program BEAUti (*Bayesian Evolutionary Analysis Utility*) rather than directly edit XML.

<img src="/img/beauti.png" width="600px"/>

---

# Running BEAST

* BEAST now requires [BEAGLE](https://github.com/beagle-dev/beagle-lib) to run.
* "Broad-platform Evolutionary Analysis General Likelihood Evaluator".
* BEAGLE is a [library](https://en.wikipedia.org/wiki/Library_(computing)) &mdash; a collection of functions that can be called from other programs.
* Using BEAGLE can make BEAST about 5-10 times faster!
* (It used to be possible to run BEAST *without* BEAGLE...)

---

# Running BEAST

* BEAST can take a very long time!
* Since we are trying to explore an enormous model space, we usually run chains of $10^8$ steps or more!
* BEAST tries to estimate how long it takes to perform 1 million steps.

```
# BEAST v1.10.5 Prerelease #23570d1
# Generated Sun Mar 03 13:42:57 EST 2019 [seed=1551638575176]
# benchmark2.xml
state	Posterior   	Prior       	Likelihood  	rootHeight  	clock.rate  	alpha       
0	-568698.9433	-16.9645    	-568681.9788	0.20000     	1.00000     	0.50000     	-
10000	-215056.1166	59.1339     	-215115.2505	0.26252     	1.00000     	0.32615     	-
20000	-202604.8926	72.8223     	-202677.7148	0.23844     	1.00000     	0.30842     	0.11 hours/million states
30000	-196143.5414	72.3079     	-196215.8493	0.27209     	1.00000     	0.26344     	0.11 hours/million states
40000	-193720.6293	59.7853     	-193780.4145	0.39626     	1.00000     	0.26003     	0.11 hours/million states
50000	-193206.4970	56.6362     	-193263.1333	0.45645     	1.00000     	0.24143     	0.11 hours/million states
```

---

# Birth-death/coalescent analysis of COVID-19

<img src="/img/stadler-covid19.png" width="650px"/>

<small>Image source: Scire, Vaughan and Stadler (2020) [virological.org preprint](http://virological.org/uploads/short-url/uX4ercsFF78N0RqkQBSH79GJASq.pdf) </small>
