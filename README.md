# Aws, Azure, and GCP VM DataDog agent setup

## DataDog Agent Installation command for AWS, AZURE and GCP

#### To get your DataDog API Key [Click Here](https://app.datadoghq.com/account/settings#api)

<pre><code>
DD_AGENT_MAJOR_VERSION=7 DD_API_KEY={Your DataDog API KEY} bash -c "$(curl -L https://raw.githubusercontent.com/DataDog/datadog-agent/master/cmd/agent/install_script.sh)"
</code></pre>

#### Note: This command works seamlessly for AWS but some times causes issue for Azure and GCP, So you may follow another method to install datadog agent in for Azure and GCP

## Azure Data dog Agent Setup
1. In the Azure portal, navigate to your VM -> Settings -> Extensions -> Add and select Datadog Agent.
2. Click Create, enter your Datadog [API key](https://app.datadoghq.com/account/settings#api), and click OK.

## GCP Data dog Agent Setup
1. Create a new [Cloud Pub/Sub](https://console.cloud.google.com/cloudpubsub/topicList)  

2. Setup the Pub/Sub to forward logs to Datadog  
Note: Use this as EndPoint while creating the subscription  
If VM is located in US: https://gcp-intake.logs.datadoghq.com/v1/input/<Data Dog API Key>/  
If VM is located in EU: https://gcp-intake.logs.datadoghq.eu/v1/input/<Data Dog API Key>/  

3. Configure exports from Stackdriver logs to the Pub/Sub  
3.1. Go to the [Stackdriver page](https://console.cloud.google.com/logs/viewer) and filter the logs that need to be exported  
3.2. Hit Create Sink and name the sink accordingly  
3.3. Choose Pub/Sub as the destination and select the Pub/Sub that was created for that purpose
