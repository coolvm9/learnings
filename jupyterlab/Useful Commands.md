
- This restarts IPython
import IPython
app = IPython.Application.instance()
app.kernel.do_shutdown(True)

Restart the kernet after libraries are loaded.


pip3 install --upgrade --user google-cloud-aiplatform

!pip3 install --upgrade --user google-cloud-aiplatform pymupdf


'# "COMPLETE THE MISSING PART AND RUN THIS CELL"

import sys

# Define project information and update the location if it differs from the one specified in the lab instructions.
PROJECT_ID = "qwiklabs-gcp-02-3ed7b92b2914"  # @param {type:"string"}
LOCATION = "europe-west4"  # @param {type:"string"}

# Try to get the PROJECT_ID automatically.
if "google.colab" not in sys.modules:
    import subprocess

    PROJECT_ID = subprocess.check_output(
        ["gcloud", "config", "get-value", "project"], text=True
    ).strip()

print(f"Your project ID is: {PROJECT_ID}")



https://github.com/GoogleCloudPlatform/training-data-analyst/blob/master/self-paced-labs/gemini/inspect_rich_documents_w_gemini_multimodality_and_multimodal_rag.ipynb'