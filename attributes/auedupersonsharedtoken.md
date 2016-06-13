---
---

# auEduPersonSharedToken

Status: Optional Attribute

Description: A unique identifier enabling federation spanning services such as Grid and Repositories. Values of the identifier are generated using a set formula. The value has the following qualities:

-    unique
-    opaque
-    non-targeted
-    persistent
-    resolvable (only by an IdP that has supplied it)
-    not re-assignable
-    not mutable (refreshing the value is equivalent to creating a new identity)
-    permitted to be displayed

    (Note: the value is somewhat display friendly, and may be appended to the displayName with a separating space, and used as a unique display name to be included in PKI Certificate DNs and as a resource ownership label, e.g. John Citizen ZsiAvfxa0BXULgcz7QXknbGtfxk) 

-    portable

**Format:** 27 character PEM “Base 64 Encoding with URL and Filename Safe Alphabet” encoded string from a 160-bit SHA1 hash of a globally unique string. Padding character, ‘=’, is removed from the value. Reference: http://tools.ietf.org/html/rfc4648#page-7

**Number of values:** Single

**Notes on usage:** Service providers participating in federation spanning services may use auEduPersonSharedToken to uniquely identify users to other systems or to map to and from identities in PKI certificates used in grid authentication. Other attributes (e.g. displayName, identity provider Id, etc) may be used together with auEduPersonSharedToken as a transparent description of a particular person at a point in time. This can be implemented to enable interoperability of both SAML and PKI based systems with services such as data and compute grids. The user’s displayName and identity provider may change over time, but it is possible to implement mechanisms for the auEduPersonSharedToken to remain the same.

**Notes on privacy:** auEduPersonSharedToken is not a privacy preserving identifier and should not be used where services are intended to be provided anonymously. Although auEduPersonSharedToken is an opaque value, as it may be released with the displayName it cannot be relied upon to preserve
anonymity.