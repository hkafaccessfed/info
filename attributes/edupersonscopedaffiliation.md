---
---

# eduPersonScopedAffiliation

**Status:** core attribute

**Description:** Specifies the person's affiliation within a particular security domain in broad categories.

**Format:** The attribute is structured as a scoped attribute, with the form affiliation@security-domain, where affiliation is one of a number of prescribed categories of user. 

Only these values are allowed to the left of the "@ sign:


|     Value |	 Meaning |
|----|----|
|     faculty|Academic or research staff |
|     student |	 Undergraduate or postgraduate student |
|    staff |	All staff |
|    employee	| Employee other than staff, e.g. contractor |
|     member | Comprises all the categories named above, plus other members with normal institutional privileges, such as honorary staff or visiting scholar |
|     affiliate	 | Relationship with the institution short of full member |
|     alum	| Alumnus/alumna (graduate)
|     library-walk-in	| A person physically present in the library  |


The values to the right of the "@" sign should indicate a security domain.

**Number of values:** multiple

**Notes on usage:** This attribute enables an organisation to assert its relationship with the user. This addresses the common case where a resource is provided on a site license basis, and the only access requirement is that the user is a bona fide member of the organisation, or a specific school or faculty within it.

This attribute may appear suitable for controlling access to, for example, an academic licensed commercial software package. However, this is usually not the case; such licenses have greater constraints than just eduScopedPersonAffiliation=faculty. In most cases an academic user must also agree to use the application for only academic purposes and perhaps accept obligations such as acknowledging the owners or reporting results in a particular way.

**Notes on privacy:** eduPersonScopedAffiliation should be used when the service provider does not need confirmation of the security domain of the user. Service providers who do need the security domain information should ask for eduPersonScopedAffiliation instead.

Several values of eduPersonScopedAffiliation are regarded as being "contained" within other values: for example, the student value is contained within member. It is recommended that identity providers have the ability either to maintain these multiple values for a given individual, or otherwise provide the ability to release either value as appropriate for a particular relying party. For example, although some relying parties might require the release of the more specific student value, a different relying party that only requires the less specific member value should only be sent the less specific value. Releasing student in this case gives the relying party more information about the user than is required, raising privacy and data protection concerns.

Despite the recommendation above that identity providers should be conservative in what they send, relying parties are recommended to be liberal in what they accept. For example, a relying party requiring member affiliation should also accept student, staff, etc. as alternatives.