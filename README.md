# DBGI QGIS plugin

QGIS plugin that creates a suited geopackage for the EMI project (including DBGI). 

## Prerequisites

This plugin is expected to be used inside a QGIS project made for QField (.qgs project file) and shared on QFieldCloud. So QField Sync plugin is expected to be installed.

## Arguments to provide:

1. The name of the geopackage
2. The name of a table (geopackage), already present on the QGIS project, that contains binomial nomenclature
3. The name of the column that contains binomial nomenclature
4. The name of a table (geopackage), already present on the QGIS project, that contains collectors informations
5. The name of the column that contains name of the collector
6. The name of a table (geopackage), already present on the QGIS project, that contains organs that will be collected
7. The name of the column that contains name of the organ

## Explanation of the arguments:

The name of the geopackage has to be unique among the project.

The binomial list is here to help the person who collect the samples. It could be a predeined list (for example a list of plants in a botanical garden, or the list of species present in a specific habitat where the samples are collected). The specific column containing the binomial nomenclature has to be specified. This is in case the list is composed of multiple columns. This permits to make the link between this list and the field "sample_name" of the geopackage file.

The collector list is here to know who has collected which specimen. This list has to contain minimum 2 columns, named "fullname" and "ORCID".

The organ list is here to know which part of the specimen is collected. This list has to contain minimum 1 column with the different organs.

## Action:

Creates the necessary fields for the collection:

- collector_fullname: Full Name of the collector

- observation_subject: Part of the specimen that is collected

- inat_upload: boolean that specifies if the actual specimen has to be uploaded on iNaturalist or not

- taxon_name: binomial nomenclature of the collected specimen

- no_name_on_list: boolean that specifies if the actual specimen is on the existing list. If true (specimen is not on the list), "name_proposition" field will appear

- name_proposition: A free field to enter a specific binomial name if it is not on the defined list

- sample_id: unique code applied to this sample, for example dbgi_123456 for the DBGI project or fibl_123456 for the FIBL project

- picture_panel, picture_general, picture_detail, picture_cut, picture_panel_label, picture_free": attachment fields to add pictures of the observed specimen

- x_coord, y_coord: x and y coordinates of the specimen

- ipen: unique identifier of the specimen, if coming from a botanical garden

- herbivory_(percent): Permits to add herbivory on the specimen (if plant)

- comment_eco: Free text to add informations about the ecology of the specimen

- soil_type: Permits to add the soil type where the specimen has been observed (useful for plants, mushrooms, insects, ...)

- weather: meteorological conditions during the observation

- temperature_(°C): Temperature during the observation

- comment_env: Free text to add informations about the environment of the specimen

- date: Stores automatically the precise date of the observation (precision: second)

- collector_orcid": ORCID identifier of the collector

Changes field properties (relation, NotNull, Unique, widget type)

Changes QField attachment naming expression: permits to rename the pictures taken, that facilitates the pictures treatment after collection. This is why QField Sync plugin has to installed.

Adds a label for displayed observation on the map.

Shows layer feature count.

# To build the plugin

```bash
cd gpkg-creator
zip -r gpkg_creator_vXX.zip gpkg_creator -x "*.git*" "*.DS_Store" "pycache/*" "*.pyc" "*.pyo"
```

This can be directly loaded from QGIS.


