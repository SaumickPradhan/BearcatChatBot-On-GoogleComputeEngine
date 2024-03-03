# Deploy Flask App on Google Cloud Platform Compute Engine and Dialogue Flow CX

## Description
This project deploys a Python3 Flask Chat Bot with user authentication on a Google Cloud Platform (GCP) Compute Engine Virtual Machine (VM) Instance. It provides a quick guide to deploying a VM instance using GCP's infrastructure, running flask with **apache webserver** and **mod_wsgi** and setting up the chat bot with **Google Dialogue Flow CX**



## Preview
<img width="605" alt="image" src="https://github.com/SaumickPradhan/GCP-Project/assets/85262444/5f4a43f1-c7f4-45c7-bdb0-2ab9f25545ff">



<img width="257" alt="image" src="https://github.com/SaumickPradhan/BearcatChatBot-On-GoogleComputeEngine/assets/85262444/f7a1d50f-ca27-403f-9ab9-f1f9d5797c35">

## Running

Run using your external ip like 

```
http://<external IP>
```


## Prerequisites
Before you begin, ensure you have the following:
- A Google Cloud Platform account.
- The Google Cloud SDK installed and initialized.
- Set up Google Cloud Dialogue Flow CX


## Getting Started
1. Clone this repository:
    ```bash
    git clone https://github.com/SaumickPradhan/GCP-Project
    ```

2. Navigate to the project directory:
    ```bash
    cd project
    ```
    
  Follow the project directory to set up.

3. Ensure you have the necessary authentication set up for your Google Cloud account. If you haven't already done this, refer to the [Google Cloud SDK documentation](https://cloud.google.com/sdk/docs/quickstart) for instructions.

4. Set up your GCP project and enable the Compute Engine API. Refer to the [Google Cloud documentation](https://cloud.google.com/compute/docs/quickstart) for detailed instructions.

5. Update the `config.yaml` file with your desired VM instance configurations. This includes settings such as machine type, region, image, etc.

6. Once the deployment is complete, you can access your VM instance using SSH or any other preferred method.

7. Set up Dialogue Flow CX and add the intents and responses in the UI

## Setting up the instance

Now that we've connected to the instance, it's time to install some of the programs we'll need.

1. Install the apache webserver and mod_wsgi.

   ```bash
   $ sudo apt-get update
   $ sudo apt-get install apache2
   $ sudo apt-get install libapache2-mod-wsgi


### Enable mod_wsgi

The apache server displays html pages by default but to serve dynamic content from a Flask app we'll have to make a few changes. In the apache configuration file located at `/etc/apache2/sites-enabled/000-default.conf`, add the following block just after the `DocumentRoot /var/www/html` line:

```
WSGIDaemonProcess flaskapp threads=5
WSGIScriptAlias / /var/www/html/flaskapp/flaskapp.wsgi

<Directory flaskapp>
    WSGIProcessGroup flaskapp
    WSGIApplicationGroup %{GLOBAL}
    Order deny,allow
    Allow from all
</Directory>
```

## Contributing
Contributions are welcome! Please feel free to submit a pull request.

## License
This project is licensed under the [MIT License](LICENSE).

## Support
For support or inquiries, please contact me
