---
title: "Add GSI to existing DynamodDB table (nodejs, aws-sdk)"
date: 2021-08-05T19:11:00+02:00
draft: false
tags: ["linux", "cli", "terminal", "grep", "ag", "ack"]
---

If you are using the Serverless Framework, you can create DynamodDB and add **one** GSI with cloudformation syntax.

How to add table: https://www.serverless.com/framework/docs/providers/aws/guide/resources/#configuration

Here is the syntax to add GSI: https://cloudkatha.com/solved-cannot-perform-more-than-one-gsi-creation-or-deletion-in-a-single-update/

Official docs related to GSI cloudformation syntax: https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-dynamodb-gsi.html

That's all fine until you need to add another GSI. You can't do that with Cloudformation syntax [1]. Luckily we can do that programatically with Node.js (you could also use another programming language and just use the related aws-sdk library: https://aws.amazon.com/tools/

Here is the code snippet to create a new GSI on an existing DynamodDB table.
The `AttributeDefinitions` need to reflect the new GSI, _not_ the existing table.

```javascript
const {
  DynamoDBClient,
  UpdateTableCommand,
} = require("@aws-sdk/client-dynamodb");

const tableName = "YOUR DYNAMODB TABLE NAME GOES HERE";
const region = "YOUR REGION, e.g. us-east-1";
const accessKeyId = "Your api user access key with access to dynamodb";
const secretAccessKey = "Your api user access secret";

(async () => {
  const config = {
    region,
    credentials: {
      accessKeyId,
      secretAccessKey,
    },
  };
  console.log(config);
  const client = new DynamoDBClient(config);
  const params = {
    TableName: tableName,
    AttributeDefinitions: [
      { AttributeName: "sk", AttributeType: "S" },
      { AttributeName: "pk", AttributeType: "S" },
    ],
    GlobalSecondaryIndexUpdates: [
      {
        Create: {
          IndexName: "sk-pk-index",
          KeySchema: [
            { AttributeName: "sk", KeyType: "HASH" },
            { AttributeName: "pk", KeyType: "RANGE" },
          ],
          Projection: { ProjectionType: "ALL" },
          ProvisionedThroughput: {
            ReadCapacityUnits: 1,
            WriteCapacityUnits: 1,
          },
        },
      },
    ],
  };
  const command = new UpdateTableCommand(params);
  try {
    await client.send(command);
  } catch (e) {
    console.error(e);
  }
  console.log(JSON.stringify(command));
})();
```

1. https://stackoverflow.com/questions/36918408/unable-to-add-gsi-to-dynamodb-table-using-cloudformation
