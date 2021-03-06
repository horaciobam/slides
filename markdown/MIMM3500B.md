# Evolution:
## Understanding the origin of pathogens
### Art Poon
Department of Pathology & Laboratory Medicine; Microbiology & Immunology; Applied Mathematics
![](/img/UWO_Logo.svg)

---

# Microbes are everywhere
* Roughly half of the cells in your body are bacteria&ast;
* Probably about<sup>&dagger;</sup> as many viruses as cells (including bacteriophages)
* New human viruses are constantly being discovered: *e.g.,* [Torque teno virus](https://en.wikipedia.org/wiki/Transfusion_transmitted_virus), described in 1997, infects about 90% of all people

![](/img/xkcd-viruses.png)

<small>* Sender, Fuchs and Milo (2016) PLOS Biology 14: e1002533<br/>
<sup>&dagger;</sup> give or take a few orders of magnitude<br/>
Image by <a href="https://what-if.xkcd.com/80/">Randall Munroe</a>.
</small>

---

# Emerging infectious diseases

<iframe width="900" height="600" src="https://eidr.ecohealthalliance.org/event-map">
</iframe>

---

# Old pathogens

* [*Helicobacter pylori*](https://en.wikipedia.org/wiki/Helicobacter_pylori) in humans dates to roughly 100,000 years ago&ast;
* [Endogenous retroviruses](https://en.wikipedia.org/wiki/Endogenous_retrovirus) make up ~8% of human genome (exceeds protein-coding gene content!)
* Origin of the placenta: capture of retrovirus envelope gene to induce formation of giant syncytia<sup>&dagger;</sup>

<small>* Moodley *et al.* (2012) PLOS Pathog 8(5): e1002693<br/>
&dagger; Mi *et al.* (2000) Nature 403: 785-789.</small>

---

# Where do new pathogens come from?

* HIV-1: origin about 1920 in central Africa
* Zika virus: first isolated 1947 in east Africa
* Ebola virus: first isolated in 1976; [western Africa outbreak](https://en.wikipedia.org/wiki/Western_African_Ebola_virus_epidemic) in 2014 
* [Wuhan coronavirus](https://en.wikipedia.org/wiki/Wuhan_coronavirus): *It's happening right now*
<img width=350px src="https://ichef.bbci.co.uk/news/660/cpsprodpb/1320E/production/_110505387_059086447.jpg"/>
<small>Image credit: AFP</small>

---

# What drove the 2014 Ebola outbreak?

* Past outbreaks associated with unusually dry conditions following the rainy season*
* Close contact with potential host species (fruit bats), bushmeat; environmental disruption from development.
* Dramatic population growth, urbanization in affected regions.
* Sustained armed conflict from 1989 to 2004; massive numbers of displaced refugees<sup>&dagger;</sup>

<small>
\* Pinzon <i>et al.</i> (2004) Am J Trop Med Hyg 71: 664-674.<br/>
&dagger; Alexander *et al.* (2015) PLOS Neglect Trop Dis 9(6): e0003652
</small>

---

# Ebola virus outbreak in West Africa

<video data-autoplay data-src="/img/ebola.mp4" type="video/mp4"></video>
<small><small>Supplementary video, Dudas <i>et al.</i> 2017, Nature 544.</small></small>

---

# Reconstructing the past

* Addressing these questions in a data-driven, quantitative framework.
* We usually don't have samples from the start of an outbreak.
* Use evolutionary methods to extrapolate from current genetic samples back in time.

---

# Phylogenies

* A phylogeny is a tree-based model of how populations are related by their common ancestors.
* The *root* represents the earliest time point in the tree.

<iframe style="display:block; margin: auto;" width="800" height="500" src="/include/rooting.html">
</iframe>

---

# Oral polio vaccine hypothesis

<table>
<tr>

<td width="60%"><ul>
<li>Live-attenuated polio vaccine cultured in non-human primate cells</li>
<li>In 1992, <i>Rolling Stone</i> magazine published a story alleging that contaminated OPV was responsible for spreading HIV-1</li>
<li>Since thoroughly refuted by experimental and phylogenetic analysis.</li>
<li>Allegations disrupted vaccination campaigns, failure to eliminate polio</li>
</ul></td>

<td><img src="/img/OPV.png" width=250px/></td>

</tr>
</table>

<small>Excerpts from Worobey *et al.* (2004) Nature 428</small>

---

# Scaling trees in time

<img src="/img/timetree.png" width=600px/>
<hr>
<img src="/img/timetree-scaled.png" width=400px/>

---

<img src="/img/worobey.png" width=700px></img>

---

# Why has HIV-1 spread?

<table>
<tr>

<td width="50%"><ul>
<li>SIV-cpz (simian immunodeficiency virus, chimpanzee) has crossed over into human populations multiple times</li>
<li>Why did this particular strain originate the global pandemic?</li>
<li>Urbanization: "founding of colonial administrative and trading centres"</li>
</ul></td>

<td><img src="/img/faria.png"/></td>

</tr>
</table>

<small><small>Figure from Faria *et al.* The early spread and epidemic ignition of HIV-1 in human populations. Science 346: 56-51.</small></small>

---

# Reconstructing epidemic growth

* We can estimate how population size (number of infections) has changed over time.
* *e.g.,* An exponentially-growing epidemic results in a different tree:


<img src="/img/coalescent.png" width="500px"/>

---

# Hepatitis C virus in Egypt

* About 15% of adult population infected by HCV genotype 4
* Coalescent reconstructed found epidemic growth associated with massive public health campaign against snail fever.

<img src="/img/egypt.svg"/>

---

# Hepatitis C virus in North America

* HCV is highly prevalent in the "baby boomer" generation
* Why?  Unsafe sex practices, experimenting with drugs?
* Who will pay for new treatments that cost $10,000's of dollars?

<table><tr>
  <td><img src="/img/poster-chalkboard8.5x11.jpg" width="300px"/></td>
  <td><img src="/img/GenHep.png"/></td>
</tr></table>

---

<img src="/img/HCV-Joy.png" width="700px"/>

<small>Figure from Joy *et al.* Lancet Inf Dis 16(6): 698-702.</small>

---

# Socioeconomic causes

* Analysis suggests that most baby boomers became infected when they were infants, not as young adults
* Shifts the health care burden from individuals to public agencies.

<img src="/img/marginalized.png" width="650px"/>

<small>Figure from Edlin (2011) Nature 474: 518-519.</small>
