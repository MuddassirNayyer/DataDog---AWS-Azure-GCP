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
1. If you haven’t already, set up the [Google Cloud platform integration first](https://docs.datadoghq.com/integrations/google_cloud_platform/?tab=datadogussite#installation)  

1.1. Navigate to the Google Cloud [credentials page](https://console.cloud.google.com/apis/credentials) for the Google Cloud project where you would like to setup the Datadog integration.  
1.2. Press Create credentials and then select Service account key  
1.3. In the Service account dropdown, select New service account  
1.4. Give the service account a unique name  
1.5. For Role, select Compute engine —> Compute Viewer, Monitoring —> Monitoring Viewer, and Cloud Asset —> Cloud Asset Viewer  

1.6. Select JSON as the key type, and press create. Take note where this file is saved, as it is needed to complete the installation  

1.7. Navigate to the Datadog [Google Cloud Integration tile]  (http://app.datadoghq.com/account/settings#integrations/google_cloud_platform)     

1.8. On the Configuration tab, select Upload Key File to integrate this project with Datadog  

2. Create a new [Cloud Pub/Sub](https://console.cloud.google.com/cloudpubsub/topicList)  

3. Setup the Pub/Sub to forward logs to Datadog  
Note: Use this as EndPoint while creating the subscription  
DataDog US Site: https://gcp-intake.logs.datadoghq.com/v1/input/<Data Dog API Key>/  
DataDog EU Site: https://gcp-intake.logs.datadoghq.eu/v1/input/<Data Dog API Key>/  

4. Configure exports from Stackdriver logs to the Pub/Sub  
4.1. Go to the [Stackdriver page](https://console.cloud.google.com/logs/viewer) and filter the logs that need to be exported  
4.2. Hit Create Sink and name the sink accordingly  
4.3. Choose Pub/Sub as the destination and select the Pub/Sub that was created for that purpose
