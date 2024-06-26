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

P-boxes are not probability distributions, but rather an envelope that contains multiple probability distributions. Below the 50th percentile, the reported values are the minima of the specified quantile across all encompassed distributions, and above the 50th percentile they are the maxima of the specified quantile. (The reported 50th percentile is the mean across all encompassed distributions.) See [Kopp, Oppenheimer, et al. (2023)](https://doi.org/10.7282/00000382) for more background on the conceptual framing of the AR6 sea level projections.

**Why is sea level change defined in some places over land?**

Physically, barystatic sea-level change (the change in the height of the geoid relative to the land surface) is defined over
the whole globe, including over land (where the geoid is lower than the land surface.)
Ocean dynamic sea-level chage is only defined over the ocean
(where water is present), but different global climate models with
different grids define this area differently. 
The AR6 projections are defined anywhere at least 2 of the
global climate models used identify as ocean. This means the area
for which the projections are defined is substantially
larger than what any single model would identify as ocean. Users should apply
their own land-ocean mask.

Caution is warranted with projections defined over semi-closed
and closed basins, where different global climate models
may differ on whether the basin is closed, semi-closed, open,
or land.

**How are the locations organized in the regional data files? Where are the gridded regional sea-level outputs?**

Both gridded outputs and tide-gauge outputs are included in the same regional output files. Locations are indexed by location ID. Location IDs below 2500 are PSMSL tide gauge IDs. Location IDs of 1000000000 or higher are on a 1 degree global grid. See [location_list.txt](location_list.txt) for the mapping of IDs to site names, latitude, and longitude. 

Note that the gridded sites are on a grid but are not stored in a gridded fashion in the netcdf files. Thus, if you want to use the gridded data in a context that expects gridded data files (eg GIS), you may need to first process the output files into a suitable format. 


