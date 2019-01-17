# Create Marketing Cloud Data Views clones

Two scripts (SSJS) that clones data extensions from the data views and create the queries that populate them.

## Steps

1. Download `all-data-views-de.html` and paste it into a _Cloud Page_ or a Script activity in the automation studio
2. Download `all-data-views-queries.html` and paste it into a _Cloud Page_ or a Script activity in the automation studio
3. Under `Email > subscribers > data extensions` location you will find your data extensions
4. Under `Automation Studio > Activities > All Queries` location you will find the query activities


## Are included

- _Job
- _Sent
- _Click
- _Complaint
- _Open
- _Subscribers
- _SubscriberSMS
- _UndeliverableSms
- _Journey
- _JourneyActivity
- _Bounce
- _PushAddress

## Sample of Script
### data extension
```html
<script runat="server">
    Platform.Load("Core", "1.1.1");
    try {
        var MC_job_data_view = {
            "CustomerKey": "MC_job_data_view",
            "Name": "MC_job_data_view",
            "Fields": [{
                    "Name": "JobID",
                    "IsRequired": true,
                    "FieldType": "Number"
                },
                {
                    "Name": "EmailID",
                    "FieldType": "Number"
                },
                [...]
                {
                    "Name": "TriggeredSendCustomerKey",
                    "MaxLength": 36,
                    "FieldType": "Text"
                }
            ]

        };
        var myMC_job_data_view = DataExtension.Add(MC_job_data_view);

    } catch (ex) {
        Write("error message: " + ex);
    }
</script>
```

### query
```html
<script runat="server">
    Platform.Load("Core", "1.1.1");
    try {
        var queryDef1 = {
            Name: "MC_job_data_view",
            CustomerKey: "MC_job_data_view",
            TargetUpdateType: "Overwrite",
            TargetType: "DE",
            Target: {
                Name: "MC_job_data_view",
                CustomerKey: "MC_job_data_view"
            },
            QueryText: "select * from _Job"
        };
        var status_queryDef1 = QueryDefinition.Add(queryDef1);
    } catch (ex) {
        Write("error message: " + ex);
    }
</script>
```

## Going further
- [Data views](https://help.salesforce.com/articleView?id=mc_as_data_views.htm&type=5)
- [SSJS](https://developer.salesforce.com/docs/atlas.en-us.mc-programmatic-content.meta/mc-programmatic-content/ssjs_syntaxGuide.htm)



 
