## Entity: Catalogue
-----------------
**mandatory:**
  - dct:title
  - dct:description
  - dct:contactPoint
  - dct:publisher
  - dct:applicableLegislation

**recommended:**
  - dcat:catalog
  - dcat:dataset
  - dcat:service
  - dct:creator
  - dct:hasPart
  - foaf:homepage
  - dct:language
  - dct:license
  - dct:modified
  - dct:issued
  - dct:record
  - dct:rights
  - dct:temporal
  - dct:themeTaxonomy
  - dct:spatial

→ Links to:
- Dataset (via `dcat:dataset`)
- Project (via `dcat:resource`)


## Entity: Dataset
---------------
**mandatory:**
  - dct:title
  - dct:description
  - dct:identifier
  - dct:theme
  - dct:publisher
  - dct:contactPoint
  - dct:creator
  - dct:type
  - dcat:keyword
  - dcat:accessRights
  - dct:applicableLegislation
  - healthdcatap:healthTheme
  - dpv:hasLegalBasis
  - healthdcatap:numberOfRecords
  - dct:spatial

**recommended:**
  - dcat:inSeries
  - dcat:distribution
  - dct:isReferencedBy
  - dct:temporal
  - dct:temporalResolution
  - dct:issued
  - dct:modified
  - adms:status
  - healthdcatap:retentionPeriod
  - dcat:version
  - adms:versionNotes
  - dcat:hasVersion
  - dct:language
  - dct:conformsTo
  - foaf:page
  - dct:accrualPeriodicity
  - dpv:hasPurpose
  - dpv:hasPersonalData
  - healthdcatap:populationCoverage
  - healthdcatap:numberOfUniqueIndividuals
  - healthdcatap:minTypicalAge
  - healthdcatap:maxTypicalAge
  - healthdcatap:hasCodedValues
  - healthdcatap:hasCodingSystem
  - healthdcatap:healthCategory
  - dpv:hasQualityAnnotation
  - prov:qualifiedAttribution
  - healthdcatap:analytics
  - adms:sample
  - adms:identifier
  - healthdcatap:publisher
  - healthdcatap:publisherNote
  - dcat:qualifiedRelation
  - prov:wasUsedBy
  - prov:wasGeneratedBy

→ Links to:
- Distribution (via `dcat:distribution`)
- Catalogue (reverse link via `dcat:dataset`)


## Entity: Distribution
--------------------
**mandatory:**
  - dcat:accessURL
  - dct:license
  - dct:applicableLegislation

**recommended:**
  - dcat:mediaType
  - dct:title
  - dct:description
  - dcat:byteSize
  - dcat:accessService
  - foaf:page
  - dcat:downloadURL
  - dct:issued
  - dct:modified
  - adms:status
  - dct:temporalResolution
  - healthdcatap:retentionPeriod
  - spdx:checksum
  - dct:language
  - dct:conformsTo
  - dct:format
  - dcat:compressFormat
  - dcat:packageFormat
  - dct:rights

→ Linked from:
- Dataset (via `dcat:distribution`)

## Entity: Project
------------------
**mandatory:**
- dct:title
- dct:description
- dct:identifier
- foaf:fundedBy
- dcat:resource

**recommended:**
- dct:hasPart

→ Links to:
- Catalogue (via `dcat:resource`)
- Investigation (via `is a` relationship)


## Entity: Investigation
------------------------
**mandatory:**
- Identifier
- Title
- Description
- SubmissionDate
- Publications
- PublicReleaseDate
- Contacts

**recommended:**
_(not explicitly listed, but follows from Study links)_

→ Links to:
- Study (1:n)


## Entity: Study
----------------
**mandatory:**
- dct:title (rdfs:Literal[1..n])
- dct:description (rdfs:Literal[1..n])
- dct:identifier (rdfs:Literal[1..1])
- dct:isPartOf (foaf:Project[1..1])
- SubmissionDate
- PublicReleaseDate
- Publications
- Contacts
- DesignType
- FactorName
- FactorType

→ Links to:
- Sample (via `containsSample`)
- Individual (via `generated by/used by`)

## Entity: Individual
---------------------
**attributes:**
- sex at birth
- ancestry
- age distribution
- BMI
- Medical History
- Pharmacological agent use
- Coverage/followup
- education
- Insurance Status

→ Links to:
- Sample (1:n)


## Entity: Sample
-----------------
**mandatory:**
- Organism
- Organism part
- Sample Type/Specimen
- Derived from
- Individual
- AssayPerformed

→ Links to:
- Individual (n:1)
- Assay (1:n)


## Entity: Assay
----------------
**mandatory:**
- isolation protocol
- biological replicates
- technical replicates
- sample concentration
- sample concentration unit
- sample preparation protocol
- quality report
- quality assessment
- raw file
- Technology/Platform
- TechnologyType
- MeasurementType

**recommended:**
- sample amount unit
- sample amount value

→ Links to:
- Sample (n:1)
- Datafile (via `data files`)
- Omics Types (see below)


## Entity: Datafile
-------------------
(no attributes listed — placeholder)

→ Linked from:
- Assay


## Omics Assay Types
---------------------
Used to specialize or categorize `Assay`. Connected via dashed line (implies inheritance or categorization):

- Lipidomics
- Glycoproteomics
- Proteomics
- Epigenomics
- Genomics
- Transcriptomics
- Metabolomics

→ Links to:
- Assay (via classification or type)