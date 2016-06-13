---
---

# mail

**Status:** core attribute

**Description:** The person's public email address used to contact the person regarding matters related to their organisation.

**Format:** A valid email address as defined in RFC 822.

**Number of values:** single.  Service providers expect to receive only one and only one email address per user).

**Notes on usage:** Mail address should only be used when the service provider needs to communicate with the end user. It should not be used as an identifier and should not be relied upon to be persistent.

**Notes on privacy:** This attribute should not be used in transactions where it is desirable to maintain user anonymity. Privacy considerations should be observed when making a decision about releasing this attribute, as it provides user contact information.