1.	Design patterns:
		- builder patterns: helpful in creating complex object. Mostly famous in java related langs but in python there are other syntactic sugar which make this pattern redundant (e.g., named args, default args, etc.)

2.	Entities:
	- Users:
		- RBAC (role based access control)
		- In base user entity, we should only track these two things:
			- Authentication: are u really who u claim to be?
			- Authorization: is this person allowed to do this operation?
	- Role:
	- Profile/Account:
	- Registered users:
	- Medicine:
		- regulated/controlled
	- Medicine category:
		- name
		- category
	- Order:
	- Cart:
	- Item:
	- Address:
	- Shipment:
	- Notification:
	- Payment Gateway:
	- Invoice/Order/Trxn:
	- Prescription:
		- prescription-only
		- other-regulated-drugs
		- ENUM:
			- pending
			- accepted
			- rejected
			- in-review
		- file_url (prescription docs/files uploaded by user)
	- Employee:
	- Inventory Item/Stock Item:
		- ts_purchased
		- vendor
		- expiry_date
		- quantity
		- cost
		- batch_no

3.	Guest user can also add item to cart and this will be done using browser session-id

4.	Attribute/Enum vs class hierarchy:
		- ENUM (drug type):
			- controlled
			- non-controlled
			- serious regulated
		- class based:
			- class medicine:
			- class controlled_medicine extends medicine:
			- class non_controlled_medicine extends medicine:

5.	aggregation:
		- A doesn't own B
	composition:
		- entity A owns entity B

6.	normalize:
		- pincode
		- city
		- state

		-> id, pincode, city, state

7.	normalize till it hurts, 
	and denormalize till it works or most of the time people go with caching than denormalizing.

8.	Medicine *---* Medicine Category
9.	Prescription *---1 Order

10. 	Relationship can also have attributes.
	- MedicineOrderMapping will have item count attribute

11.	Cart 1---* CartItem

12.	encoding: utf-8, ascii, base-64
	encryption (it's reversible): AES, RSA, DES, ceaser cipher
	hash (it's irreversible): md5, sha1, sha256, checksumm, bcrypt

13.	

