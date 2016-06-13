---
---

# eduPersonAssurance

**Status:** Core Attribute

**Description:** Set of URIs that assert compliance with specific standards for identity assurance.

This attribute represents identity assurance profiles (IAPs), which are the set of standards that are met by an identity assertion, based on the identity provider's identity management processes, the type of authentication credential used, the strength of its binding, etc.  For identity assurance, this refers to the strength of the processes used to identify the user at the time of user registration.  For token and credential management assurance, this refers to the strength of the token used and the strength of the processes used to manage tokens and credentials.  Those establishing values for this attribute should provide documentation explaining the semantics of the values. 

The driving force behind the definition of this attribute is to enable applications to understand the various strengths of different identity management systems and authentication events and the processes and procedures governing their operation and to be able to assess whether or not a given transaction meets the requirements for access.

**Format:** A URN that resolves to the definition of the value used.

URNs must have format urn:mace:aaf.edu.au:iap:id:.[level], where level is a value from 1 to 2, or urn:mace:aaf.edu.au:iap:authn:[level], where level is a value from 0 to 2.

E.g.

urn:mace:aaf.edu.au:iap:id:1
urn:mace:aaf.edu.au:iap:id:2

urn:mace:aaf.edu.au:iap:authn:0
urn:mace:aaf.edu.au:iap:authn:1
urn:mace:aaf.edu.au:iap:authn:2

**Number of values:** multiple

As a multi-valued attribute, relying parties may receive multiple values and should ignore unrecognized values.

Notes on usage: There are different aspects to the concept of assurance, including the strength of assurance in the user’s identity and the strength of the method used to authenticate the user. In a SAML federation, it is possible to use two attributes to differentiate these concepts. The AuthenticationMethod attribute that is part of the SAML transaction can assert the strength of the authentication method used in the transaction, and the eduPersonAssurance attribute can assert the level of assurance in the user’s identity. 

The Levels of Assurance section of this wiki provides a standard vocabulary to express both of these concepts – the strength of assurance in the user’s identity and the strength of the method used to authenticate the user.

**Notes on privacy:** Because a particular assurance value may be associated with a small number of persons at an organisation, it may be prudent to remove assurance information from data when performing anonymisation or deidentification.