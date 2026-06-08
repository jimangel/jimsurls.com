# CHECK / LIST CONFIGS:
gcloud config configurations list
gcloud config configurations activate <CONFIG_NAME>

# CREATE A CONFIG
gcloud config configurations create <CONFIG_NAME>
gcloud config set project <PROJECT_NAME>
gcloud config set account <ACCOUNT_NAME>
gcloud services enable compute.googleapis.com
gcloud config set compute/region us-central1
gcloud config set compute/zone us-central1-a

# IMPERSONATE SERVICE ACCOUNTS
gcloud config set auth/impersonate_service_account ${_SA_EMAIL}

# LOGIN / SWITCH PROJECTS
gcloud auth login
gcloud config set project <PROJECT_ID>

# LIST / USE GKE CLUSTERS
export GKE_NAME=
gcloud container clusters list
gcloud container clusters get-credentials $GKE_NAME
gcloud container clusters create $GKE_NAME --num-nodes 1 --machine-type e2-standard-4 --enable-ip-alias
# optional: --workload-pool=PROJECT_ID.svc.id.goog

# ENABLE SERVICES
gcloud services enable container.googleapis.com

# COPY DATA BETWEEN GCS BUCKETS
gcloud transfer jobs create --overwrite-when=always {src} {dst}

# Serverless Gemma 3n with Ollama and Cloud Run in two commands:
gcloud run deploy --image ollama/ollama --port 11434 --gpu 1 
OLLAMA_HOST=[...]  ollama run gemma3n 
