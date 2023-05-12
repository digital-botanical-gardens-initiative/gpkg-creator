# gpkg_creator

QGIS plugin that creates a suited geopackage for the DBGI project. 

## Prerequisites

This plugin is expected to be used inside a QGIS project made for QField (.qgs project file) and shared on QFieldCloud. So QField Sync plugin is expected to be installed.

## Arguments to provide:

1. The name of the geopackage
2. The name of a file (CSV or geopackage), already present on the QGIS project, that contain a column that contains binomial nomenclature
3. The name of the column that contains binomial nomenclature

## Explanation of the arguments:

The name of the geopackage has to be unique among the project and has to be linked with the name of the person that collects these samples. For example: firstname_lastname. 

The binomial list is here to help the person who collect the samples. It could be a predeined list (for example a list of plants in a botanical garden, or the list of species present in a specific habitat where the samples are collected).

The specific column containing the binomial nomenclature has to be specified. This is in case the list is composed of multipl columns. This permits to make the link between this list and the field "sample_name" of the geopackage file.

## Action:

Creates the necessary fields for the collection:

- sample_name = binomial nomenclature of the collected species
- sample_id = unique code applied to this sample, for example dbgi_123456 for the DBGI project
- picture_panel = a picture of the specimen's panel if available (cultivated plants for example)
- picture_general = a general picture of the specimen
- picture_detail = a remarkable detail that permits the identification of the species
- picture_cut = a picture showing the collected part of the specimen
- picture_panel_label = a picture of the sample_id with the panel if available, with the specimen if panel not available

Changes field properties (relation, NotNull, Unique, widget type)

Changes QField attachment naming expression: permits to rename the pictures taken, that facilitates the pictures treatment after collection. This is why QField Sync plugin has to installed.

Adds a label for displayed observation on the map.

Shows layer feature count.
