# STAC: Spatial Temporal Asset Catalog

Author: [@jakobdanel](https://github.com/jakobdanel)

**Overview:**

1. What is STAC?
2. How it works
3. What are the benefits from STAC?
4. Examples
5. STAC tools

What is STAC?
----------------

- STAC stands for Spatial Temporal Asset Catalog
- The catalog describes a certain way to describe spatiotemporal data, so that every user of them can use them in the same way
- The problem we are facing is that data are provided in many ways, so most data are not available for users.
- STAC is Open-Source and fully community driven.
- The goal is that whenever new spatiotemporal data are published, they will be published as a STAC, so that there is no need to write new Code for a new API or new data set.

What are the benefits from STAC?
-----

The benefits of using the STAC specification can be seen from the three different positions of a data provider, a developer and a data user

**Data Provider:**

- The data provider have the advantage, that there is no need of overthinking the structure the data.
- The data provider can use the STAC specification to organize and structure the data and have the opportunity to safe a lot of time which is not be used for documentation

**Developer:**

- Developers does not need to read lots of documentation about an API or a data sat, if they have worked with an STAC product before.
- Also, there are many opportunities to refactor code, which was written for another STAC product, but can be used on others too.


**Data User:**

- Data Users often need to build different pipelines for each product they use, if all products use the STAC specification the building of these pipelines is much easier, because the data are structured in a similar way.

How it works
-----------

STAC is a composition of four semi-independent specifications which can be used standalone but works best as combination of all four.
The four specifications are:

**STAC Item:**

- The core atomic unit of a dataset repreenting a GeoJSON feature with additional information about datetime and links.
- A STAC item following the rules of a GeoJSON file and must contain some required fields
- See also the documentation on [GitHub](https://github.com/radiantearth/stac-spec/blob/master/item-spec/item-spec.md)  

**STAC Catalog:**

- STAC Catalogs are JSON files which contain links to STAC items
- A Catalog is to structure and organize all of the STAC items
- In the most cases the catalog is the entry point into the STAC dataset 
- The structure of the JSON is simply some fields with basic informations and a links field, which holds an Array of link objects.
- The specification documentation can also be find on [GitHub](https://github.com/radiantearth/stac-spec/blob/master/catalog-spec/catalog-spec.md)
- There are many of best practice advices which can be found [here](https://github.com/radiantearth/stac-spec/blob/master/best-practices.md).

**STAC Collections:**

- STAC Collections are an extension of the Catalog, which extends the Catalog with extra information, like provider, keywords or license of the STAC Items inside the catalog.
- Because it is an extension of a Catalog a STAC Collection also must be in JSON format.
- Every valid STAC Collection is a valid STAC Catalog.
- The documention of the specification you can find [here](https://github.com/radiantearth/stac-spec/blob/master/collection-spec/collection-spec.md).

**STAC API:**

- The STAC API provides a RESTful endpoint which makes searching for STAC Items posssible.
- STAC API using the standard of OpenAPI, fur further information see [here](https://www.openapis.org/).
- STAC API requires a landing page, which returning a STAC Catalog which can navigate down with the links to as many Items, Catalogs and Collections as you want.
- The API also require an endpoint `stac/search` which takes an JSON object with a bounding box and a timestamp. The API sshould return all catalogs with data inside the given time and space. 
- The documentation can be find on [GitHub](https://github.com/radiantearth/stac-api-spec).

Examples
--------

The following examples are datasets which provided as a STAC:

- [Landsat](https://landsat.gsfc.nasa.gov/)
- [CBERS](https://earth.esa.int/web/eoportal/satellite-missions/c-missions/cbers-3-4)
- [Sentinel 2](https://sentinel.esa.int/web/sentinel/missions/sentinel-2)
- [Google Earth Engine](https://earthengine.google.com/)
- ISERV
- EarthSearch is a STAC API for the Earth on AWS datasets that implement STAC.
- Radiant MLHub hosts datasets for training machine learning algorithms.
- Earth OnDemand provides a STAC API for a variety of public datasets.
- Sentinel Hub has a STAC implementation to describe their available datasets.


STAC Tools
----------

These are some tools, which help to deal with STAC data:

- **STAC Browser** is a Vue-based browser for STAC catalogs.
Cognition is a pluggable, STAC-compliant, proxy for searching geospatial assets.
- **STAC Validator** is a python utility to validate STAC json files against the STAC spec or against local STAC extensions.
- **STAC Node Validator** is a javascript utility to validate STAC JSON files against the STAC. It is currently the only validator working against 1.0.0-beta.1 (and only works against that version).
- **Serverless STAC Crawler** is a static STAC crawler that runs on Lambda and SQS integration.
- **Intake-STAC** provides tools for opening STAC as Intake catalogs. Intake and Intake-xarray enable loading STAC assets into Xarray objects.
- **PySTAC** is a library for working with STAC catalogs in Python.
- **STAC Server** (previously known as sat-api) is a STAC compliant web API for searching and serving metadata for geospatial data. It is written in Javascript and backed by Elasticsearch
- **Franklin** A STAC and OGC API Features compliant web service focused on ease-of-use for end-users.
- **pygeoapi** is a Python server implementation of the OGC API suite of standards, as well as support for serving geospatial data via STAC.
- **staccato** is a Java server implementation of STAC, backed by Elasticsearch. It includes support for transactions, statistics, auto-generated schemas, gRPC endpoints and Kafka ingestion.
- **sat-api-pg** is a STAC API implementation backed by PostGIS.
- **Rocket** is STAC client that enables browsing of any public STAC Catalog through a nice user interface.
- **EODAG** is a CLI tool and a Python framework for searching, aggregating results and downloading EO data through a unified API regardless of the data provider. It can be run as STAC client or STAC API proxy server for non-STAC providers.
- **Sat-utils** is a set of utilities for searching/processing satellite data, including:
- **Sat-search** is a Python 3 library and a command line tool for discovering and downloading publicly available satellite imagery.
- **Sat-stac** is a Python 3 library for creating and working with STAC catalogs.
- **Sat-stats** is a Python 3 library for calculating zonal statistics on i mages being stored remotely on S3.
- **Sat-fetch** is a Python 2/3 library and command line tool for fetching, warping, and clipping remote imagery datasets.


References:
-----------

- [STAC specification documention](https://stacspec.org/)
- [GitHub](https://github.com/radiantearth/stac-spec)
- [Browse through STAC data](https://www.stacindex.org/)