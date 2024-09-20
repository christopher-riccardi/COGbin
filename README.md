# `COGbin`, COG Enrichment With Statistical Significance  
### Description
The binomial test is used to determine if the number of upregulated or downregulated genes in a specific COG (Clusters of Orthologous Groups) category from an RNA-seq experiment is significantly greater than what would occur by random chance. It models the number of "successes" (such as upregulated genes) in a sequence of independent events (e.g., genes in a COG category), where each event has a fixed probability of success. This test helps assess whether the observed number of changes in gene expression within a particular category is statistically significant, rather than a result of random variability.

Mathematically, the binomial distribution is described by the probability mass function:

$$P(X = k) = \binom{n}{k} p^k (1-p)^{n-k}$$


Where:
- $k$ is the number of observed successes (e.g., the number of upregulated genes in a COG category),
- $n$ is the total number of trials (e.g., the total number of genes in the COG category),
- $p$ is the probability of success on each trial (e.g., the background probability of a gene being upregulated).

To perform the binomial test, the p-value is calculated as the probability of observing at least $k$ successes, given the binomial distribution:

$$\text{p-value} = P(X \geq k) = \sum_{x=k}^{n} \binom{n}{x} p^x (1-p)^{n-x}$$


This one-sided test compares the observed number of upregulated or downregulated genes in a COG category to the expected number, based on the background probability $p$.

The null hypothesis $H_0$ posits that the proportion of upregulated or downregulated genes in the category is equal to the background proportion, while the alternative hypothesis $H_1$ suggests that this proportion is significantly greater than expected by chance.

The p-value is then compared to a predetermined significance level ($\alpha = 0.01$). If the p-value is less than $\alpha$, the null hypothesis is rejected, indicating that the COG category is significantly enriched with upregulated or downregulated genes.  

### Implementation  
The Jupyter notebook contains the source code to perform this simple enrichment analysis, given three inputs:  
- An [eggNOG-mapper](http://eggnog-mapper.embl.de/) annotation file;
- A text file listing the _upregulated_ genes
- Another listing the _downregulated_ ones

 
### Testing  
A folder, `Data', is provided for a practical example. 
The output consists of optional plots during the execution of the script, as well as a table containing three columns:  

|Cat | Upreg | Downreg|  
|----|-------|--------| 
|L|\*|n.s.|  
|C|n.s.|\*|  
|P|n.s.|n.s.|
|(...)|||



