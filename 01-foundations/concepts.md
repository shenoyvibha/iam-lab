What is SP 800-63:
SP 800-63 (version 4 now) is a set of guidelines, not a framework, on digital identity management. It has three parts: identity proofing (63A), authentication (63B) and federation (63C). Its main idea is assurance levels, which let us match the strength of the checks to the risk of the system.
- Identity Assurance Level (IAL): confirms the user is the same person they claim to be in real life. It can be verified with documents such as a driving license or an SSN (the documents differ by country).
- Authenticator Assurance Level (AAL): confirms that the person who registered is the one logging in, using passwords, MFA and so on. Stronger levels use stronger authenticators.
- Federation Assurance Level (FAL): confirms how securely identity attributes and assertions are transmitted across systems.

Why would a non-US company adopt this: (1) Customers, auditors and regulators accept it as a benchmark, so following it is easy to explain and defend. (2) It is detailed enough to be converted into concrete controls, so a company does not have to invent its own standard. It is mandatory only for US federal agencies; everyone else adopts it by choice.

AuthN vs AuthZ: which is more common?
AuthN failures with strong AuthZ are basically weak passwords or shared passwords for accounts. They could be admin accounts or accounts with most access to the systems. What weak authN does is give access to people who are not supposed to reach the secure data. let's say an admin account is shared by a FEDev/ Marketing Analyst and a System Admin. The marketing analyst should not have access to the database which is now enabled by a shared admin account. It also does not help in audit trails because now we only know that the admin account was used but we don't know "who" used it.
In case of AuthN being strong and AuthZ being weak: the problem is that any authenticated user will have access to all the details. This could be a sales rep having access to deleting a plan which is least sold.
So it all depends on which lens you are looking at. it's either a breach of credential or an excess privilege which is noticed.

employee lifecycle:
Joiner -> Mover -> Leaver:
I strongly feel that the mover is the most underestimated move. Let's say a sales rep becomes a developer tomorrow. Initially they had access to the sales dashboard where they could log entries of the sales made, revenue which came in and the billing details of the customer.
Now the software engineer which is the new role of this user has no business in knowing the billing details of the customer. They are a junior developer and have no access to the database(production) but their old permission as sales rep is giving them access to the user's billing and credit card details. Nobody would notice because "nothing breaks". The following control would catch this over privilege: Periodic review of access and catalog match. The role of the user and the permissions for that user should match. if it doesn't its a red flag.

Least privilege:
Least privilege means giving a role only the bare minimum permission needed to achieve its task, and nothing more.

"Enough access" is difficult to pin down because every role needs some access to function. It is role specific and is defined by the type of work the role has to do. Read-only is not automatically least privilege: even read access to sensitive data is exposure if the role has no need for it.

Four parameters come into play: what, where, how long and who.
- What: the type of permission (read, write, delete, admin).
- Where: which system and which environment (dev, staging, production).
- How long: always on, or only for as long as the task needs.
- Who: which specific role, not everyone.

Developer example: a developer needs the billing structure (how the billing data is laid out) to debug a billing issue for a customer, but should not see customers' real billing or card details.
- What: read access to the billing structure only, not to customer billing data, and no write or delete.
- Where: the development or staging database, using masked or test data. Write access is limited to dev; production stays tightly controlled.
- How long: only while working on the issue, not permanently.
- Who: the developers working on billing, not every developer.
