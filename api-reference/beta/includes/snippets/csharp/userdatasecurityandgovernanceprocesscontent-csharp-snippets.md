---
description: "Automatically generated file. DO NOT MODIFY"
---

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.Me.DataSecurityAndGovernance.ProcessContent;
using Microsoft.Graph.Beta.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new ProcessContentPostRequestBody
{
	ContentToProcess = new ProcessContentRequest
	{
		ContentEntries = new List<ProcessContentMetadataBase>
		{
			new ProcessConversationMetadata
			{
				OdataType = "microsoft.graph.processConversationMetadata",
				Identifier = "07785517-9081-4fe7-a9dc-85bcdf5e9075",
				Content = new TextContent
				{
					OdataType = "microsoft.graph.textContent",
					Data = "Write an acceptance letter for Alex Wilber with Credit card number 4532667785213500, ssn: 120-98-1437 at One Microsoft Way, Redmond, WA 98052",
				},
				Name = "PC Purview API Explorer message",
				CorrelationId = "d63eafd2-e3a9-4c1a-b726-a2e9b9d9580d",
				SequenceNumber = 0L,
				IsTruncated = false,
				CreatedDateTime = DateTimeOffset.Parse("2025-05-27T17:23:20"),
				ModifiedDateTime = DateTimeOffset.Parse("2025-05-27T17:23:20"),
			},
		},
		ActivityMetadata = new ActivityMetadata
		{
			Activity = UserActivityType.UploadText,
		},
		ProtectedAppMetadata = new ProtectedApplicationMetadata
		{
			Name = "PC Purview API Explorer",
			Version = "0.2",
			ApplicationLocation = new PolicyLocationApplication
			{
				OdataType = "microsoft.graph.policyLocationApplication",
				Value = "83ef208a-0396-4893-9d4f-d36efbffc8bd",
			},
		},
		IntegratedAppMetadata = new IntegratedApplicationMetadata
		{
			Name = "PC Purview API Explorer",
			Version = "0.2",
		},
		AdditionalData = new Dictionary<string, object>
		{
			{
				"deviceMetadata" , new UntypedObject(new Dictionary<string, UntypedNode>
				{
					{
						"operatingSystemSpecifications", new UntypedObject(new Dictionary<string, UntypedNode>
						{
							{
								"operatingSystemPlatform", new UntypedString("Windows 11")
							},
							{
								"operatingSystemVersion", new UntypedString("10.0.26100.0")
							},
						})
					},
					{
						"ipAddress", new UntypedString("127.0.0.1")
					},
				})
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Me.DataSecurityAndGovernance.ProcessContent.PostAsync(requestBody);


```