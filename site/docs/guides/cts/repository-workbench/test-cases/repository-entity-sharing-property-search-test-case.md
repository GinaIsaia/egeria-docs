<!-- SPDX-License-Identifier: CC-BY-4.0 -->
<!-- Copyright Contributors to the ODPi Egeria project. -->

# Repository entity sharing property search test case

This test validates that a repository connector supports `findEntitiesByProperty` using match properties
and `findEntitiesByPropertyValue` using search criteria, where the repository does not support the
creation of metadata instances through the metadata collection interface. Such a repository does not
support methods like addEntity() or addRelationship(). This testcase relies on there being existing instances
in the repository; it performs a broad search to retrieve an initial set of instances, and then performs
finer-grain searches and verifies that the results are consistent with the initial instance set and the
query that was performed.

The metadata collection interface 'find' methods accept regular expressions, but for many purposes a caller may be satisfied
with exact match semantics. To achieve this, it is recommended that the caller invokes on the repository helper methods, such
as `getExactMatchRegex()`. This testcase is concerned with this type of use of the metadata collection interface. String
property values and search criteria (a string that is tested against all string properties) are specified
as exact match regular expressions as produced by the repository helper's exact match regex method.

## Operation

The entity sharing property search testcase extracts the entity type definitions supported by the repository under test.
For each supported entity type it performs a broad search using `findEntitiesByProperty()`, in which no match properties
are specified. This initial search will return up to a page worth of instances. The testcase analyses the returned instances
and constructs follow-on queries based on the property values found in the initial set.

The follow-on queries use property values from the initial set together with different settings for matchCriteria, to
retrieve further result sets. Each result set is verified against what would be expected in terms of the initial set,
the query parameters and the fact that these searches may return hitherto unseen entities that were not in the initial
set due to paging, but which are nevertheless valid results.


## Assertions

The following assertions are used in this testcase


* **repository-sharing-entity-property-search-01** - findEntitiesByProperty returned a result.
* **repository-entity-sharing-property-search-02** - findEntitiesByProperty search contained the expected number of entities.
* **repository-entity-sharing-property-search-03** - findEntitiesByProperty search contained expected entities.
* **repository-entity-sharing-property-search-04** - findEntitiesByProperty match criteria ANY returned a result.
* **repository-entity-sharing-property-search-05** - findEntitiesByProperty match criteria ANY search contained the expected number of entities.
* **repository-entity-sharing-property-search-06** - findEntitiesByProperty match criteria ANY search contained expected entities.
* **repository-entity-sharing-property-search-07** - findEntitiesByProperty match criteria ALL returned a result.
* **repository-entity-sharing-property-search-08** - findEntitiesByProperty match criteria ALL search contained the expected number of entities.
* **repository-entity-sharing-property-search-09** - findEntitiesByProperty match criteria ALL search contained expected entities.
* **repository-entity-sharing-property-search-10** - findEntitiesByProperty match criteria NONE returned a result.
* **repository-entity-sharing-property-search-11** - findEntitiesByProperty match criteria NONE search contained the expected number of entities.
* **repository-entity-sharing-property-search-12** - findEntitiesByProperty match criteria NONE search contained expected entities.
* **repository-entity-sharing-property-search-13** - findEntitiesByPropertyValue returned a result.
* **repository-entity-sharing-property-search-14** - findEntitiesByPropertyValue search contained the expected number of entities.
* **repository-entity-sharing-property-search-15** - findEntitiesByPropertyValue search contained expected entities.




## Discovered Properties

There are no discovered properties for this test - the search capabilities are part of the mandatory profile.




---8<-- "snippets/abbr.md"
