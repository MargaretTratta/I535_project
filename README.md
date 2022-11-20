# I535_Class_Project
November, 2022

This work builds on the cleaning work done by Radomír Černoch to the dataset originally compiled by Gio Wiederhold. Their work is currently (November, 2022) still available:

Original (Wiederhold): https://archive.ics.uci.edu/ml/datasets/Movie

Reformatted (Černoch): https://github.com/cernoch/movies

To prepare this dataset for import into a Neo4j database, additional cleaning / preparation was needed:

-remove remaining historical html formatting artifacts and standardize csv formatting for consistent column import (not all errors were caught, some fields still import into the incorrect column)

-de-duplicated movie ID and director ID records

-Typos in the director field of MAIN made this field unsuitable for matching, extracted director ID from movie ID for matching.

-removed some text field qualifiers (e.g."D:" in director, "@" preceding years (temporal) data)

-split "directed by" data out of MAIN, into separate csv for import

My goal here was learning Neo4j, and not in analyzing the dataset, so not all tables were prepped for Neo4j import. The following tables were culled from the dataset as Černoch stored it:

awtypes

keys

locales

quotes

remakes

sayings

studios

synonyms

Remaining/prepped tables (as csv files):

actors_clean

casts_clean

directed_by_clean

main_clean

people_clean



There were still some .html formatting artifacts (mostly typos of <td>), or other inconsistencies that caused cells to import into an inconsistent column using the csv files downloaded from Černoch’s repository (main_initial_exploration). I wish I had the technical skills to rectify these problems in reproducible code, unfortunately, my current skill level is not that advanced. Utilizing Numbers’ “find and replace” functionality, I was able to standardize column contents, and remove .html formatting artifacts. In the “data prep” folder are "ready" files that were generated using Numbers to remove the html formatting artifacts and standardize column contents and the Jupyter Notebooks with the code used for cleaning and other formatting (e.g. pulling the directed-by relationship out of the main table and into its own table), once the columns were consistent.

Lifecycle Metadata and content metadata on the fields prepped for import is located in lifecycle_metadata.csv and content_metadata.csv

