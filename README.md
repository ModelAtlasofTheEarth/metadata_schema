# M@TE Metadata Model

## Project Description

Model Atlas of the Earth (M@TE) is a project supported by AuScope. It supports the FAIR data principles in relation to computation models of the Earth, with a focus on tectonics/geodynamics, hydrogeology and surface processes. M@TE provides and connects digital infrastructure, to support the entire model life-cycle, resulting in a permanent collection of FAIR computation models of Earth processes. The model submission process (for details, see github.com/ModelAtlasofTheEarth/model_submission) generates a comprehensive metadata  document, utilising the principles of the RO-Crate project. To ensure long-term storage of large computational model outputs, M@TE models are cloned to servers on the National Computational Infrastructure (more information at geonetwork.nci.org.au). This procedure assigns a citable  DOI to each M@TE model. Additionally,  models are featured on the project website,  https://mate.science. See website for further information. 

## Summary of metadata model

In the M@TE project, the metadata format that describes a model is based on the [RO-Crate project](https://www.researchobject.org/ro-crate/). The metadata file is found in the root directory of the model (`/ro-crate-metadata.jsonld`). 

In RO-Crate, a research-object (here a computational model) is encapsulated through a collection (crate) of several `schema.org` types or entities. Together these form a meaningful unit for the purposes of communication, citation, distribution, preservation, etc.

The file `mate_ro_crate/ro-crate-metadata.jsonld` is the basic template, which is filled out in the model submission stage. Users can extend or modify this file.

## RO-Crate: background 

In RO-Crate a research-object is encapsulated through a collection (crate) of several `schema.org` types or entities.  Schema.org is a collaborative, community activity with a mission to create, maintain, and promote schemas for structured data on the Internet, on web pages, in email messages, and beyond.

Some of these entities refer to directories and file payloads that are stored in the M@TE model (e.g. on Github/NCI). These are generally referred to as `data entities`. Other entities exist elsewhere, for instance people, research groups, and data is already available on persistent web repositories, such as Zenodo. These are referred to as `contextual entities` 

RO-crates use the JSON-LD format. JSON-LD is a lightweight Linked Data format. In the JSON-LD format, the crate is represented by the @graph array:

```
"@graph": [

  {
    thing1
  },
  {
    thing2
  }]]
```

The most general layer of information is a ro-crate is the Root Data Entity `@id=.\`. This Root Data Entity has the schema.org _Type_ `DataSet`, which is a subset of `CreativeWork` Type (https://schema.org/CreativeWork)

Where files and folders are represented as *Data Entities* in the RO-Crate JSON-LD, these MUST be linked to, either directly or indirectly, from the [Root Data Entity](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html) using the [hasPart](http://schema.org/hasPart) property.

Some contextual entities can also be considered data entities - for instance the [license](https://www.researchobject.org/ro-crate/1.1/contextual-entities.html#licensing-access-control-and-copyright) property refers to a [CreativeWork](http://schema.org/CreativeWork) that can reasonably be downloaded, however a license document is not  usually considered as part of research outputs and would therefore  typically not be included in [hasPart](http://schema.org/hasPart) on the [root data entity](https://www.researchobject.org/ro-crate/1.1/root-data-entity.html).

### RO-Crate: adapting for M@TE

RO-Crates are well suited to the task of describing computational models (a research object). Key attributes of the RO-Crate format/specification which we find useful:

* handle the diverse set of entitites that are involved in the creation of model (software pojects, specific code, computers, output data, publication, funders) 
* clear conceptual separation between data and contextual entities
* based on schema.org/json-ld
* facilitate reuse of existing metadata (e.g. ORCID data, using json-ld requests)
* easy to programatically verify and modify
* can be extended to provide descriptions of workflow

In terms of M@TE project, an important requirement is that the RO-Crate can fulfil metadata requirements (ISO 19115) used in the NCI GeoNetwork catalogue (https://geonetwork.nci.org.au/), where M@TE model are stored. Many of the field requirements in ISO 19115 are easily mapped to  `DataSet` (or by inheritance `CreativeWork`) Properties. For instance `CreativeWork` properties will hold information about licence, authors, keywords, version, citation, funder etc.

___Key features of RO-Crates___

* conceptual separation between data entities, such as code stored in the ` model_code_inputs` subdirectory ("@type": "SoftwareSourceCode"), as well as external "contextual" entities which are identified via URIs.

* RO-Crates can be extended to include additional features such as file manifests.
* RO-Crates have to capacity to capture workflows and relationships between inputs, software/binaries, and outputs (e.g., https://www.researchobject.org/ro-crate/1.1/workflows.html). 

___Some terminology___

* schema:
* payload: files and data that exist in a model directory
* crosswalk: Metadata crosswalks translate elements and values from one schema to those of another. 
* entity:

## Building an RO-Crate for a M@TE model


M@TE models are created using a github issue form. When you fill out and submit a `model_submission` issue, some checks will run, and a new repository will be created. This top level directory will be named with a slug: e.g `name_topic_year`. The `ro-crate-metadata.jsonld` file will sit in this directory. The model submission workflow promarily helps users construct this "crate" of metadata.  

The URI for the model will generally be provided through a doi provided by NCI, within the M@TE collection.

While code and documentation can be provide through github, model output data will usually be handled separately, once the model has been checked and copied onto the NCI filesystem, you will recieve an upload link.

M@TE mdoels exists both as a github repository, as well as being hosted on the NCI. Moreover, your model may contain different payloads at different locations depending on different locations. The metadata file is what links these entities together.

## Further information:

Similar projects/efforts can be found at codemeta, comses.net, bioschemas, science-on-schema.

