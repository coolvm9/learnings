

To authenticate to Google Cloud Platform (GCP) services in either Java or Python, you generally use a **Service Account Key** or **Application Default Credentials (ADC)**. Here’s how to set up and use both approaches in Java and Python.

  

**Step 1: Set Up a Service Account and Download Key File**

  

1. **Create a Service Account**:

• Go to the [GCP Console](https://console.cloud.google.com/).

• Navigate to **IAM & Admin > Service Accounts**.

• Click **Create Service Account** and give it a name and description.

2. **Assign Roles**:

• Assign roles based on the GCP services the application needs to access (e.g., “Storage Admin” for Google Cloud Storage access).

3. **Generate and Download a Key**:

• Under the service account’s details, select **Keys** and click **Add Key > Create New Key**.

• Choose **JSON** and download the key file to your machine.

4. **Set Environment Variable (Optional)**:

• Set the GOOGLE_APPLICATION_CREDENTIALS environment variable to the path of your JSON key file. This allows both Java and Python to use this key automatically.

  

export GOOGLE_APPLICATION_CREDENTIALS="/path/to/service-account-file.json"

  

  

  

**Authentication in Java**

  

**Using Google Cloud Client Libraries (Recommended)**

  

The Google Cloud Client Libraries for Java automatically handle authentication if the GOOGLE_APPLICATION_CREDENTIALS environment variable is set.

  

1. **Add Dependency** (if using Maven):

  

<dependency>

    <groupId>com.google.cloud</groupId>

    <artifactId>google-cloud-storage</artifactId>

    <version>2.1.0</version>

</dependency>

  

  

2. **Authenticate with the Client Library**:

  

import com.google.cloud.storage.Storage;

import com.google.cloud.storage.StorageOptions;

  

public class GcpAuthExample {

    public static void main(String[] args) {

        Storage storage = StorageOptions.getDefaultInstance().getService();

        System.out.println("Successfully authenticated to GCP Storage");

    }

}

  

  

  

**Explicitly Loading the Credentials**

  

If you prefer to load the credentials explicitly:

  

import com.google.auth.oauth2.ServiceAccountCredentials;

import com.google.cloud.storage.Storage;

import com.google.cloud.storage.StorageOptions;

import java.io.FileInputStream;

import java.io.IOException;

  

public class GcpAuthExample {

    public static void main(String[] args) throws IOException {

        Storage storage = StorageOptions.newBuilder()

                .setCredentials(ServiceAccountCredentials.fromStream(new FileInputStream("/path/to/service-account-file.json")))

                .build()

                .getService();

        System.out.println("Successfully authenticated to GCP Storage");

    }

}

  

**Authentication in Python**

  

**Using Google Cloud Client Libraries (Recommended)**

  

The Google Cloud Client Libraries for Python will also automatically use the GOOGLE_APPLICATION_CREDENTIALS environment variable.

  

1. **Install the Client Library**:

  

pip install google-cloud-storage

  

  

2. **Authenticate with the Client Library**:

  

from google.cloud import storage

  

def authenticate_to_gcp():

    client = storage.Client()

    print("Successfully authenticated to GCP Storage")

  

authenticate_to_gcp()

  

  

  

**Explicitly Loading the Credentials**

  

Alternatively, you can specify the credentials explicitly in Python:

  

from google.cloud import storage

from google.oauth2 import service_account

  

def authenticate_to_gcp():

    credentials = service_account.Credentials.from_service_account_file('/path/to/service-account-file.json')

    client = storage.Client(credentials=credentials)

    print("Successfully authenticated to GCP Storage")

  

authenticate_to_gcp()

  

**Summary**

  

• **Set the** GOOGLE_APPLICATION_CREDENTIALS **environment variable** to make authentication easier across both languages.

• **Use client libraries** whenever possible, as they simplify the authentication process.

• For Python, use pip to install the necessary libraries. For Java, add dependencies to your pom.xml or use gradle if applicable.