---
---

# eduPersonEntitlement

**Status:** Core Attribute

**Description:** URI (either URN or URL) that indicates a set of rights to specific resources.

**Format:** URIs only, i.e. a URL or URN, see [RFC 3986]

**Number of values:** Multiple

**Notes on usage:** The meaning of a given value of eduPersonEntitlement is normally defined by a service provider. In the case of a value using the "http" scheme, it is recommended that the value resolve to a document giving the definition of the value. Having defined the meaning of the attribute value, the service provider then invites some or all identity providers to express that value for those users who satisfy the definition. In this way the service provider can delegate to the identity provider some or all of the responsibility for authorisation of access to a particular resource.

Typically, this attribute is used to assert entitlements over and above those enjoyed by other members of the organisation; for example, "Entitled to access the restricted material present in the Med123 resource". In this case, the service provider trusts the organisation to verify that the user
satisfies the (arbitrarily complex) authorisation conditions associated with the entitlement. This may involve an additional licence clause, where the organisation undertakes to assign the eduPersonEntitlement values according to agreed criteria. 

Notes on privacy: Because a particular value of eduPersonEntitlement often represents an entitlement to access a specific resource, Identity Providers should be capable of associating any number of entitlements with an individual user. However, such entitlements may represent personal or even sensitive personal data about the individual. It is therefore important to control the release of individual values of eduPersonEntitlement closely, so that only Service Providers with a legitimate need for any given value of eduPersonEntitlement will have that value released to them. For example, values defined by a particular Service Provider should normally only be released back to that same Service Provider.