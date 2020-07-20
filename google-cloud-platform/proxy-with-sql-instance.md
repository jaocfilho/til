<h1>Communicating with Cloud SQL using a local copy of Cloud SQL Proxy</h1>

<p>Before using Cloud SQL, you must enable the Cloud SQL Admin API
</p>

    gcloud services enable sqladmin

<p>The next step is install the Cloud SQL Proxy, the Cloud SQL Proxy connects to your Cloud SQL instance when running locally.
</p>

    # Download the proxy(changes for each OS):
    wget https://dl.google.com/cloudsql/cloud_sql_proxy.linux.amd64 -O cloud_sql_proxy

    # Make the proxy executable:
    chmod +x cloud_sql_proxy

<p>Assuming that you already have a Cloud SQL instance, use the following command to show the value of your instance <code>connectionName</code>.
</p>

    gcloud sql instances describe [YOUR_INSTANCE_NAME] | grep connectionName

<p>Note that <code>connectionName</code> value is in the format [PROJECT_NAME]:[REGION_NAME]:[INSTANCE_NAME].
</p>
<p>Now to start the Cloud SQL Proxy, use the connectionName from the previous step.
</p>

    # Port 3306 for a MySQL instance and 5432 for a PostgreSQL one.
    ./cloud_sql_proxy -instances="[YOUR_INSTANCE_CONNECTION_NAME]"=tcp:5432

<p>This step establishes a connection from your local computer to your Cloud SQL instance for local testing purposes. Keep the Clous SQL Proxy running the entire time you test your app locally.
</p>
<p>Source: https://cloud.google.com/python/django/appengine#deploying_the_app_to_the_standard_environment_
</p>