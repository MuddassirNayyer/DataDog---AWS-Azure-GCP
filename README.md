# Aws, Azure, and GCP VM DataDog agent setup

## DataDog Agent Installation command for AWS, AZURE and GCP

#### To get your DataDog API Key [Click Here](https://app.datadoghq.com/account/settings#api)

<pre><code>
DD_AGENT_MAJOR_VERSION=7 DD_API_KEY=<Your DataDog API KEY> bash -c "$(curl -L https://raw.githubusercontent.com/DataDog/datadog-agent/master/cmd/agent/install_script.sh)"
</code></pre>

#### Note: This command works seamlessly for AWS but some times causes issue for Azure and GCP, So you may follow other method to install datadog agent in for Azure and GCP

## Azure Data dog Agent Setup
1. In the Azure portal, navigate to your VM -> Settings -> Extensions -> Add and select Datadog Agent.
2. Click Create, enter your Datadog [API key](https://app.datadoghq.com/account/settings#api), and click OK.

## GCP Data dog Agent Setup
