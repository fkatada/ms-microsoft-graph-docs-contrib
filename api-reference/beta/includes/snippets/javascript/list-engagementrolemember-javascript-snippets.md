---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/employeeExperience/roles/{engagementRoleId}/members')
	.version('beta')
	.get();

```