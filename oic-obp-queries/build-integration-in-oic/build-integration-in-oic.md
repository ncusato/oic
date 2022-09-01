# Build Integration in OIC

## Introduction

In this lab, we will create an integration in OIC drive this REST connection to OBP. We will declare JSON payloads to enable mapping between integration points.

Estimated Time: 15 minutes

### Objectives

In this lab, you will complete the following tasks:

- Search App Driven Orchestration
- Create Sample REST Endpoint
- Declare JSON payload for REST
- Declare response JSON payload for REST
- Create OBP Balance Transfer Invocation
- Declare JSON payload for OBP
- Declare response JSON payload for OBP
- Map to Invocation from Sample REST Endpoint
- Map to Invocation from OBP Balance Transfer Endpoint
- Add Tracking
- Activate Integration
  

### Prerequisites

This lab assumes you have:
- An Oracle Always Free/Free Tier, Paid or LiveLabs Cloud Account

## Task 1: Create Predictive Model

1. Notice the new connection populated from the previous lab. Select **Integrations** in the menu bar to the left.

    ![Menu options for integration](images/integration-menu.png) 

2. Select **Create** to begin the process.

    ![Create button for integration](images/create-integration.png) 

3. Select **App Driven Orchestration** from the available integration styles and click **Select** to continue.

    ![Integration Styles menu](images/app-driven-orchestration.png) 

6. Fill out the form as such:

    ```
    Name: BalanceTransferIntegration
    Identifier: BALANCETRANSFERINTEGRATION (auto-populated)
    Version: 01.00.0000
    ```

    Select **Create** to proceed to next step.

    ![Integration Properties options](images/integration-properties.png) 

## Task 2: Create Sample REST Endpoint

7. Select the **Sample REST Endpoint** Trigger to configure the endpoint.
   
    ![Integration pipeline starting endpoint](images/begin-integration.png) 

8. Give a name for the endpoint and click **Next** to continue.
   
    ![Integration pipeline starting endpoint](images/endpoint-basic-info.png) 

9.  Fill out the information for the resource configuration as such:
    
    ```
    What does this operation do: calling the chaincode function (optional)
    What is the endpoint's relative resource URI: /invocation
    What action do you want to perform on the endpoint: POST
    ```

    Select the tick-boxes for:

    ```
    Configure a request payload for this endpoint
    Configure this endpoint to receive the response
    ```
   
    ![Integration pipeline starting endpoint](images/resource-configuration.png) 

## Task 3: Declare JSON Payload for REST

10. Select **JSON Sample** for the request payload format and then, click **inline** to enter sample JSON. 

    ![Configure REST endpoint JSON](images/configure-rest-endpoint.png) 

11. Copy and paste the following sample JSON payload for the request:

    ```
    <copy>
    {
     "channel": "x",
     "chaincode": "x",
     "method": "x",
     "scalararg":"a",
     "chaincodeVer": "x"
    }
    </copy>
    ```

12. Select **JSON** for the media type to receive and then select **Next.** 

    ![Next Request option screen](images/next-json-format.png) 

## Task 4: Declare Response JSON for REST

13. Select **JSON Sample** for the request payload format and then, click **inline** to enter sample JSON. 

    ![Configure Response REST endpoint](images/json-response.png)

14. Copy and paste the following sample result payload for the request:

    ```
    <copy>
    {
    "returnCode": "x",
    "result": {
    "payload": "x",
    "message": "",
    "encode": "x"
    },
    "txid": "x"
    }
    </copy>
    ```

    ![Result payload input](images/sample-json-response.png) 

15. Select **JSON** for the media type to receive and then select **Next.** 

    ![Next Request option screen](images/next-json-format.png) 

16. On the summary page, select **Done** to finish the configuration.

    ![Summary of configuration](images/endpoint-summary.png) 

## Task 5: Create OBP Balance Transfer Invocation

