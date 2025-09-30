# Reproducing LMRv2.1 with PAGES2k and LinkedEarth Tools

By [Tanaya Gondhalekar](https://orcid.org/0009-0004-2440-3266), [Deborah Khider](https://orcid.org/0000-0001-7501-8430) & [Julien Emile-Geay](https://orcid.org/0000-0001-5920-4751). 

Climate field reconstruction is the task of estimating variations in one or more climate fields (e.g. surface temperature or precipitation) from a collection of paleoclimate observations (aka "proxies"). Several methods are available for doing so ; a relatively new and impactful one has been offline data assimilation, as implemented in the Last Millennium Reanalysis ([Hakim et al. (2016)](http://dx.doi.org/10.1002/2016JD024751)). The method was recently incorporated into the [cfr](https://fzhu2e.github.io/cfr/) Python package, published by [Zhu et al (2024)]( https://doi.org/10.5194/gmd-17-3409-2024) and validated on the pseudoPAGES2k dataset [Zhu et al (2023)](https://doi.org/10.1038/s41597-023-02489-1).  

Here we show how to reproduce the Last Millennium Reanalysis, version 2.1 [(Tardif et al, 2019)](https://doi.org/10.5194/cp-15-1251-2019), using tools from the [LinkedEarth](http://linked.earth) Python research ecosystem (and broader scientific Python stack). LMRv2.1 used the offline data assimilation method of [Hakim et al. (2016)](http://dx.doi.org/10.1002/2016JD024751) together with the [PAGES 2k](http://dx.doi.org/10.1038/sdata.2017.88) database, version 2.0.0. 

The reconstruction workflow is broken down into 3 major steps:
1. Data assembly: gathering, selection and cleaning
2. Data assimilation, which blends proxy observations with calibration data and the model prior
3. Validation and comparison to other relevant reconstructions

Here we offer two different ways to carry out Step 1, both of which result in a netCDF file that can be used in Step 2:

- [Step 1a](notebooks/data_assembly/C01_a_db_assembly_Tardif2019_pickle.ipynb) illustrates how to get a proxy database derived from the two pickle files (metadata and data) provided by [(Tardif et al, 2019)](https://doi.org/10.5194/cp-15-1251-2019).
- [Step 1b](/reproduce_lmr_pb/notebooks/data_assembly/C01_b_db_assembly_cfr_PAGES2k.html) illustrates how to get the proxy database directly from what is built into the `cfr` codebase. 

[Step 2](/reproduce_lmr_pb/notebooks/data_assimilation/C02_a_DA_with_class_based_seasonality.html) is common to all workflows, and only one instance is illustrated here (results obviously vary as a function of how Step 1 is implemented). [Step 3](/reproduce_lmr_pb/notebooks/validation/C03_a_validation.html) focuses here on emulating LMR v2.1, with validating both our results from Step 2, as well as comparing different proxy databases from Step 1 for forensics purposes. Newer reconstructions based on updates to the PAGES 2k database will be the subject of upcoming notebooks/publications.
