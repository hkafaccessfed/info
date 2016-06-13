---
---

# displayName

**Status:** core attribute

**Description:** The preferred name of a person to be used when displaying entries.

**Format:** free string

**Number of values:** single

**Notes on usage:** Where a relying party has a requirement for a user’s name, the displayName is the preferred attribute to request. An identity provider may source the value to return as displayName from any appropriate internal attributes. Relying parties should note this value is not guaranteed to be either unique or persistent. It is not recommended to be used as a unique key or for authorisation.

**Notes on privacy:** This attribute should not be used in transactions where it is desirable to maintain user anonymity.