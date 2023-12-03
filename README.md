# M@TE Metadata overview (m@tadata)

The m@tadata model is a collection of resources represented as a Schema.org types, that together form a meaningful unit for the purposes of communication, citation, distribution, preservation, etc. The development was informed by projects such as codemeta, ro-crate amd comses.net

## Summary


In the M@TE project, a computational model is represented by several schema.org types. Of these, only one is considered essential: the `CreativeWork'. This is a broad category that encompassed many applicable entities, such as Dataset, SoftWareSource code. Many of the field requierements in ISO 19115 are easily mapped to  `CreativeWork' Properties. For instance `CreativeWork' properties will hold information about licence and author

Similar to ro-crate, we us an @graph array to add entities to the metadata model. The `CreativeWork' entity is one. Other useful entities are `DataSet', `SoftwareSourceCode' and `Publication'. The metadata format is flexilble, as additional entities may be added by the user. 

What to do with multiple entites of the same type. 

The model submission workflow promarily helps users contructe this `bucket' of metadata.  

The metadata template (m@tadata.json) is based on json-ld and schema.org, and was designed to fulfil metadata requirements (ISO 19115) used in teh NCI GeoNetwork catalog. 


## Structure and creation of a M@TE model

A M@TE model can be created from scratch, or created usinf a github issue form. The latter is preffered. When you fill out and submit a `model_submission' issue, some check will run, and a new repository will be created. This top level directory will be named with a slug: e.g `name_topic_year'. The m@tadata.json file will sit in this directory. 

The URI for the model will generally be provided through a doi provided by NCI, within the M@TE collection. 

Not all entities need to be physically stored in the M@TE model. For instance, if teh code for your model is already archived, you may wish to simply add a URI to that node in the graph. Alternatively, you can used the `code' subdirectory to add your model code; in this case the URI will will be doi provided by NCI. This is simalar to the model used in ro-crate. 

While code and documentation can be provide through github, model output data will usually be handled separetely. If you click the box "I plan to submit model data", a hidden diretcly will be created in the model creation phase. Later, once the model hae been checked and copied onto the NCI fielsystem, you will recieve an upload link. 

At this stage, you will relise that yout model exisst both in gihub, and the NCI (and possibly also Zenode). The metdata file is what links these entites togetrehr, and 
