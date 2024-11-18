# URN "thread" Registry

Version ID: 1.4.0

## 1. General

### URN rules
The terminology and rules for "thread" URNs are defined in [urn-registration-v1.txt](urn-registration-v1.txt).

### Security 
Registered `sub-namespace` entries MUST NOT contain privacy- or security-sensitive information. The `sn-content` elements MAY contain privacy- or security-sensitive information if the information is properly protected (cryptographically and/or physically) during URN handling.
Any URNs that may contain privacy- or security-sensitive `sn-content` are marked as "private" in the Security column of the table. "public" means no privacy- or security-risks apply.

### References
- [ThreadSpec] Thread Group, Inc., Thread Specification v1.4.0, September 26, 2024.

## 2. Registry entries

| URN sub-namespace and sn-content | Short Description                 | Security | [ThreadSpec] References
|----------------------------------|-----------------------------------|----------|------------------------ 
| `dataset:act:hex:<hex-string>`   | Active Operational Dataset (hex)  | private  | 8.4.2.2.2, 8.7.4.7
| `dataset:pen:hex:<hex-string>`   | Pending Operational Dataset (hex) | private  | 8.4.2.2.2, 8.7.4.7
| `pc:<code-string>`               | Thread Administration Passcode    | private  | 8.4.9
| `spec:<version>`                 | Thread Specification Version      | public   | 2.9.4
| `spec:<version>:sec:<section>`   | Thread Spec Section Reference     | public   | 2.9.4


## 3. Entry details

### dataset:act:hex:\<hex-string>	
An Active Operational Dataset as a hexadecimal string encoding of all included TLVs. 
- \<hex-string> MUST match the regexp: `[a-fA-F0-9]*` 
- \<hex-string> is case-insensitive
- length of \<hex-string> MUST be an even number of characters
- a zero-length \<hex-string> denotes an empty dataset
- there is no top-level MLE Active Operational Dataset TLV used

Example: `urn:thread:dataset:act:hex:0e080000000000010000000300000f35060004001fffe0020839758ec8144b07fb0708fdf1f1add0797dc00510f366cec7a446bab978d90d27abe38f23030f4f70656e5468726561642d353933380102593804103ca67c969efb0d0c74a4d8ee923b576c0c0402a0f7f8`


### dataset:pen:hex:\<hex-string>	
A Pending Operational Dataset as a hexadecimal string encoding of all included TLVs.
- \<hex-string> defined as for dataset:act:hex:\<hex-string>
- there is no top-level MLE Pending Operational Dataset TLV used


### pc:\<code-string>
Thread Administration Passcode. A temporary, single-use numeric code that is used for Thread Administration Sharing.
- \<code-string> MUST match the regexp: `[0-9]+`
- specific Thread use cases of the passcode MUST define additional length requirements for code-string (including minimum and maximum lengths).

Example: `urn:thread:pc:903723159`


### spec:\<version>
A reference to a particular version of a Thread Specification.
- \<version> is a string e.g. 1.1.1, 1.2.0, 1.2.1, 1.3.0, 1.3.1, 1.4.0 etc.

Example: `urn:thread:spec:1.3.0`


### spec:\<version>:sec:\<section>
A reference to a numbered Section of a Thread Specification.
- \<version> is a string as defined in the previous row.
- \<section> is a string of the section number, without trailing dot.

Example: `urn:thread:spec:1.4.0:sec:2.9.5`
