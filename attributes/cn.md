---
---

# cn

**Status:** core attribute

**Description:** An individual's common name. For the AAF this is defined as the users first name followed by their surname.

**Format:** first name <space> surname

**Number of values:** single

**Notes on usage:** cn can be used by services for searching for a person, or creating user friendly auxiliary usernames. Usually the cn will contain two names, the first name and surname, with a single space separating them. However, in the situation where a user only possesses one name, then the name will be consider the users surname.

**Notes on privacy:** This attribute should not be used in transactions where it is desirable to maintain user anonymity.