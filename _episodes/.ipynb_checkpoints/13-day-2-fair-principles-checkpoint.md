---
title: "Neuroimaging Data and the FAIR Principles"
teaching: Self-paced
exercises: 30
instructor:
- Yukai Zou
objectives:
- "Understanding identifiers"
- "History of open and linked data"
- "Overview of the FAIR principles"
- "Learn about resources a laboratory can utilize (off the shelf) to be a good steward of their data"
- "Learn about different databasing options if a custom solution is desired"
keypoints:
- Understanding the FAIR Data principles
- Understanding identification of FAIR data
- There are a number of tools, developed by the research community and also by companies, to assist in stewardship of laboratory data.
- There are a number of options for developing your own custom database solution.
---

## Overview

This lesson provides an overview of strategies for making research outputs available through the web, with an emphasis on data. It introduces concepts such persistent identifiers, linked data, the semantic web and the FAIR principles. It is designed for those with little to no familiarity with these concepts. More technical discussions can be found in the reference materials.

> ## Lesson Episodes
> - [Research objects and identifier systems](#research-obj)
> - [Short history of open & linked data technologies](#short-history)
> - [Benefits of linked open data with examples](#benefits-lod)
> - [Towards the FAIR principles](#fair-principles)
> - [FAIR Neuroimaging Data](#fair-neuroimaging-data)
> - [Neuroimaging Data Platforms](#neuroimaging-data-platforms)
{: .callout}

> ## References
> Additional materials:
>
>   - [Linked Data Guides and Tutorials](http://linkeddata.org/guides-and-tutorials)
>   - [Linked Data: Tim Berners-Lee, 2006](https://www.w3.org/DesignIssues/LinkedData.html)
>   - McMurray et al. (2015) 10 Simple rules for design, provision, and reuse of persistent identifiers for life science data, [[link](https://doi.org/10.5281/zenodo.31765)]
>   - [W3C RDF Primer](https://www.w3.org/TR/rdf11-concepts/)
>
> Relevant Books:
>
>   - Tom Heath and Christian Bizer (2011) Linked Data: Evolving the Web into a Global Data Space (1st edition). Synthesis Lectures on the Semantic Web: Theory and Technology, 1:1, 1-136. Morgan & Claypool. [[link](http://linkeddatabook.com/editions/1.0/)]
{: .callout}

<a name="research-obj"></a>
## Research objects and identifier systems

The advent of computers and networks have allowed scientists to share not only the final report of the work, i.e., the scientific article, but also additional research products that form an integral part of the work, e.g., data, code,  workflows and even works like slide presentations. The term "research object" in a general sense connotes these many outputs of scientific research. The term ["research object"](https://en.wikipedia.org/wiki/Research_Object) is also used specifically to refer to a method for the identification, aggregation and exchange of scholarly information on the Web. The basic idea is that each of these objects should have its own persistent identifier (see below) and objects that belong together, e.g., an article with its associated code and data, should have some means of being aggregated, so that all associated research objects can be discovered together.  Although this might seem to be obvious, as research objects are scattered across different repositories on the web, the connections between them are often lost.

One of the most important concepts to understand and implement when developing information systems on the web for robust and reproducible science is that of globally unique and persistent identifiers [(PIDs)](https://en.wikipedia.org/wiki/Persistent_identifier). You will see references to PIDs throughout this tutorial. Globally unique and persistent identifiers are exactly what they sound like: a unique and long-lasting reference to something, e.g., documents, files, books, people and even the concepts that define a field (ontologies). Globally unique means that the identifier points to only a single entity on a global scale. Many of you may be familiar with locally unique identifiers, e.g., database accession numbers, that are unique within a single source. But when utilizing the web to retrieve information, we have to consider the entire web. For example, a web URL is a globally unique identifier because each URL is different. If they weren't, then there would be no sure way to locate documents on the web.

Identifiers for non-digital objects: Persistent identifiers can still be assigned to things that are not natively digital, e.g., people, reagents, concepts. In this case, some authority issues identifiers for these entities. The PID can be thought of as "digital middle names" for things we refer to. If they are unique - that is, each identifier identifies only one thing - and they are designed to be used by computers, then PIDs can be used to locate references to these particular entities reliably and disambiguate that one entity from others that may have similar names. For example, the concept "nucleus" can point to the nucleus of a cell, of an atom or of the brain. But these three concepts each have unique identifiers in biological terminologies such as the Gene Ontology or UMLS (Unified Medical Language System). When these identifiers are used inside of databases or research articles, a machine can easily tell them apart.

Although a URL can be thought of as a form of PID, PIDs are actually distinct from locators like URLs in that they retrieve an object independent of where the object is located on the web. We are all familiar with broken links on the web. A broken link happens when a web browser sends out a request to a server for a document with a specified URL. If that URL no longer exists, because, for example, the system administrator migrated systems and created a new URL or if someone decided to no longer pay the fee to keep up a particularly domain name on the internet, we get a `404: Document not found error`. In scholarship, the [404 error](http://www.cs.umd.edu/~golbeck/LBSC690/SemanticWeb.html) is particularly pernicious as it breaks the chain of evidence that is provided within a scientific paper. If we refer to a web page that no longer exists, we have no way to verify or benefit from the information in that web page. Broken links can be avoided by making sure that re-direct pages are available for old URLs, but how do you know that the new URL actually points to the same document? Also, what happens when multiple copies of the same article exist in different places? Each of those places would have its own URL, making it look to a computer as if the objects they reference are different.

PIDs actually address both of these problems. The identifier is separated from the location so that it buffers against changes in location. If a web document is moved to a new location, the new location is registered with the resolving system so that it now points to the same object in a new place. If the same object is present in multiple locations, e.g., a scientific article can be found at the publisher's web site, in PubMed Central and in platforms such as Mendeley, the DOI listed as part of the metadata is the same, so we know that it is the same article in different places. It is important to note that these identifier systems, as will be discussed below in the FAIR principles, are not magic. Rather they are a social contract between the publisher of research objects and users that they will maintain the integrity of the resolution services.

### Persistent Identifiers in Neuroimaging

The application of persistent identifiers in neuroimaging has been discussed in the context of data citation: "Data Citation in Neuroimaging: Proposed Best Practices for Data Identification and Attribution" ([Honor et al., 2016](https://doi.org/10.3389/fninf.2016.00034)). This paper presents a prototype system to integrate Digital Object Identifiers (DOI) and a standardized metadata schema into a XNAT-based repository, allowing for identification of data at both the project and image level. This identification scheme allows any newly defined combination of images, aggregated from any number of projects, to be tagged with a new group-level DOI that automatically inherits the individual attributes and provenance information of its constituent parts. This allows for the consistent identification of data used as part of an analysis - a key aspect in ensuring analyses are reproducible.

> ## Selected External Lesson Material
> 1. An overview of persistent identifiers from the Australian National Data Service: [Unpacking Persistent Identifiers for Research](https://www.slideshare.net/AustralianNationalDataService/unpacking-persistent-identifiers-for-research)
> 2. EUDAT's [Introduction to Persistent Identifiers](https://www.slideshare.net/EUDAT/introduction-to-persistent-identifiers)
{: .callout}

> ## Exercise: Identifiers (click on the arrow to the right to open)
> **What is the difference between a globally unique and locally unique identifier?**
>
> Consider the PubMed database. PubMed assigns a unique identifier, the PMID, to each article, e.g., PMID:26978244. If you type in the identifier, [26978244](https://www.ncbi.nlm.nih.gov/pubmed/?term=26978244), into the PubMed search box, you will get exactly one article, in this case on the FAIR data principles.  
> 
> But now type that number into Google search. You will see [the article about the FAIR data principles](https://www.ncbi.nlm.nih.gov/pubmed/26978244) but also lots of other things identified by this number, e.g., [an image of a soccer player](https://www.dreamstime.com/stock-images-sk-rapid-vs-austria-wien-image26978244), [a house for sale](http://www.rightmove.co.uk/property-for-sale/property-26978244.html). In other words, divorced from a particular database, the identifier 26978244 is meaningless.
>
> In contrast, when you type in a globally unique identifier, e.g., a DOI, it should identify one and only one object on the web, in this case the article about the FAIR data principles. To see the difference, notice the list of search results when you type in the DOI for this article: `10.1038/sdata.2016.18`.
> As we will discuss in a later session, it is possible to turn a locally unique ID into a globally unique ID by adding additional features, e.g., namespaces before the ID, e.g., `pubmed/.
>
>
> **What is the difference between searching for an PID and resolving an PID?**
>
> There is a difference between identifying an object and accessing it. In the above exercise, when you type the DOI or PMID into a web search, it performs a search for that number just like it would for any search string. Note that the list of results includes URls that will take you to the article itself, e.g., `https://www.nature.com/articles/sdata201618`, or that contain references to the article, e.g., `http://www.ontoforce.com/why-data-should-be-fair/`. A resolving service is more specific; it is designed to resolve to the object that is being referenced. To see how a resolver works, copy `http://dx.doi.org/` into your browser followed by the DOI for the FAIR principles article `10.1038/sdata.2016.18`. Note that it takes you to the web URL [https://www.nature.com/articles/sdata201618](https://www.nature.com/articles/sdata201618) where the article is found. This exercise also illustrates the difference between a PID and URL. If the URL for the article changes, Nature is obliged to notify the DOI maintainer of the new location.
>
{: .challenge}

> ## Exercise: Identifier Resolution (click on the arrow to the right to open)
> **Where can I resolve globally unique identifiers?**
>
> The California Digital Library ([CDL](http://www.cdlib.org)) makes a number of tools available regarding persistent identifiers, including: registering DOIs and ARKs and providing resolution services. The N2T tool (Names to Things) is a resolving service that keeps names (identifiers) persistent, forwarding (resolving) them to the best known web addresses. For example, to resolve the PubMed identifier used in the above challenge, one would use the following call to N2T: [http://n2t.net/pubmed:26978244](http://n2t.net/pubmed:26978244)
>
> The CDL is partnering with [identifiers.org](http://identifiers.org) to maintain a registry of resolvable prefixes. In this exercise, please explore the [registry at identifiers.org](https://www.ebi.ac.uk/miriam/main/collections) and choose a repository.  Browse the repository and extract some IDs and test the resolvers at N2T [http://n2t.net/](http://n2t.net/) and identifiers.org [http://identifiers.org](http://identifiers.org).
>
> If your resource doesn't have its prefix registered, [you can register it via a Google form](https://docs.google.com/forms/d/18MBLnItDYFOglVNbhNkISqHwB-pE1gN1YAqaARY9hDg/viewform?edit_requested=true)
>
{: .challenge}

<a name="short-history"></a>
## Short history of open & linked data technologies

The concepts introduced in the above section - research objects and PIDs - are important for understanding how we can adapt the web for sharing and integrating data. We are all familiar with web-accessible databases, that is, databases that are available for searching through the web. PubMed is one well-known example. But just because a database is web accessible, doesn't mean that its data are designed for use on the web. In fact, data contained in dynamic databases are often considered to be part of the [hidden web](https://en.wikipedia.org/wiki/Deep_web), that is, it is not easily indexed in search engines like Google. The [Neuroscience Information Framework](http://neuinfo.org) was designed to search inside of these databases. But there are ways to design databases so that they are more web friendly. A major proponent of using the internet for sharing data and not simply web document is [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee).

**Linked data** is a method of publishing structured data on the web so that it can be interlinked and queried using a formal semantic query language ([https://en.wikipedia.org/wiki/Linked_data](https://en.wikipedia.org/wiki/Linked_data)). Linked Open Data is linked data that is covered under on open source license so that it can be reused by third parties. Linked data builds upon standard Web technologies, e.g., HTTP, RDF (Resource Description Framework) and URIs (Uniform Resource Identifiers). But rather than using these technologies to share web pages, linked data extends them to share information in a way that can be read automatically by computers. The goal is to allow data from different sources to be connected and queried through a web browser.

Tim Berners-Lee coined the term "Linked Data"" in 2006 and laid out 4 basic principles [[link](https://www.w3.org/DesignIssues/LinkedData.html)]:

1. Use URIs to name (identify) things.
2. Use HTTP URIs so that these things can be looked up (interpreted, "dereferenced").
3. Provide useful information about what a name identifies when it's looked up, using open standards such as RDF, SPARQL, etc.
4. Refer to other things using their HTTP URI-based names when publishing data on the Web.

We've introduced a few new terms here, so let's give a few explanations.

### URI

A [URI](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier) is a PID, i.e, a string of characters used to identify an entity. URIs have a specific syntax (that's what makes them uniform), which we will not go into here (see [Wikipedia](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)). One of the biggest points of confusion in the world of PIDs is the difference between a URI and a URL. In fact, the terms URI and URL are often used interchangeably, but they are distinct. The easiest way to think about it is that a URL is a URI that happens to point to a resource over a network ([Wikipedia](https://en.wikipedia.org/wiki/Uniform_Resource_Identifier)). In other words, *all URLs are URIs but not all URIs are URLs*. In our above examples, we could turn a local identifier into a globally unique identifier by adding a namespace before the ID, e.g., `pubmed/26978244` If we add a network access protocol to that identifier, `**https://www.ncbi.nlm.nih.gov/**pubmed/26978244`, we have a URI that is also a URL. Because we are dealing here with data on the web, most of our URI examples will, in fact, be URLs in accordance with the 2nd principle of Linked Data (Use HTTP URIs so that these things can be looked up).

### RDF 

According to W3C, the standards body for the web, [RDF](https://www.w3.org/RDF/) is *"a standard model for data interchange on the Web"*. RDF has features that facilitate data merging even if the underlying schemas differ, and it specifically supports the evolution of schemas over time without requiring all the data consumers to be changed.

RDF extends the linking structure of the Web to use URIs to name the relationship between things as well as the two ends of the link (this is usually referred to as a "triple"). Using this simple model, it allows structured and semi-structured data to be mixed, exposed, and shared across different applications.

This linking structure forms a directed, labeled graph, where the edges represent the named link between two resources, represented by the graph nodes. This graph view is the easiest possible mental model for RDF and is often used in easy-to-understand visual explanations.

### SPARQL

[SPARQL](https://en.wikipedia.org/wiki/SPARQL) is the query language that is used to query RDF databases.

**Examples**:
An RDF triple comprises a subject, predicate and object, each identified by a URI. In a simple example, a statement such as: Kevin Bacon stars in the movie Footloose can be turned into RDF by coding the subject (Kevin Bacon), the predicate (is star of) and object (Movie:Footloose). A SPARQL query can then be formulated to Find all movies where "is star of" = Kevin Bacon.  Note that this example is highly simplified: please refer to actual coding examples at Wikipedia [here](https://en.wikipedia.org/wiki/Resource_Description_Framework) and at W3C [here](https://www.w3.org/RDF/).

Although the majority of biomedical data sources have been slow to adopt the [Open Linked Data protocol](http://lod-cloud.net/), a perusal of the Linked Open Data Cloud indicates that life sciences comprises a substantial part of the web of data.

<a name="benefits-lod"></a>
## Benefits of linked open data with examples

The benefits of **Linked Open Data (LOD)** are encapsulated in the description of RDF above:
* It facilitates data interchange on the web
* It facilitates data integration across sources even when schemas are different
* It supports evolution of schemas over time with minimal disruption to data consumers

What these benefits mean is that we can use the general architecture of the web to link not just web pages to each other, but objects within databases to similar objects in other databases.  Why is this important?  Currently, information about brain structures, diseases or genes is scattered across hundreds of databases. Searching NIF for [cerebellum](https://neuinfo.org/data/search?q=cerebellum&l=cerebellum#all), for example, yields over 1 million records from > 100 databases. These databases contain different types of information; some contain information on connectivity of the cerebellum, others on gene expression. Still others provide imaging data or measurements of the cerebellum in disease. Currently, a search across NIF will let you see what databases contain the term "cerebellum" and will let you visit each of them. But to integrate the information across them, e.g., find all images of cerebellum showing genes known to be implicated in Parkinson's disease requires a fair amount of work and multiple queries to multiple databases. For example, I might go to ClinVar to find a list of genes associated with Parkinson's disease, then use these genes to query NIF to find [image databases](https://neuinfo.org/data/source/nif-0000-00508-1/search?q=NR4A2&l=+NR4A2) that show expression of these genes.

With LOD, this process becomes much easier. If each of these databases had exposed their data as LOD, it would be possible to construct the query: find all images of cerebellum showing genes known to be implicated in Parkinson's disease, so that it returned the same data in far fewer steps. Why? Because the links between these different data sources would be explicit, so the "mash up" of results from different data sources is facilitated.

Of course, this type of integration is only possible if developers of databases for the life sciences agree to the same set of URIs for the things they refer to, in this case, concepts like "cerebellum" and "disease" and the relationships that connect them. These concepts are typically assigned URIs when they are represented in data structures called ontologies, essentially, formal models of knowledge within a domain. If each database develops its own identifier for Parkinson's Disease, then we are in the same boat as today:  we'd have to go to each database, find their data dictionaries and extract the particular identifier. A single set of identifiers for entities in the life sciences is one of the goals of the [OBO Foundry:  Open Biological Ontologies](http://www.obofoundry.org/). Where it has been achieved, e.g., the Gene Ontology in genomics, cross query of databases is highly facilitated. But for other biological domains, e.g., neuroscience, consistent use of identifiers for concepts and relationships across databases has been less successful. For this reason, life sciences has also had to maintain a lot of cross-mapping between concepts in ontologies and other controlled vocabularies.

> ## Selected External Lesson Material
> 1. Open Data Support's (a project of DG CONNECT of the European Commission) [Linked Open Data: Principles, Technologies and Examples](https://www.slideshare.net/OpenDataSupport/linked-open-data-principles-technologies-and-examples)
> 2. Data Europa:
>   * [The usefulness of data - the starts of linked open data](https://data.europa.eu/en/academy/usefulness-data-stars-linked-open-data)  
>     **Abstract:** This course focuses on understanding the concept of the 5 stars of linked open data. You will learn about the web of linked open data, understand how the 5 Stars of open linked data can help you start browsing the web of data, and understand and being able to recognise the first 3 stars.
>   * [Data citation: a guide to best practice [data citation, citation, interoperability]](https://data.europa.eu/en/academy/data-citation-guide-best-practice-data-citation-citation-interoperability)  
>     **Abstract:** Everyday millions of people use data. They search, publish, reuse, analyse! But very often, a major difficulty for the users is finding the right data. And how to help them? It is simple: Cite the data! This training is focused on introducing the publication “Data citation: a guide to best practice”. It is a practical guide that includes recommendations and best practices on how to cite data. It is divided in 3 parts: 1) issues in data citation, general recommendations; 2) recommendations on specific formats and other elements for data citation; 3) other information (e.g. specific differences between recommendations). At the end you will find many useful annexes with checklists, diagrams and examples.
> 4. [Linked Data Engineering](https://open.hpi.de/courses/semanticweb2016), provided by openHPI (the educational Internet platform of the German Hasso Plattner Institute)
> 5. Coursera's [Web of Data](https://www.coursera.org/learn/web-data?aid=true)
{: .callout}

<a name="fair-principles"></a>
## Towards the FAIR principles

While LOD has had some uptake across the web, the number of databases using this protocol compared to the other technologies is still modest. But whether or not we use LOD, we do need to ensure that databases are designed specifically for the web and for reuse by humans and machines. To provide guidance for creating such databases independent of the technology used, the FAIR principles were issued through [FORCE11](http://force11.org): the Future of Research Communications and e-Scholarship. The FAIR principles put forth characteristics that contemporary data resources, tools, vocabularies and infrastructures should exhibit to assist discovery and reuse by third-parties through the web.  

According to Wilkinson et al. ([2016](https://www.nature.com/articles/sdata201618)), FAIR stands for: Findable, Accessible, Interoperable and Re-usable. The definition of FAIR is provided in Table 1:

Number | Principle
--------- | -----------
**F**         | **Findable**
F1        | (meta)data are assigned a globally unique and persistent identifier
F2        | data are described with rich metadata
F3        | metadata clearly and explicitly include the identifier of the data it describes
F4        | (meta)data are registered or indexed in a searchable resource
**A**         | **Accessible**
A1        | (meta)data are retrievable by their identifier using a standardized communications protocol
A1.1      | the protocol is open, free, and universally implementable
A1.2      | the protocol allows for an authentication and authorization procedure, where necessary
A2        | metadata are accessible, even when the data are no longer available
**I**         |**Interoperable**
I1        | (meta)data use a formal, accessible, shared, and broadly applicable language for knowledge representation.
I2        |(meta)data use vocabularies that follow FAIR principles
I3        |(meta)data include qualified references to other (meta)data
**R**       | **Reusable**
R1        |meta(data) are richly described with a plurality of accurate and relevant attributes
R1.1      |(meta)data are released with a clear and accessible data usage license
R1.2      |(meta)data are associated with detailed provenance
R1.3      |(meta)data meet domain-relevant community standards

A detailed explanation of each of these is included in the article ([Wilkinson et al., 2016](https://www.nature.com/articles/sdata201618)).

<img src="{{ page.root }}/tni2022/assets/img/FAIRprinciples850width.png" 
alt="The FAIR data principles" width="80%"/>

### Findable
Findable comprises two major attributes: the data set be identified by a PID, so that it can be unambiguously located by a machine and the data be described by sufficient metadata so that it an be discovered by a human. F3 connects the identifier to this rich metadata so that a human can verify that the dataset is correctly resolved. Finally, the data must be registered or indexed so that it can be found. The more machine-readable metadata that a data resource provides for its contents, the more likely a web search through a search engine like Google will find them.

### Accessible
Accessible provides requirements for ensuring that third parties can access the data by specifying that the PID is resolvable and that the access protocol is standard, e.g., http, and open.  The access protocol should allow for authentication and authorization to protect sensitive data.  Finally, a critical requirement to ensure the integrity of links across the web is that the metadata persist, even if the data they describe have been removed for some reason. In this way, a basic description of the data can still be found at the same PID, much like descriptive metadata of out of print books can still be found. Ideally, the page describing the metadata includes a statement about when and why the data were removed [(Starr et al., 2015)](https://peerj.com/articles/cs-1/).

### Interoperable
Interoperable outlines requirements for ensuring that data across databases can be combined with minimal effort. Note that this principle specifically calls for the use of formal vocabularies widely used in a community that are themselves FAIR, i.e., have a persistent identifier and access protocol.

### Reusable
Reusable also emphasizes rich metadata, but in this case so that the dataset can be sufficiently understood by a human so that it can be reused appropriately. Many communities have published minimal information models that provide the minimum set of attributes required for proper interpretation of a given data set, e.g., [MIAME](http://fged.org/projects/miame/). Reusable also specifies that a data license, preferably in a machine-readable form, accompanies the data specifying how it may be re-used, e.g., a CC-BY license specifies that the data may be re-used without restriction, but attribution of the source must accompany the reuse.  And, of course, re-usable emphasizes the use of community-accepted standards for metadata and for data themselves. A major goal of ReproNim is to help define these standards for neuroimaging.

It is important to reiterate that, unlike LOD described in the previous section, the FAIR principles are not a protocol or a standard.  Rather, they are viewed as characteristics modern databases, and, indeed, any research object, should have if they are to be useful. Along these lines, some of the original authors of the FAIR paper published a follow up paper [Mons et al., 2017](http://content.iospress.com/articles/information-services-and-use/isu824), outlining what the FAIR principles are not. FAIR is not:
* A standard
* Equivalent to RDF, Linked Data, or the Semantic Web
* Equivalent to open

The Linked Data protocol can be fully FAIR, if implemented properly, but as the authors discuss, these technologies may not be optimal for representing certain types of data. The authors also explicitly state that FAIR data need not be open data, although it is hard to see how data can be maximally reusable if they are not.  But even the most ardent open advocates recognize that all data may not be openly shared, particularly in the case where sharing would cause potential harm to either the research subjects or the researcher. Because FAIR is aspirational and flexible, it has enjoyed wide endorsement by the US National Institutes of Health, the G20, ELIXIR and H2020.

> ## Selected External Lesson Material
> 1. [FAIR Data Principles Explained](https://www.dtls.nl/fair-data/fair-principles-explained/) - a step by step guide through the FAIR data principles
> 2. [An overview on FAIR Data](https://www.slideshare.net/lolavo/fair-data-overview) and the roadmap for FAIR Data solutions coordinated by the Dutch Techcentre for Life Sciences
> 3. [FAIR Data stewardship](https://www.dtls.nl/fair-data/data-stewardship/) by the Dutch Techcentre for Life Sciences
{: .callout}

> ## Exercise (click on the arrow to the right to open)
>  At the current time, the best way to ensure that your data are FAIR is to deposit them in a database that observes the FAIR principles.  How do you know if a repository observes FAIR?  In this exercise, you will visit some repositories and mark them against the principles above to create a FAIR scorecard.
>
>  1. [NITRC-IR](http://www.nitrc.org/ir/)
>  2. [OpenfMRI](https://openfmri.org/)
>  3. [NeuroVault](http://www.neurovault.org/)
>  4. [DataVerse](https://dataverse.harvard.edu/)
>  5. [DataLad datasets](https://datasets.datalad.org/)
>  6. A repository of your choosing
>
> [Submit your answers via Google Form](https://goo.gl/forms/uCOC34qwJARtQzPT2)
{: .challenge}

<a name="fair-neuroimaging-data"></a>
## FAIR Neuroimaging Data

### Brain Imaging Data Structure (BIDS)
[BIDS](http://bids.neuroimaging.io) is a community developed file organization and naming scheme ([GitHub Repository](https://github.com/INCF/BIDS)) that makes it easier to publish data and share it with others in a consistent format. BIDS is being developed within the [International Neuroinformatics Coordinating Facility](http://incf.org) and in the collaboration with many scientists working in the neuroimaging field. The goal of BIDS is to define a powerful, flexible, and consistent framework for integrating the diverse types of experimental data routinely acquired in neuroimaging studies. Provisions are included in BIDS to accommodate these data types: subject-level variables (e.g. gender, age, handedness); longitudinal and multi-session studies; structural, anatomical imaging data; resting state and task-based fMRI data; task event information; diffusion-weighted imaging data; field maps for correcting for B0 inhomogeneity; physiological monitoring output acquired during MRI experiments; behavioral data collected without MRI; and standardized metadata to describe the conditions and parameters of the experiment data.

> ## Selected External Lesson Material
> 1. Krzysztof Gorgolewski's overview of BIDS and reproducibility: [Towards open and reproducible neuroscience in the age of big data](https://www.slideshare.net/chrisfilo1/towards-open-and-reproducible-neuroscience-in-the-age-of-big-data)
> 2. The [BIDS Specification](https://bids-specification.readthedocs.io/en/stable/)
> 3. "The brain imaging data structure, a format for organizing and describing outputs of neuroimaging experiments" (Gorgolewski et al 2016) [link](http://n2t.net/doi:10.1038/sdata.2016.44)
{: .callout}

> ## Exercise: Create a BIDS-compliant dataset (click on the arrow to the right to open)
>
> In this exercise you will work through the creation of a BIDS dataset using sample data.  Please follow the following steps:
>
> 1. Download the [sample base dataset]({{site.root}}/data/TNI001_base.zip). This sample data contain both MRI and SPECT images collected at University Hospital Southampton.
> 2. Re-work the base dataset to conform to BIDS.
> 3. As you work through this exercise - you can use the [BIDS validator](http://incf.github.io/bids-validator/) to check your progress (must use Google Chrome or Firefox).
>
{: .challenge}

> ## Exercise Solution (click on the arrow to the right to open)
>
> We have made the original BIDS dataset for the single subject available:
>
> 1. Download the [sample BIDS dataset]({{site.root}}/data/TNI001_bids.zip)
{: .challenge}

### Neuroimaging Data Model (NIDM)

[NIDM](http://nidm.nidash.org) captures brain data, workflow, and results in a structured format using a derivative of the W3C PROV Data Model. Currently, results of fMRI analyses conducted in FSL and SPM can be stored using NIDM-Results. These results can be uploaded to NeuroVault for sharing with others.

> ## Selected External Lesson Material
> 1. [Getting Started with NIDM](http://nidm.nidash.org/getting-started/)
> 2. [NIDM Specifications](http://nidm.nidash.org/specs/)
{: .callout}

### The International Neuroinformatics Coordinating Facility (INCF) Recommendations

There are currently many choices of repository, which is quite diverse and may confuse neuroimaging and neuroinformatics researchers. The International Neuroinformatics Coordinating Facility (INCF) has developed selection criteria and associated recommendations (below) for the neuroscience community, to provide researchers with guidance to pick the resource that fits them best:

1. Ensure discoverability and transparency in ownership and service usage statistics
2. Clearly communicate access and reuse conditions
3. Consider ethical requirements for authorship transparency and sensitive data
4. Follow best practices for licensing and responsibility
5. Ensure accessibility and interoperability
6. Build capabilities for reproducibility, replicability, reuse
7. Excel in documentation and user support
8. Be transparent in governance and operations
9. Involve community in governance and decision making
10. Be transparent on sustainability - financial and technical

A detailed checklist of the recommendations is available via the INCF portal [here](https://
www.incf.org/criteria-checklist).

> ## References
> * Recommendations for repositories and scientific gateways from a neuroscience perspective (Sandström et al., 2022) [[link](https://doi.org/10.1038/s41597-022-01334-1)]
{: .callout}

### Committee on Best Practice in Data Analysis and Sharing (COBIDAS) Recommendations
To advance open science in neuroimaging the Organization for Human Brain Mapping created the Committee on Best Practice in Data Analysis and Sharing (COBIDAS), charged with creating a report that collects best practice recommendations from experts and the entire brain imaging community. The purpose of this work is to elaborate the principles of open and reproducible research for neuroimaging using Magnetic Resonance Imaging (MRI), and then distill these principles to specific research practices.

> ## References
> * Best practices in data analysis and sharing in neuroimaging using MRI (Nichols et al., 2017) [[link](https://www.nature.com/articles/nn.4500)]
{: .callout}

<a name="neuroimaging-data-platforms"></a>
## Neuroimaging Data Platforms

There are many options available when it comes to neuroimaging data management. A number of academic and commercial products allow you to manage your neuroimaging and associated data within their platform. This session focuses on resources available at the University of Southampton and University Hospital Southampton NHS Foundation Trust (UHS).

### eXtensible Neuroimaging Archive Toolkit (XNAT)

[XNAT](https://www.xnat.org) is an open-source imaging informatics platform that can store, manage, and share neuroimaging data. Originally developed by the Buckner Lab (now at Harvard University) and the [Neuroinformatics Research Group](https://github.com/NrgXnat) at Washington University in St Louis, XNAT facilitates common management, productivity, and quality assurance tasks for imaging and associated data. Thanks to its extensibility, XNAT has widely implemented to support a wide range of imaging-based projects around the world.

#### XNAT at UHS

The XNAT services are provided by UHS at the following addresses:

Instances | Use Cases | URLs 
--------- | --------- | ---- 
Identifiable | UHS internal only | [UHS_XNAT_IDENTIFIABLE](https://connect.uhs.nhs.uk/app/template/,DanaInfo=rhmxnat.uhs.nhs.uk+Login.vm#!)
Pseudonymised | UHS internal only | [UHS_XNAT_ANON](https://connect.uhs.nhs.uk/app/template/,DanaInfo=rhmxnatanon.uhs.nhs.uk+Login.vm#!)
De-identified | UHS external | [https://xnat.uhs.nhs.uk](https://xnat.uhs.nhs.uk)

#### Anonymisation using DicomEdit

XNAT has built-in anonymisation/pseudonymisation using ``DicomEdit`` scripts, but users can consider using customised script such as ``pydicom`` to include important capabilities. ``DicomEdit`` is a domain-specific mini language that was developed by the same team as XNAT and is documented [here](https://wiki.xnat.org/xnat-tools/dicomedit/dicomedit-6-2-language-reference). Updated version of ``DicomEdit`` may have built-in important capabilities, e.g., replacing UIDs with new UIDs in a coherent way that does not break referential integrity, but this is not guaranteed.

#### Download Data from XNAT

XNAT makes the individual slices available at a fixed URL for download, rather it has a [REST API](https://wiki.xnat.org/display/XAPI/XNAT+API+Documentation) that is accessible via URLs and allows programmatic [discovery & downloading](https://wiki.xnat.org/display/XAPI/How+To+Download+Files+via+the+XNAT+REST+API) of those projects, **sessions**, and images that the user has access to. 

An XNAT **project** is the top-level object in XNAT’s hierarchy. A project contains both subjects/patients and scans. XNAT implements access control using logon sessions, so all XNAT users have an account that they can log in to, and each XNAT project has access control lists that grant specific users a given level of access.

> ## References
> - [XNAT GitHub](https://github.com/NrgXnat)
> - Full documentation for XNAT can be found on their [Wiki](https://wiki.xnat.org/documentation) page.
> - [XNAT Tools: DicomEdit 6.2 Language Reference](https://wiki.xnat.org/xnat-tools/dicomedit/dicomedit-6-2-language-reference)
> - [REST API](https://wiki.xnat.org/display/XAPI/XNAT+API+Documentation)
> - [How To Download Files via the XNAT REST API](https://wiki.xnat.org/display/XAPI/How+To+Download+Files+via+the+XNAT+REST+API)
{: .callout}