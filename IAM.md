
Stands for identity and access managements , we could use it to create users and assign them to group. 
- Users are people in the organization and can be grouped
- Groups only contain users, not other groups
- Users don't have to belong to a group and can belong to multiple groups.

### IAM Permission
We create users to give them permission, they can be assigned thanks to a JSON document called "polices".

### IAM polices structures
![[Pasted image 20230203142917.png]]
- `Version` : policy language version.
- `Id` : an identifier for the policy (optional)
- `Statement`: one or more statement (required)
	Statements consists of
		- `Sid`: Statement id
		- `Effect`: whether the statement allows or denies access
		- `Principal`: account/user/role to which this policy is applied to
		- `Action` List of action that this policy allow or denies (based on effect)
		- `Resource` List of res to which the action is applied
		- `Condiction`: for when this policy is in effect