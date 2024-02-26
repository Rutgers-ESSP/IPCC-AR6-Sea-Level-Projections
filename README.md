# Guide to the IPCC AR6 Sea Level Projections

This repo provides guidance for accessing the IPCC Sixth Assessment Report sea level projections. See [Chapter 9 of the Working Group 1 contribution to the Sixth Assessment Report](https://www.ipcc.ch/report/ar6/wg1/chapter/chapter-9/) for more information.

Summary versions of regional projections can  be accessed through the [NASA/IPCC Sea Level Projections Tool](https://sealevel.nasa.gov/ipcc-ar6-sea-level-projection-tool). For most users, this site should provide the desired level of information. 

[LICENSE.md](LICENSE.md) describes licensing of the sea-level projections and required acknowledgements and citations.

Please [file an issue](https://github.com/Rutgers-ESSP/IPCC-AR6-Sea-Level-Projections/issues) on the repo if you have questions.

## Additional Resources

* [FAQ.md](FAQ.md) addresses frequently asked questions regarding the projections.

* [Kopp, Oppenheimer, et al. (2023)](https://doi.org/10.7282/00000382) provides more background on the conceptual framing of the AR6 sea level projections.

* [Kopp, Garner, et al. (2023)](https://doi.org/10.5194/gmd-16-7461-2023) provides details on the [Framework for Assessing Changes To Sea-level (FACTS)](https://github.com/radical-collaboration/facts), used to produce these projections. 

* [location_list.txt](location_list.txt) provides a list of site names, location IDs, site names, and associated latitude and longitudes used in the regional sea level projections.

## Data Sets available via Zenodo

* **[IPCC AR6 Sea Level Projections](https://doi.org/10.5281/zenodo.5914709):** This data set contains the full set of samples for the global projections, as well as summary relative sea level projections (both with and without the AR6 estimate of background sea level process rates). This is the dataset most users will need. See [FACTS_confidence_output_file_readme.pdf](https://github.com/Rutgers-ESSP/IPCC-AR6-Sea-Level-Projections/blob/main/FACTS_confidence_output_file_readme.pdf) for documentation.
* **[IPCC AR6 Sea Level Milestones](https://doi.org/10.5281/zenodo.7098141):** This data set contains files indicating the likelihood of when sea level milestones are crossed over time.
* **[IPCC AR6 Relative Sea Level Projection P-Boxes](https://doi.org/10.5281/zenodo.5914918):** This data set contains relative sea level projections for all of the p-boxes described in AR6 WG1 9.6.3, as well as a variant excluding the AR6 estimates of background sea level change.
* **[IPCC AR6 Relative Sea Level Projection Distributions](https://doi.org/10.5281/zenodo.5914931):** This data set contains relative sea level projection distributions for all the workflows described in AR6 WG1 9.6.3.2, as well as distributions for the components contributing to relative sea level change.
* **[IPCC AR6 Relative Sea Level Projections without Background Component](https://doi.org/10.5281/zenodo.5967268):** This data set contains relative sea level projections that exclude the background term (representing primarily land subsidence or uplift). It includes probability distributions for all the workflows described in AR6 WG1 9.6.3.2, as well as p-boxes derived from these distributions.
* **[Framework for Assessing Changes To Sea-level (FACTS) modules, scripts, and data for the IPCC AR6 sea level projections](https://doi.org/10.5281/zenodo.6419953):** This package contains the Frameworks for Assessing Changes To Sea-level (FACTS) modules, data, and scripts used to produce the sea level projections in the Intergovernmental Panel on Climate Change Sixth Assessment Report (AR6). See [the FACTS GitHub repo](https://github.com/radical-collaboration/facts) for the current version of FACTS.

## Access to full set of Monte Carlo samples

We are still working on a permanent hosting solution for the ~10 TB of local relative sea level samples. As a temporary solution, the simulation totals for each workflow and scenario are available as partitioned zarr arrays on google cloud. Rates of change associated with the provided levels have been omitted from the below archive while we look for a hosting solution.

The full set of files available via google cloud are listed in the JSON file [`google_zarr_stores.json`](https://raw.githubusercontent.com/Rutgers-ESSP/IPCC-AR6-Sea-Level-Projections/main/google_zarr_stores.json) in this repository.

### Global Monte Carlo samples

The full set of Monte Carlo samples for global mean sea level projections, as well as the components driving global mean sea level change, are available via [Zenodo](https://doi.org/10.5281/zenodo.5914709).

### Gauge-based & gridded workflow Monte Carlo sample totals

The data have been separated into gridded and tide-gauge based datasets. Because the simulations are generated based on sea level observations at tide gauge locations, users are encouraged to use the tide-gauge-based data for areas with good coverage of tide gauge locations. For areas with sparser coverage, or for applications requiring gridded or comprehensive global coverage, the gridded data is more suitable. Note that the gridded datasets are 40-50x larger than the tidal datasets, but have been partitioned spatially, enabling quick and bandwidth-efficient access to subsets of the globe.

The tide-gauge and gridded datasets simulation totals have the following Google Cloud Storage URI patterns:
* tide gauges (*free to download*: 38.42 GB):  [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows)
* gridded (*free to download*: 1.65 TB):  [`gs://ar6-lsl-simulations-public-standard/gridded/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/gridded/full_sample_workflows)

They can also be acceessed via HTTPs through the public API endpoints:
* tide gauges: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`
* gridded: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/gridded/full_sample_workflows/{workflow_id}/{experiment_id}/total-workflow.zarr`

For example, the SSP1-1.9 experiment using workflow 1-E may be found at the following url:

```
https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows/wf_1e/ssp119/total-workflow.zarr
``` 

This may be read using [zarr](https://zarr.dev/) using the zarr v1 specification.

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

Please note that the simulation datasets are significantly larger than the corresponding distribution and confidence files. The tide gauge data is 38 GB and the gridded data is 1.65 TB. When downloading the data over the public internet, *we ask that you please limit your download to the portions of the globe, time slices, workflows, and experiments which you will use prior to download*, and that you download a copy once and then access a local copy rather than downloading repeatedly from our servers. The data are in the `us-west1` (Oregon) data center. Transfers within the Google Cloud Storage platform are significantly cheaper, and within the us-west1 region much more so.

### Gauge-based & gridded workflow Monte Carlo samples (excluding vertical land motion)

The tide-gauge and gridded datasets simulation totals have the following Google Cloud Storage URI patterns:
* tide gauges (*free to download*: 35.27 GiB): [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm)
* gridded (***requester pays***: 1.81 TB): [`gs://ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_workflows_novlm)

The tide gauge data can also be acceessed via HTTPs through the public API endpoints:
* tide gauges (*free to download*): `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_workflows_novlm/{workflow_id}/{experiment_id}/total-workflow.zarr`

Note that the gridded workflow samples (excluding vertical land motion) are in a "Requester Pays" google cloud bucket. That means that, while we are looking for a permanent hosting solution, anyone accessing the No-VLM gridded workflow samples will be charged for the data retrieval and egress fees. These can be expensive. Depending on your location, downloading the full 1.81 TB of data can cost upwards of $75-$400 (at the time of writing). Please note that the authors are not charging for access to the data - any costs incurred are simply the costs assessed by Google to retrieve the data. In order to access the data, you will need to authenticate with an active Google Cloud account with an attached payment method. The data are in the `us-west1` (Oregon) data center. Transfers within the Google Cloud Storage platform are significantly cheaper, and within the us-west1 region much more so. See https://cloud.google.com/storage/pricing#network-pricing.

### Gauge-based & gridded workflow Monte Carlo sample components

The above workflow totals are calculated by adding individual components which together form the drivers of the local sea level simulations. Each of the workflow totals above have attributes which reference the workflow components from whihc they are derived (the components reference the `.nc` files from the original workflow, but the filenames may be parsed to find the correct workflow components in this dataset).

* tide gauges (*free to download*: 63.67 GB): [`gs://ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components/{component}.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components)
* gridded (***requester pays***: 2.15 TB): [`gs://ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_components/{component}.zarr`](https://console.cloud.google.com/storage/browser/ar6-lsl-simulations-requesterpays-standard/gridded/full_sample_components)

The tide gauge data can also be acceessed via HTTPs through the public API endpoints:
* tide gauges: `https://storage.googleapis.com/ar6-lsl-simulations-public-standard/tide-gauges/full_sample_components/{component}.zarr`

Note that the gridded workflow components are in a "Requester Pays" google cloud bucket. That means that, while we are looking for a permanent hosting solution, anyone accessing the gridded workflow components data will be charged for the data retrieval and egress fees. These can be expensive. Depending on your location, downloading 2.15 TB of data can cost upwards of $90-$450 (at the time of writing). Please note that the authors are not charging for access to the data - any costs incurred are simply the costs assessed by Google to retrieve the data. In order to access the data, you will need to authenticate with an active Google Cloud account with an attached payment method. The data are in the `us-west1` (Oregon) data center. Transfers within the Google Cloud Storage platform are significantly cheaper, and within the us-west1 region much more so. See https://cloud.google.com/storage/pricing#network-pricing.
