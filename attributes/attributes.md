---
---

# HKAF Attributes

Attributes are pieces of information about a user, such as name or email address. 

This page provides background information on how to map the HKAF attributes to your own Identity Management System (IdMS). 

We recommend you visit the HKAF core attributes overview and the HKAF core attributes specification and understand the guidelines for implementation. 

## Attributes Overview

- The HKAF has Core, Recommended, and Optional attributes

- The HKAF attribute set is based on multiple formal attribute specifications:
      
  - Basic LDAP schema (person)
  - eduPerson – additional attributes useful for academic environment
  - auEduPerson – additional extensions developed by AAF

- The IdP can pull some attributes directly from the IdMS 
(LDAP, AD):
  - Core attributes: displayName, mail, cn
  - Recommended: givenName, sn

- Some attributes are hashes calculated on the fly
  - Core: eduPersonTargetedID, auEduPersonSharedToken (SharedToken should be stored back in the IdMS or a DB)

- Some attributes have to be synthesized from existing IdMS information
  - eduPersonPrincipalName: <uid> + ‘@’ + ‘domain.edu.au’
  - eduPersonAffiliation: using a scriptlet:

    IF isStaff==TRUE THEN ‘staff’

- Some attributes may have to be added to the identity management system (e.g, eduPersonEntitlement, eduPersonAssurance)

## Attribute Matrix

### HKAF Core Attributes###

| Attribute Name | Typical source |	 Description |
|----------------|----------------|--------------|
| [displayName](http://hkafaccessfed.github.io/info/attributes/displayname) |	 LDAP |	 Preferred name of a person to be used when displaying entries. |
| [eduPersonAffiliation](http://hkafaccessfed.github.io/info/attributes/edupersonaffiliation)  | 	 Scriptlet definition |  	 Specifies the person’s relationship(s) to the institution in broad categories such as student, faculty, staff, alum, etc. |
|     [eduPersonEntitlement](http://hkafaccessfed.github.io/info/attributes/edupersonentitlement)  |	 LDAP (if available) | 	 URI (either URN or URL) that indicates a set of rights to specific resources. |
| [eduPersonScopedAffiliation](http://hkafaccessfed.github.io/info/attributes/edupersonscopedaffiliation) | 	 Take eduPersonAffiliation + "@" + add Scope | 	 Specifies the person’s affiliation within a particular security domain in broad categories such as student, faculty, staff, alum, etc. |
|     [eduPersonTargetedID](http://hkafaccessfed.github.io/info/attributes/edupersontargetedid)  | 	 Hash with write back |  	 A persistent, non-reassigned, privacy-preserving identifier for a user shared between an identity provider and service provider. An identity provider uses the appropriate value of this attribute when communicating with a particular service provider or group of service providers, and does not reveal that value to any other service provider except in limited circumstances. |
| [authenticationMethod](http://hkafaccessfed.github.io/info/attributes/authenticationmethod) |	 IdP	| Set of URIs that assert compliance with specific standards for authentication method. |
|     [eduPersonAssurance](http://hkafaccessfed.github.io/info/attributes/edupersonassurance)  | 	 LDAP (if available or synthesized from other available information) | 	 Set of URIs that assert compliance with specific standards for identity assurance. |
|     [cn](http://hkafaccessfed.github.io/info/attributes/cn) 	| LDAP |	 User’s first name then surname.|
|     [o (or organizationName)](http://hkafaccessfed.github.io/info/attributes/o) | Static | 	 Standard name of the top-level organization (institution) with which this person is associated. |
|     [mail](http://hkafaccessfed.github.io/info/attributes/mail)   |	 LDAP  |	 Email address, single value. User’s preferred outward facing email address with regard to the organisation.  |


### HKAF Recommended Attributes ###

|   Attribute Name	| Typical Source | 	 Description |
|----|-----|----|
|[auEduPersonSharedToken](http://hkafaccessfed.github.io/info/attributes/auedupersonsharedtoken)  |	 Hash with write  back | 	 A unique identifier enabling federation spanning services such as Grid and Repositories. |
|    [givenName](http://hkafaccessfed.github.io/info/attributes/givenname)  |	 LDAP	| A persons first name or preferred name |
|     [sn (surname)](http://hkafaccessfed.github.io/info/attributes/surname)  |	 LDAP	| A persons surname |
|     [schacHomeOrganization](http://hkafaccessfed.github.io/info/attributes/schachomeorganization) 	| Static |                	 Specifies a person’s home organisation using the domain name of the organisation. |
|     [schacHomeOrganizationType](http://hkafaccessfed.github.io/info/attributes/schachomeorganizationtype)	| Static	| Specifies a person’s home organisation's type. |
|     [organizationalUnit](http://hkafaccessfed.github.io/info/attributes/organizationalunit)	| LDAP	| Specifies a person's unit within their home organisation. |
|     [postalAddress](http://hkafaccessfed.github.io/info/attributes/postaladdress)	| LDAP	| Specifies a person's postal address. |
|     [telephoneNumber](http://hkafaccessfed.github.io/info/attributes/telephonenumber)	| LDAP	| Specifies a person's telephone number. |
|     [mobileNumber](http://hkafaccessfed.github.io/info/attributes/mobilenumber)	| LDAP	| Specifies a person's mobile telephone number.|
|     [businessCategory](http://hkafaccessfed.github.io/info/attributes/businessCategory)	| LDAP	| Define the type of business in which organisation is involved. |
|     [departmentNumber](http://hkafaccessfed.github.io/info/attributes/departmentNumber)	| LDAP	| Specify a person’s department code within their organisation. |
|      [division](http://hkafaccessfed.github.io/info/attributes/division)	| LDAP	| Specify a person’s division within their organisation. |
|    [eduPersonOrcid](http://hkafaccessfed.github.io/info/attributes/eduPersonOrcid) |     	 LDAP |	 A persistent digital identifier that distinguishes the account holder from every other researcher. |

