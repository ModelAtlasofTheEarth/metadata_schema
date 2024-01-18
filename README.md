# M@TE Metadata Model

## Summary

In the M@TE project, the metadata that describes a computational model is based on the ro-crate prject https://www.researchobject.org/ro-crate/.

In ro-crates, a research-object (here a computational model) is encapsulated through a collection (crate) of several `schema.org` types or entities. Together these form a meaningful unit for the purposes of communication, citation, distribution, preservation, etc.

Similar projects/efforts can be found at codemeta, comses.net, bioschemas, science-on-schema.

The file `mate_ro_crate/ro-crate-metadata.jsonld` is the basic template, which is filled out in the model submission stage. Users can extend or modify this file.

## Structure and development


In ro-crates, a research-object (here a computational model) is encapsulated through a collection (crate) of several `schema.org` types or entities.  Schema.org is a collaborative, community activity with a mission to create, maintain, and promote schemas for structured data on the Internet, on web pages, in email messages, and beyond.

Some of these entities refer to directories and file payloads that are stored in the M@TE model (e.g. on Github/NCI), other entities exist elswhere, for instance, data that already availble on persistent web repositories, such as Zenodo. These are identified with the @id property.

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

The most general layer of information is a ro-crate is the Root Data Entity. This has the schema.org Type `DataSet`, which is a subset of `CreativeWork` Type.


A key requirement is that m@tedata can fulfil metadata requirements (ISO 19115) used in the NCI GeoNetwork catalog. Many of the field requierements in ISO 19115 are easily mapped to  `DataSet` (or by inheritance `CreativeWork`) Properties. For instance `CreativeWork` properties will hold information about licence authors, keywords, version, citation, funder etc.

In many cases computatation models involve a novel usage (new model) based on an existing software framework/application. This may involve a new set of paramaters, new plugins, modification to the source code of the existing software application. We want the metadata model try to reflect these relationships. We encourage users to add any model code (and inputs) that are required to run their model. Physcall, these files go into the `model_code_inputs` directory.  


## Questions:

* What to do with multiple entites of the same type (multiple publications, datasets)?
* What @id takes precedence?
* Should we use the concept of a root directory as in RO-Crates

## Further features of RO-Crate

The m@te-data model has several similarities to ro-crate (we try to adopt the same terminology). One similarity is the use of the @graph array as the "bucket" that stores different entitites. Like RO-Crates, m@te-data can also reference  both internal entites, such as code stored in the `code` subdirectory ("@type": "SoftwareSourceCode"), as well as external entities which are stored or accessed separately, via absolute URIs.

Unlike RO-Crates, m@te-data is not intended to create file manifests. One reason for this is that M@TE model a anticapted to have a more homegneous subdirectory structure. That is, we know in advance that certain subdirectories will contain certian files. File manifests are provided by M@TE, but are not included in the m@te-data model. Nor do we envisage m@tadata as a way to encapsulate workflow information (e.g, https://www.researchobject.org/ro-crate/1.1/workflows.html). In this respect we follow comses.net, and leave this to the user to document in standard ways.


## Structure and creation of a M@TE model


A M@TE model is usually created using a github issue form. When you fill out and submit a `model_submission` issue, some checks will run, and a new repository will be created. This top level directory will be named with a slug: e.g `name_topic_year`. The m@te-data.json file will sit in this directory. The model submission workflow promarily helps users contruct this "bucket" of metadata.  

The URI for the model will generally be provided through a doi provided by NCI, within the M@TE collection.

Not all entities need to be physically stored in the M@TE model. For instance, if the code for your model is already archived (e.g. FigShare, Zenodo), you may wish to simply add a URI to this entitity in the graph. Alternatively, you can used the `code` subdirectory to add your model code; in other words, you can add payload files to model subdiretories. In this case the URI (@id) will be doi provided by NCI. This is simalar to the model used in ro-crate.

While code and documentation can be provide through github, model output data will usually be handled separetely. If you click the box "I plan to submit model data", a hidden diretcly will be created in the model creation phase. Later, once the model hae been checked and copied onto the NCI fielsystem, you will recieve an upload link.

At this stage, you will relise that your model exists both as a github repository, as well as beign hosted on the NCI. Morover, your model may contain dofferent payloads at different locations depending on different locations. The metdata file is what links these entities together.

## m@tedata template


![./json_templates/m@te-data.json viewed at https://json-ld.org/playground/)](json_templates/JSON-LD_Playground.png)
