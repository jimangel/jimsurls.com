# CHECK / LIST CONFIGS:
gcloud config configurations list
gcloud config configurations activate <CONFIG_NAME>

# CREATE A CONFIG
gcloud config configurations create <CONFIG_NAME>
gcloud config set project <PROJECT_NAME>
gcloud config set account <ACCOUNT_NAME>
gcloud config set compute/region us-central1
gcloud config set compute/zone us-central1-a

# LOGIN / SWITCH PROJECTS
gcloud auth login
gcloud config set project <PROJECT_ID>

# LIST / USE GKE CLUSTERS
gcloud container clusters list
gcloud container clusters get-credentials <NAME>
gcloud container clusters create <NAME> --num-nodes 1 --machine-type e2-standard-4
  
# ENABLE SERVICES
gcloud services enable container.googleapis.com
