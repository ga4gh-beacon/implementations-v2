
## Progenetix & Beacon<span style="color: red; font-weight: 800;">+</span>

The Beacon+ implementation - developed in the Python & MongoDB based [`bycon` project](https://github.com/progenetix/bycon/) -
implements an expanding set of Beacon v2 paths for the [Progenetix](http://progenetix.org)
resource.

### Examples

#### Base `/filtering_terms`

##### `/filtering_terms/`

* [/filtering_terms/](https://progenetix.org/beacon/filtering_terms/)


##### `/filtering_terms/` + query

* [/filtering_terms/?filters=PMID](https://progenetix.org/beacon/filtering_terms/?filters=PMID)
* [/filtering_terms/?filters=NCIT,icdom](https://progenetix.org/beacon/filtering_terms/?filters=NCIT,icdom)

#### Base `biosamples`

##### `/biosamples/` + query

* [/biosamples/?filters=cellosaurus:CVCL_0004](https://progenetix.org/beacon/biosamples/?filters=cellosaurus:CVCL_0004)
  - this example retrieves all biosamples having an annotation for the Cellosaurus _CVCL_0004_
  identifier (K562)

##### `/biosamples/{id}/`

* [/biosamples/pgxbs-kftva5c9/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/)
  - retrieval of a single biosample

##### `/biosamples/{id}/variants/` & `/biosamples/{id}/variants_in_sample/`

* [/biosamples/pgxbs-kftva5c9/variants/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants/)
* [/biosamples/pgxbs-kftva5c9/variants/](http://progenetix.org/beacon/biosamples/pgxbs-kftva5c9/variants_in_sample/)
  - retrieval of all variants from a single biosample
  - currently - and especially since for a mostly CNV containing resource - `variants` means "variant instances" (or as in the early v2 draft `variantsInSample`) 


#### Base `variants`

There is currently (April 2021) still some discussion about the implementation and naming
of the different types of genomic variant endpoints. Since the Progenetix collections
follow a "variant observations" principle all variant requests are directed against
the local `variants` collection.

If using `g_variants` or `variants_in_sample`, those will be treated as aliases.

##### `/variants/` + query

* [/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000](http://progenetix.org/beacon/variants/?assemblyId=GRCh38&referenceName=17&variantType=DEL&filterLogic=AND&start=7500000&start=7676592&end=7669607&end=7800000)
  - This is an example for a Beacon "Bracket Query" which will return focal deletions in the TP53 locus (by position).

##### `/variants/{id}/` or `/variants_in_sample/{id}` or `/g_variants/{id}/`

* [/variants/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/)
* [/variants_in_sample/5f5a35586b8c1d6d377b77f6/](http://progenetix.org/beacon/variants_in_sample/5f5a35586b8c1d6d377b77f6/)

##### `/variants/{id}/biosamples/` & `variants_in_sample/{id}/biosamples/

* [/variants/5f5a35586b8c1d6d377b77f6/biosamples/](http://progenetix.org/beacon/variants/5f5a35586b8c1d6d377b77f6/biosamples/)
* [/variants_in_sample/5f5a35586b8c1d6d377b77f6/biosamples/](http://progenetix.org/beacon/variants_in_sample/5f5a35586b8c1d6d377b77f6/biosamples/)
