---
title: 'Introduction to Azure Cosmos DB API for MongoDB'
description: Learn how you can use Azure Cosmos DB to store and query massive volumes of JSON documents with low latency using the popular OSS MongoDB.
keywords: what is MongoDB
services: cosmos-db
author: SnehaGunda

ms.service: cosmos-db
ms.component: cosmosdb-mongo
ms.topic: overview
ms.date: 02/12/2018
ms.author: sclyon
experimental: true
experiment_id: "662dc5fd-886f-4a"
---
# Introduction to Azure Cosmos DB API for MongoDB

[Azure Cosmos DB](../cosmos-db/introduction.md) is Microsoft's globally distributed, multi-model database service for mission-critical applications. Azure Cosmos DB provides [turn-key global distribution](distribute-data-globally.md), [elastic scaling of throughput and storage](partition-data.md) worldwide, single-digit millisecond latencies at the 99th percentile, and guaranteed high availability, all backed by [industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db/). Azure Cosmos DB [automatically indexes data](https://www.vldb.org/pvldb/vol8/p1668-shukla.pdf) without requiring you to deal with schema and index management. It is multi-model and supports document, key-value, graph, and columnar data models. 

![Azure Cosmos DB API for MongoDB](./media/mongodb-introduction/cosmosdb-mongodb.png) 

Azure Cosmos DB databases can be used as the data store for apps written for [MongoDB](https://docs.mongodb.com/manual/introduction/). This functionality means that by using existing [drivers](https://docs.mongodb.org/ecosystem/drivers/), your application written for MongoDB can now communicate with Azure Cosmos DB and use Azure Cosmos DB databases. In many cases, you can switch from using MongoDB to Azure Cosmos DB by simply changing a connection string. Using this functionality, you can easily build and run MongoDB globally distributed database applications in the Azure cloud with Azure Cosmos DB and it's [comprehensive industry-leading SLAs](https://azure.microsoft.com/support/legal/sla/cosmos-db), while continuing to use familiar skills and tools for MongoDB.

**MongoDB compatibility**: You can use your existing MongoDB expertise, application code, and tooling as Azure Cosmos DB implements the MongoDB wire protocol. You can develop applications using MongoDB and deploy them to production using the fully managed, and globally distributed Azure Cosmos DB service. For more information on supported versions see [MongoDB Protocol Support](mongodb-feature-support.md#mongodb-protocol-support).

The Azure Cosmos DB API for MongoDB cannot be used as a direct endpoint for services such as Azure Stream Analytics, because the it uses the same [client drivers](https://docs.mongodb.org/ecosystem/drivers/) as the native MongoDB. To integrate with Azure Stream Analytics, consider using [Azure App Service](../app-service/overview.md) or [Azure Functions Service](../azure-functions/functions-overview.md) as a middleware service that can write data to the Azure Cosmos DB API for MongoDB.

## What is the benefit of using Azure Cosmos DB for MongoDB applications?

**Elastically scalable throughput and storage:** Meet your applications needs by easily scaling up or down your Azure Cosmos DB for MongoDB API database. Your data is stored on solid-state disks (SSD) for low predictable latencies. Azure Cosmos DB supports MongoDB collections that can scale to virtually unlimited storage sizes and provisioned throughput. You can elastically scale Azure Cosmos DB with predictable performance seamlessly as your application grows. 

**Multi-region replication:** Azure Cosmos DB transparently replicates your data to all regions you've associated with your Cosmos account, enabling you to develop applications that require global access to data while providing tradeoffs between consistency, availability, and performance, all with corresponding guarantees. Azure Cosmos DB provides transparent regional failover with multi-homing APIs, and the ability to elastically scale throughput and storage across the globe. Learn more in [Distribute data globally](distribute-data-globally.md).

**No server management**: You don't have to manage and scale your Azure Cosmos DB for MongoDB API databases. Azure Cosmos DB is a fully managed service, which means you do not have to manage any infrastructure or Virtual Machines yourself. Azure Cosmos DB is available in 30+ [Azure Regions](https://azure.microsoft.com/regions/services/).

**Tunable consistency levels:** Because Azure Cosmos DB supports multi-model APIs the consistency settings are applicable at the account level and enforcement of the consistency is controlled by each API. Until MongoDB 3.6, there was no concept of a session consistency, so if you set a Azure Cosmos DB API account for MongoDB to use session consistency, the consistency is downgraded to eventual when using Azure Cosmos DB API for MongoDB. If you need a read-your-own-write guarantee for an Azure Cosmos DB API for MongoDB, the default consistency level for the account should be set to strong or bounded staleness. Learn more in [Using consistency levels to maximize availability and performance](consistency-levels.md).

| Azure Cosmos DB Default Consistency Level |	Mongo API (3.4) |
|---|---|
|Eventual| Eventual |
|Consistent Prefix| Eventual with consistent order |
|Session| Eventual with consistent order |
|Bounded Staleness| Strong |
| Strong | Strong |

**Automatic indexing**: By default, Azure Cosmos DB automatically indexes all the properties within documents in your Azure Cosmos DB for MongoDB API database and does not expect or require any schema or creation of secondary indices. In addition, the unique index capability enables a uniqueness constraint on any document fields that are already auto-indexed in Azure Cosmos DB.

**Enterprise grade**: Azure Cosmos DB supports multiple local replicas to deliver 99.99% availability and data protection in the face of local and regional failures. Azure Cosmos DB has enterprise grade [compliance certifications](https://www.microsoft.com/trustcenter) and security features. 

## How to get started

Follow the MongoDB quickstarts to create an Azure Cosmos DB account and migrate your existing MongoDB application to use Azure Cosmos DB, or build a new one:

* [Migrate an existing Node.js MongoDB web app](create-mongodb-nodejs.md).
* [Build a web app with .NET and the Azure portal using Azure Cosmos DB API for MongoDB](create-mongodb-dotnet.md)
* [Build a console app with Java and the Azure portal using Azure Cosmos DB API for MongoDB](create-mongodb-java.md)

## Next steps

Information about the Azure Cosmos DB API for MongoDB is integrated into the overall Azure Cosmos DB documentation, but here are a few pointers to get you started:

* Follow the [Connect to an Azure Cosmos DB API for MongoDB account](connect-mongodb-account.md) tutorial to learn how to get your account connection string information.
* Follow the [Use Studio 3T (MongoChef) with Azure Cosmos DB](mongodb-mongochef.md) tutorial to learn how to create a connection between your Azure Cosmos DB database and MongoDB app in Studio 3T.
* Follow the [Migrate data to Azure Cosmos DB with protocol support for MongoDB](mongodb-migrate.md) tutorial to import your data to an Azure Cosmos DB for MongoDB API database.
* Connect to an API for Azure Cosmos DB API for MongoDB account using [Robomongo](mongodb-robomongo.md).
* Learn how to [configure read preferences for globally distributed apps](../cosmos-db/tutorial-global-distribution-mongodb.md).
