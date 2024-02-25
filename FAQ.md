# Frequently asked questions

**What are the different workflows?**

The seven workflows differ in their treatment of cryospheric components.

| Workflow | Cryospheric components |
|----------|------------------------|
| 1e | Emulated ISMIP6 projections for ice sheets and emulated GlacierMIP projections for glaciers. (Should not be used for rates) |
| 1f | Parametric fits to ISMIP6 projections for Greenland, IPCC AR5 parametric model for Antarctica, recalibrated IPCC AR5 parametric glacier model for glaciers. }
| 2e | Emulated ISMIP6 projections for Greenland, LARMIP2 emulator for Antarctica, emulated GlacierMIP projections for glaciers. (Should not be used for rates) |
| 2f | Parametric fits to ISMIP6 projections for Greenland, LARMIP2 emulator for Antarctica, recalibrated IPCC AR5 parametric glacier model for glaciers. |
| 3e | Emulated ISMIP6 projections for Greenland, DeConto et al. (2021) for Antarctica, emulated GlacierMIP projections for glaciers. (Should not be used for rates) |
| 3f | Parametric fits to ISMIP6 projections for Greenland, DeConto et al. (2021) for Antarctica, recalibrated IPCC AR5 parametric glacier model for glaciers. |
| 4 | Bamber et al. (2019) for ice sheets, recalibrated IPCC AR5 parametric glacier model for glaciers |

Note that the ISMIP6 and GlacierMIP emulator does not capture correlations between different time periods, and thus should not be used for rates.

See [Kopp, Garner, et al. (2023)](https://doi.org/10.5194/gmd-16-7461-2023) for more information.

**What are the different p-boxes?**

| p-box | Description |
|-------|-------------|
| 1e | P-box of workflows 1e and 2e. Considers only *medium confidence* ice sheet processes. (Should not be used for rates.) |
| 1f | P-box of workflows 1f and 2f. Considers only *medium confidence* ice sheet processes. |
| 2e | P-box of workflows 1e, 2e, 3e and 4. Incorporates *low confidence* ice sheet processes.  (Should not be used for rates.)  |
| 2f | P-box of workflows 1f, 2f, 3f, and 4. Incorporates *low confidence* ice sheet processes. |

The canonical IPCC results use p-boxes 1e and 2e for projections of levels through 2100, and p-boxes 1f and 2f for post-2100 projections and for projections of rates.

**Why do some areas exhibit discontinuities beyond 2100?**

The preferred p-boxes used for level projections post 2100 are different than those used until 2100, as ISMIP6 and GlacierMIP results are not available after 2100. In addition, there is a reduction in the availability of GCMs used to inform dynamic sea level projections after 2100. These discontinuities can be significant between 2100 and 2110, and thus it may be desirable to skip the 2110 (and in some cases 2120) time steps.

**Why do the p-box and confidence files exhibit discontinuities at the 50th percentile?**

P-boxes are not probability distributions, but rather an envelope that contains multiple probability distributions. Below the 50th percentile, the reported values are the minima of the specified quantile across all encompassed distributions, and above the 50th percentile they are the maxima of the specified quantile. (The reported 50th percentile is the mean across all encompassed distributions.) See [Kopp, Oppenheimer, et al. (2023)](https://doi.org/10.1002/essoar.10511663.1) for more background on the conceptual framing of the AR6 sea level projections.