1. Hover the mouse over the line connecting the Invocation to Map to Invocation. Click the **Plus sign** that appears and select the **OBPBalanceTransfer.

    ![Integration mapping page with additional invocation](images/add-invocation.png) 

2. Fill out the following on the basic information page:
    
    ```
    What do you want to call your endpoint: InvocationToBlockchain
    What is the endpoint's relative resource URI: /invocation
    What action do you want to perform on the endpoint: POST
    ```

    Select the tick-boxes for:

    ```
    Configure a request payload for this endpoint
    Configure this endpoint to receive the response
    ```

    ![Basic information of invocation](images/invocation-basic-info.png) 

    Select **Next** to proceed to next step.

## Task 6: Declare JSON payload for OBP

1. Select **JSON Sample** for the request payload format and then, click **inline** to enter sample JSON. 

    ![Configure invocation request](images/invocation-request.png)

2. Copy and paste the following jason payload for the actual values:

    ```
    <copy>
    {
    "channel": "x",
    "chaincode": "x",
    "method": "x",
    "args":["a"],
    "chaincodeVer": "x"
    }
    </copy>
    ```

    Select **OK** to proceed.

    ![JSON payload input](images/json-request.png) 

## Task 7: Declare response JSON payload for OBP

1. Select **Next** to proceed to response payload.

   ![Next JSON request](images/next-json-request.png) 

22. Do the same for the response payload, using the following:

    ```
    <copy>
    {
    "returnCode": "x",
    "result": {
    "payload": "x",
    "message": "",
    "encode": "x"
    },
    "txid": "x"
    }
    </copy>
    ```

    Click **OK** and **Next** to proceed to summary.

   ![Next JSON request](images/next-response-payload.png) 

   ![Next JSON request](images/response-payload.png) 

23. Select **Done** on the summary screen.

   ![Invocation Summary](images/invocation-summary.png) 

## Task 8: Map to Invocation from Sample REST Endpoint

1. In order to create a mapping between REST endpoints, click the top (or left - if horizontal) **Map to Invocation** and select the **pencil icon**  

   ![Pipeline mapping option](images/pipeline-mapping.png) 

2. On the mapping page, select the **drop-down arrows** of each request wrappers and draw a line from each of the mappings:

    ```
    -Channel
    -Chaincode
    -method
    -scalararg
    -chaincodeVar
    ```

   ![Mapping from source to target](images/mapping.png) 

Select **Validate** and then **Close** to proceed.

## Task 9: Map to Invocation from OBP Balance Transfer Endpoint

1. Select the bottom **Map to invocation** and click the **pencil icon.**

   ![Mapping from source to target](images/map-to-invocation.png)

2. On the mapping page, similar to before, select the **drop-down arrows** of each request wrappers (Instead, this time for the first REST option in source) and draw a line from each of the mappings:

    ```
    -returnCode
    -payload
    -message
    -encode
    -txid
    ```

   ![Mapping from source to target](images/source-target-mapping.png) 

Select **Validate** and then **Close** to proceed.

## Task 10: Add Tracking

1. On the pipeline page, select the hamburger menu at the top right and click **Tracking.**

   ![Hamburger menu tracking option](images/tracking-menu.png) 

2. Drag **Channel** from the left side onto the blank field on the first line.

   ![Mapping from source to target](images/channel-tracking.png) 

3. On the integration page, select **Save** and **Close** 

   ![Mapping from source to target](images/save-integration.png) 

## Task 11: Activate Integration

1. Click on the **Pushbutton** icon to activate the integration. 

   ![Pushbutton for activation](images/push-button.png)

2. Select **Enable Asserter Recording,** **Enable tracing,** and **include payload** plus **Activate** to proceed. Wait for confirmation, when the status changes to active you are ready to proceed to next lab.

   ![Activate integration](images/enable-tracing.png)

## Acknowledgements

- **Author**- Nicholas Cusato, Santa Monica Specialists Hub, September 2022
- **Contributers**- Jens Lusebrink, Christophe Peytier
- **Last Updated By/Date** - Nicholas Cusato, September 1, 2022