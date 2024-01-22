# M@TE Metadata Model

## Summary

In the M@TE project, the metadata format that describes a model is based on the ro-crate project https://www.researchobject.org/ro-crate/. The metadata file is found in the root directory of the model. 

In ro-crates, a research-object (here a computational model) is encapsulated through a collection (crate) of several `schema.org` types or entities. Together these form a meaningful unit for the purposes of communication, citation, distribution, preservation, etc.

Similar projects/efforts can be found at codemeta, comses.net, bioschemas, science-on-schema.

The file `mate_ro_crate/ro-crate-metadata.jsonld` is the basic template, which is filled out in the model submission stage. Users can extend or modify this file.

## ro-crates - background 


In ro-crates, a research-object is encapsulated through a collection (crate) of several `schema.org` types or entities.  Schema.org is a collaborative, community activity with a mission to create, maintain, and promote schemas for structured data on the Internet, on web pages, in email messages, and beyond.

Some of these entities refer to directories and file payloads that are stored in the M@TE model (e.g. on Github/NCI). These are referred to as `data entities` 

Other entities exist elsewhere,  for instance people, research groups, and data is already available on persistent web repositories, such as Zenodo. These are referred to as `contextual entities` 

Ro-crates use the JSON-LD format. JSON-LD is a lightweight Linked Data format.  In the JSON-LD format, the crate is represnted by the @graph array:

```
"@graph": [

  {
    thing1
  },
  {
    thing2
  }]]
```

The most general layer of information is a ro-crate is the Root Data Entity. This has the schema.org Type `DataSet`, which is a subset of `CreativeWork` Type (https://schema.org/CreativeWork)

### ro-crates - M@TE

ro crates provide a nice solution for describing computation models, because they:

* handle the diverse set of entitites that are involved in the creation of model
* are based on schema.org/json
* can be extended to provide descriptions of wokflow


An important requirement is that the ro-crate can fulfil metadata requirements (ISO 19115) used in the NCI GeoNetwork catalog, where M@TE model are stored. Many of the field requirements in ISO 19115 are easily mapped to  `DataSet` (or by inheritance `CreativeWork`) Properties. For instance `CreativeWork` properties will hold information about licence authors, keywords, version, citation, funder etc.

In many cases relevant to M@TE, models involve a novel usage (new model) based on an existing software framework/application. This may involve a new set of parameters, initial-condition, new plugins, or modification to the source code of the existing software application. 

 We encourage users to add any model code (and inputs) that are required to run their model. Physically, these files go into the `model_code_inputs` directory.  They form part of the data entities of the ro-crate. 

___Further features of ro-crates___

* conceptual separation between data entities, such as code stored in the ` model_code_inputs` subdirectory ("@type": "SoftwareSourceCode"), as well as external "contextual" entities which are identified via URIs.

* RO-Crates have additional feature like the ability to create file manifests. In building a basic metadata file for computation models (i.e through the Github issue form) the resulting ro-crate does not include file level descriptions or manifests. 
* Ro-crates have to capacity to capture workflows and relationships between inputs, software/binaries, and outputs (e.g, https://www.researchobject.org/ro-crate/1.1/workflows.html). 



## Building ro-crate for a M@TE model


M@TE models are created using a github issue form. When you fill out and submit a `model_submission` issue, some checks will run, and a new repository will be created. This top level directory will be named with a slug: e.g `name_topic_year`. The `ro-crate-metadata.jsonld` file will sit in this directory. The model submission workflow promarily helps users contruct this "crate" of metadata.  

The URI for the model will generally be provided through a doi provided by NCI, within the M@TE collection.

While code and documentation can be provide through github, model output data will usually be handled separately, once the model has been checked and copied onto the NCI filesystem, you will recieve an upload link.

M@TE mdoels exists both as a github repository, as well as being hosted on the NCI. Moreover, your model may contain different payloads at different locations depending on different locations. The metadata file is what links these entities together.


