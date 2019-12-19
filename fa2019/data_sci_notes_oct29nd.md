To start with the second deliverable, you can import the code via :

include("knitr")
purl("insights.Rmd", output = "part1.r")
source("part1.r")

You can use this to produce the code from the first deliverable.

In the Rmd file you can add "run functions"

```{r}
```

Can be

```{r echo=FALSE, message=FALSE, error=FALSE, warning=FALSE, results='hide'}
```
