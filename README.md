# Guide to the IPCC AR6 Sea Level Projections

This repo provides guidance for accessing the IPCC Sixth Assessment Report sea level projections. See [Chapter 9 of the Working Group 1 contribution to the Sixth Assessment Report](https://www.ipcc.ch/report/ar6/wg1/downloads/report/IPCC_AR6_WGI_Chapter09.pdf) for more information.

## Required Acknowledgements and Citations

In order to document the impact of these sea-level rise projections, users of the projections are obligated to cite chapter 9 of Working Group 1 contribution to the the IPCC Sixth Assessment Report, the Framework for Assessment of Changes To Sea-level (FACTS) model description paper, and the version of the data set used:

> Fox-Kemper, B., H.T. Hewitt, C. Xiao, G. Aðalgeirsdóttir, S.S. Drijfhout, T.L. Edwards, N.R. Golledge, M. Hemer, R.E. Kopp, G. Krinner, A. Mix, D. Notz, S. Nowicki, I.S. Nurhati, L. Ruiz, J.-B. Sallée, A.B.A. Slangen, and Y. Yu, 2021: Ocean, Cryosphere and Sea Level Change. In Climate Change 2021: The Physical Science Basis. Contribution of Working Group I to the Sixth Assessment Report of the Intergovernmental Panel on Climate Change \[Masson-Delmotte, V., P. Zhai, A. Pirani, S.L. Connors, C. Péan, S. Berger, N. Caud, Y. Chen, L. Goldfarb, M.I. Gomis, M. Huang, K. Leitzell, E. Lonnoy, J.B.R. Matthews, T.K. Maycock, T. Waterfield, O. Yelekçi, R. Yu, and B. Zhou (eds.)\]. Cambridge University Press, Cambridge, United Kingdom and New York, NY, USA, pp. 1211–1362, [doi:10.1017/9781009157896.011](https://doi.org/10.1017/9781009157896.011).
     
> Garner, G. G., R. E. Kopp, T. Hermans, A. B. A. Slangen, G. Koubbe, M. Turilli, S. Jha, T. L. Edwards, A. Levermann, S. Nowikci, M. D. Palmer, C. Smith, in prep. Framework for Assessing Changes To Sea-level (FACTS). Geoscientific Model Development.
     
> Garner, G. G., T. Hermans, R. E. Kopp, A. B. A. Slangen, T. L. Edwards, A. Levermann, S. Nowikci, M. D. Palmer, C. Smith, B. Fox-Kemper, H. T. Hewitt, C. Xiao, G. Aðalgeirsdóttir, S. S. Drijfhout, T. L. Edwards, N. R. Golledge, M. Hemer, G. Krinner, A. Mix, D. Notz, S. Nowicki, I. S. Nurhati, L. Ruiz, J-B. Sallée, Y. Yu, L. Hua, T. Palmer, B. Pearson, 2021. IPCC AR6 Sea Level Projections. Version 20210809. Dataset accessed [YYYY-MM-DD] at https://doi.org/10.5281/zenodo.5914709.

Please also include in the acknowledgements of works citing these projections:

> We thank the projection authors for developing and making the sea-level rise projections available, multiple funding agencies for supporting the development of the projections, and the NASA Sea Level Change Team for developing and hosting the IPCC AR6 Sea Level Projection Tool.

## IPCC AR6 Licensing

The IPCC AR6 Sea-Level Rise Projections are licensed by the authors under a [Creative Commons Attribution 4.0 International License](https://creativecommons.org/licenses/by/4.0/). The data producers and data providers make no warranty, either express or implied, including, but not limited to, warranties of merchantability and fitness for a particular purpose. All liabilities arising from the supply of the information (including any liability arising in negligence) are excluded to the fullest extent permitted by law.

## Data Repositories and Tools

### Available via Zenodo

* **[IPCC AR6 Sea Level Projections](https://doi.org/10.5281/zenodo.5914709):** This data set contains the full set of samples for the global projections, as well as summary relative sea level projections (both with and without the AR6 estimate of background sea level process rates). This is the dataset most users will need.
* **[IPCC AR6 Relative Sea Level Projection P-Boxes](https://doi.org/10.5281/zenodo.5914918):** This data set contains relative sea level projections for all of the p-boxes described in AR6 WG1 9.6.3, as well as a variant excluding the AR6 estimates of background sea level change.
* **[IPCC AR6 Relative Sea Level Projection Distributions](https://doi.org/10.5281/zenodo.5914931):** This data set contains relative sea level projection distributions for all the workflows described in AR6 WG1 9.6.3.2, as well as distributions for the components contributing to relative sea level change.
* **[IPCC AR6 Relative Sea Level Projections without Background Component](https://doi.org/10.5281/zenodo.5967268):** This data set contains relative sea level projections that exclude the background term (representing primarily land subsidence or uplift). It includes probability distributions for all the workflows described in AR6 WG1 9.6.3.2, as well as p-boxes derived from these distributions.
* **[Framework for Assessing Changes To Sea-level (FACTS) modules, scripts, and data for the IPCC AR6 sea level projections](https://doi.org/10.5281/zenodo.6419953):** This package contains the Frameworks for Assessing Changes To Sea-level (FACTS) modules, data, and scripts used to produce the sea level projections in the Intergovernmental Panel on Climate Change Sixth Assessment Report (AR6). See [the FACTS GitHub repo](https://github.com/radical-collaboration/facts) for the development version of FACTS.

### Other tools

Summary versions of regional projections can also be accessed through the [NASA/IPCC Sea Level Projections Tool](https://sealevel.nasa.gov/ipcc-ar6-sea-level-projection-tool).

### Access to full set of Monte Carlo samples

**Global Monte Carlo samples**

The full set of Monte Carlo samples for global mean sea level projections, as well as the components driving global mean sea level change, are available via [Zenodo](https://doi.org/10.5281/zenodo.5914709).

**Gauge-based & gridded workflow Monte Carlo sample totals**

We are still working on a permanent hosting solution for the ~5 TB of relative sea level samples. As a temporary solution, the simulation totals for each workflow and scenario are available as partitioned zarr arrays on google cloud. The data have been separated into gridded and tide-gauge based datasets. Because the simulations are generated based on sea level observations at tide gauge locations, users are encouraged to use the tide-gauge-based data for areas with good coverage of tide gauge locations. For areas with sparser coverage, or for applications requiring gridded or comprehensive global coverage, the gridded data is more suitable. Note that the gridded datasets are 40-50x larger than the tidal datasets, but have been partitioned spatially, enabling quick access to subsets of the globe.

The tide-gauge and gridded datasets simulation totals have the following Google Cloud Storage URI patterns:
* tide gauges: [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows)
* gridded: [`gs://ar6-lsl-simulations-public-standard/gridded/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/gridded/full_sample_workflows)

They can also be acceessed via HTTPs through the public API endpoints:
* tide gauges: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`
* gridded: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/gridded/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`

For example, the SSP1-1.9 experiment using workflow 1-E may be found at the following url:

```
https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/wf_1e/ssp119/total-workflow.zarr
``` 

This may be read using zarr using the zarr v1 specification.

For example, in python:

```python
In [1]: import xarray as xr

In [2]: ds_url = (
   ...:     'https://storage.googleapis.com/ar6-lsl-simulations-public-standard/'
   ...:     'tide-gauges/full_sample_workflows/wf_1e/ssp119/total-workflow.zarr'
   ...: )

In [3]: ds = xr.open_dataset(ds_url, engine='zarr', chunks='auto')

In [4]: ds
Out[4]:
<xarray.Dataset>
Dimensions:           (locations: 1012, samples: 20000, years: 9)
Coordinates:
    lat               (locations) float64 dask.array<chunksize=(1012,), meta=np.ndarray>
  * locations         (locations) int64 1 2 3 5 7 8 ... 2326 2329 2330 2356 2358
    lon               (locations) float64 dask.array<chunksize=(1012,), meta=np.ndarray>
  * samples           (samples) int64 0 1 2 3 4 ... 19996 19997 19998 19999
  * years             (years) int64 2020 2030 2040 2050 2060 2070 2080 2090 2100
Data variables:
    sea_level_change  (samples, years, locations) float32 dask.array<chunksize=(5000, 5, 1012), meta=np.ndarray>
Attributes:
    citation:              In order to document the impact of these sea-level...
    description:           Total sea-level change for workflow
    extra_info_url:        https://github.com/Rutgers-ESSP/IPCC-AR6-Sea-Level...
    history:               Created Fri Jun 18 14:00:48 2021
    license:               The IPCC AR6 Sea-Level Rise Projections are licens...
    source:                FACTS: Post-processed total among available contri...
    zarr_processing_date:  Mon Jun  6 05:25:45 2022 (UTC)
```

The data may also be copied in bulk using the command-line utility [`gsutil`](https://cloud.google.com/storage/docs/gsutil_install). For example, to copy the entire set of workflow 1-E tide-gauge experiments to your downloads directory, you could run the command (assuming a \*nix shell):

```bash
gsutil cp gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/wf_1e ~/Downloads/
```

Please note that the simulation datasets are significantly larger than the corresponding distribution and confidence files. The tide gauge data is 35GB and the gridded data is 1.5 TB. When downloading the data over the public internet, *we ask that you please limit your download to the portions of the globe, time slices, workflows, and experiments which you will use prior to download*, and that you download a copy once and then access a local copy rather than downloading repeatedly from our servers.

**Gauge-based & gridded workflow Monte Carlo samples (excluding vertical land motion)**

The tide-gauge and gridded datasets simulation totals have the following Google Cloud Storage URI patterns:
* tide gauges (*free to download*): [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm)
* gridded (***requester pays***): [`gs://ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_workflows_novlm)

The tide gauge data can also be acceessed via HTTPs through the public API endpoints:
* tide gauges (*free to download*): `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`

Note that the gridded workflow samples (excluding vertical land motion) are in a "Requester Pays" google cloud bucket. That means that, while we are looking for a permanent hosting solution, anyone accessing the No-VLM gridded workflow samples will be charged for the data retrieval and egress fees. These can be expensive. Depending on your location, downloading the full 5 TB of data can cost upwards of $200-$1000 (at the time of writing). Please note that the authors are not charging for access to the data - any costs incurred are simply the costs assessed by Google to retrieve the data. In order to access the data, you will need to authenticate with an active Google Cloud account with an attached payment method. See https://cloud.google.com/storage/pricing#network-pricing.

**Gauge-based & gridded workflow Monte Carlo sample components**

The above workflow totals are calculated by adding individual components which together form the drivers of the local sea level simulations. These simulations, together make up a 

* tide gauges (*free to download*): [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components)
* gridded (***requester pays***): [`gs://ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_components/{workflow_id}/{experiment_id}/{component}.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_components)

The tide gauge data can also be acceessed via HTTPs through the public API endpoints:
* tide gauges: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components/{workflow_id}/{experiment_id}/total-workflow.zarr`

Note that the gridded workflow components are in a "Requester Pays" google cloud bucket. That means that, while we are looking for a permanent hosting solution, anyone accessing the gridded workflow components data will be charged for the data retrieval and egress fees. These can be expensive. Depending on your location, downloading 5 TB of data can cost upwards of $200-$1000 (at the time of writing). Please note that the authors are not charging for access to the data - any costs incurred are simply the costs assessed by Google to retrieve the data. In order to access the data, you will need to authenticate with an active Google Cloud account with an attached payment method. See https://cloud.google.com/storage/pricing#network-pricing.


## Acknowledgements

The development of the sea-level rise projections was supported by multiple funders, including the U.S. National Aeronautics and Space Administration (grants 80NSSC17K0698, 80NSSC20K1724 and 80NSSC21K0322 and JPL task 105393.509496.02.08.13.31), the U.S. National Science Foundation (grant ICER-1663807), the U.K. Natural Environment Research Council (grant NE/T009381/1), NIOZ Royal Netherlands Institute for Sea Research, PROTECT (which has received funding from the European Union's Horizon 2020 research and innovation programme under grant agreement no. 869304), and UK Natural Environment Research Council grant NE/T007443/1. We acknowledge the World Climate Research Programme, which, through its Working Group on Coupled Modelling, coordinated and promoted CMIP6. We thank the climate modeling groups for producing and making available their model output, the Earth System Grid Federation (ESGF) for archiving the data and providing access, and the multiple funding agencies who support CMIP6 and ESGF. 
