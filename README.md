# Bioinformatics Project: Statistical analyses of a dataset generated by Flow Cytometry and Mass Spectrometry
The data we will work with is based on advances in the fields of [Flow Cytometry](https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5939936/) for single cell analysis and [Mass Spectrometry](https://www.broadinstitute.org/technology-areas/what-mass-spectrometry) for measurement of cellular proteomic processes (the [phenotypical process endpoint](https://en.wikipedia.org/wiki/Central_dogma_of_molecular_biology) of cellular function and behavior). Based on these technologies, the multivariate landscape of proteomic activity can be measured for a single cell in any experiemental condition for any cell type at scale (e.g., cellular lines with a cancerous genotype at various stages of progression). By understanding typical cellular homeostatis of healthy and deliterious cells, and observing the phenotypical transformation of cellular proteomic homeostatsis over time in response to different experimental conditions, we may eventually be able to understand how to direct deleterious cellular states to transition into non-deleterious states. And with the ability of "data-driven identification and control of high-dimensional dynamical systems" we'll be able to fight cancer!
> The data observations simultaneously measure 22 so-called [AP-1 transcription factors](https://en.wikipedia.org/wiki/AP-1_transcription_factor) 
> and 4 phenotype proteins. So there are 26 total variables, 22 of which are thought of as "casues" and 4 of which are thought of as "outcomes". Each measurement is taken on a single cell; but, we can actually measure lots and lots of individual cells at once; and, we can do the measurements under different experiemental conditions, which lets us repeatedly observe these 22 variables over lots of different cells under lots of different treatment conditions (such as at different treatment conditions at different stages of cancer progression).
> - How can we measure the progression over time? Actually, we can't measure the same cells over and over. To make a measurement on a cell we have to destroy it... but, if we take a batch of cells (in a specific experimental condition) then we can split the cells up into groups and make the measurements on the different groups at different times; thus, we observe "the progression of the experimental condition over time".
>
> So the experiment based on condition $x$ and time $t$ produces the following tidy data table
>
>
>| | TF<sub>1</sub> | TF<sub>2</sub> | TF<sub>3</sub> |  $\vdots$| TF<sub>20</sub> | TF<sub>21</sub> | TF<sub>22</sub> | Y<sub>1</sub> | Y<sub>2</sub> | Y<sub>3</sub> | Y<sub>4</sub> | Drug | Dosage | Time | Rep |
>|-|-----|-----|-----|----------|------|------|------|----|----|----|----|------|--------|------|-----|
>|1|     |     |     |          |      |      |      |    |    |    |    |      |        |      |     |
>|2|     |     |     |          |      |      |      |    |    |    |    |      |        |      |     |
>|$\vdots$|  |   |   |          |      |      |      |    |    |    |    |      |        |      |     |
>|$n$|  |   |   |          |      |      |      |    |    |    |    |      |        |      |     |
>
> where the total number of observations $n = \sum_x \sum_t n_{xt}$ is the sum of all the samples $n_{xt}$ in each condition $x$ and time $t$ (which will be different since different batches of cells so we don't always have the same number of cells).
>
> - Note that the "number of individual cells" is the "number of observations" on which the (26) measurements have been made for each experimental condition $x$ which is defined by two drugs and their dosage, and each condition is repeated a few times for validation purposes.