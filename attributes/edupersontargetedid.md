---
---

# eduPersonTargetedID

**Status:** Core Attribute

**Description:** A persistent, non-reassigned, privacy-preserving identifier for a user shared between an identity provider and service provider. An identity provider uses the appropriate value of this attribute when communicating with a particular service provider or group of service providers, and does not reveal that value to any other service provider except in limited circumstances.

> **Persistence:** eduPersonTargetedID does not require a specific lifetime, but the association should be maintained longer than a single user interaction and long enough to be useful as a key for a particular service that is consuming it.


> **Privacy:** This attribute is designed to preserve the user's privacy and inhibit the ability of multiple unrelated services from correlating user activity by comparing values. It is therefore required to be opaque.


> **Uniqueness:** A value of this attribute is intended only for consumption by a specific audience of applications (often a single one). Values of this attribute therefore must be unique within the namespace of the identity provider and the namespace of the service provider(s) for whom the value is created. The value is "qualified" by these two namespaces and need not be unique outside them. Logically, the attribute value is made up of the triple of an identifier, the identity provider, and the service provider(s).


> **Reassignment:** A distinguishing feature of this attribute is that it prohibits reassignment. Since the values are opaque, there is no meaning attached to any particular value beyond its identification of the user. Therefore particular values created by an identity provider must not be  reassigned such that the same value given to a particular



**Format:** The eduPersonTargetedID value is an opaque string of no more than 256 characters. 

The format comprises the entity name of the identity provider, the entity name of the service provider, and the opaque string value. These strings are separated by “!” symbols.

**Number of values:** Multiple held by a user but only one sent to a service.

Notes on usage: If a service provider is presented only with the affiliation of an anonymous subject, as provided by eduPersonScopedAffiliation, it cannot provide service personalisation or usage monitoring across sessions. These capabilities are enabled by the eduPersonTargetedID attribute, which provides a persistent user pseudonym, distinct for each service provider.

A service provider may use eduPersonTargetedID to support aspects of its service that depend on recognising the same user from session to session. The most common use is to enable service personalisation, to record user preferences such as stored search expressions across user sessions. A secondary use is to enable tracking of user activity, to make it easier to detect systematic downloading of content or other suspected breaches of licence conditions.

The attribute enables an organisation to provide a persistent, opaque, user identifier to a service provider. For each user, the identity provider presents a different value of eduPersonTargetedID to each service provider to which the attribute is released.

The eduPerson specification requires that a value of eduPersonTargetedID once assigned to a user for a given service provider shall never be reassigned to another user. Users and service providers should note, however, that not all identity providers may be able to guarantee that a  user will always present the same value of eduPersonTargetedID; indeed, identity providers may offer their users the ability to generate new values of  eduPersonTargetedID if they feel their privacy has been compromised. identity providers and users should note that changing a user’s eduPersonTargetedID for a particular service provider may break the relationship with that service provider.

Notes on privacy: eduPersonTargetedID is intended to be a privacy-preserving attribute.