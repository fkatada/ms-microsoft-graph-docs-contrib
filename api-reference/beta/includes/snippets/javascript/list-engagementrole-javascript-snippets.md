---
description: "Automatically generated file. DO NOT MODIFY"
---

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let roles = await client.api('/employeeExperience/roles')
	.version('beta')
	.get();

```