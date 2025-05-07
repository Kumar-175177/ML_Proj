Project 1: Target Voice Separation using Deep Neural Networks (VoiceFilter)
“I was part of the Data & AI team, where we worked on an audio-based project for speaker enhancement and separation. The core idea was to filter out target speaker audio from noisy input — like Google's VoiceFilter — useful for call centers, embedded devices, or ASR systems.

📥 1. Data Collection & Preprocessing:
I worked with a mixture of public datasets (like LibriSpeech, VoxCeleb) and synthetic noisy audio files generated using background noise overlays.

Initially, the clips were 3–4 seconds long, but I extended the samples to 30 seconds to improve real-world performance and train the model better.

I extracted Mel spectrograms as input features and paired them with speaker embeddings (d-vectors).

🧠 2. Model Building & Tuning:
I used the VoiceFilter architecture and fine-tuned the hyperparameters such as learning rate, batch size, and model layers.

I experimented on an NVIDIA RTX GPU locally (via PyTorch), and after several training cycles, I achieved Median SDR of 14.4 dB.

The final model was saved as a .pt file after validation on hold-out data.

📦 3. Containerization & Testing:
I created a Flask-based inference service with an API that takes noisy audio and outputs clean target voice.

This was Dockerized, and I ran tests locally and on a dev server to ensure output quality was consistent.

☁️ 4. Hybrid MLOps Deployment (Manual + AWS):
The Docker image was pushed to Amazon ECR, and the model .pt file was stored in Amazon S3.

I deployed the container as a real-time inference endpoint on SageMaker using a custom inference script.

For retraining or version control, I used SageMaker Model Registry so that each new training version could be easily tracked.

📊 5. Monitoring & Automation:
To monitor usage and model health, I used CloudWatch logs & metrics (latency, memory usage, response times).

CloudWatch Alarms were set for failures or performance drops.

I also manually logged inference results and did a monthly check to evaluate model drift.

🔁 6. Retraining Plan:
If new speakers were added or audio quality changed, I had a retraining pipeline:

Sync new data to S3,

Fine-tune model locally or via SageMaker Training Jobs,

Register new model version, and

Redeploy it using CI/CD (GitHub → GitHub Actions → SageMaker Deployment).

🐬 Project 2: Marine Animal Head and Body Detection (YOLOv4 + MHSA)
“This project focused on detecting head and body regions of marine animals from underwater videos, which are often blurry and low-contrast. We wanted a robust model to assist marine biologists in tagging animals without manual frame analysis.

📥 1. Data Collection & Annotation:
We collected thousands of underwater images from drone footage and submarine cameras.

I used CVAT for manual bounding box annotation, creating labels for head and body.

The dataset was uploaded to S3 for backup and versioning.

🧠 2. Model Development:
I modified YOLOv4 and added Multi-Head Self-Attention (MHSA) blocks to improve detection under noisy visuals.

Training was done locally on GPU using PyTorch with a batch size of 16 and image size of 608x608.

The final model achieved 82% mAP on the validation set and was saved as .pt.

📦 3. Containerization & API Interface:
I wrote an inference script using OpenCV and Flask to accept image input and return detected boxes with labels.

The app was containerized with Docker, and I tested locally and on a dev server.

☁️ 4. Hybrid MLOps Deployment:
I pushed the Docker image to ECR and stored the model in S3.

The model was deployed using:

Option 1: On-premise Kubernetes cluster with autoscaling and horizontal pods.

Option 2: SageMaker real-time endpoint for cloud-based usage.

In Kubernetes, I used Helm charts for deployment, and KEDA for scaling based on requests.

📊 5. Monitoring:
For Kubernetes, I used:

Prometheus for custom metrics like image size, inference time.

Grafana dashboards to visualize health and usage.

Liveness and readiness probes to ensure container health.

For AWS deployments, I relied on CloudWatch logs, latency metrics, and auto-scaling configurations for the SageMaker endpoint.

🔁 6. Retraining Workflow:
When new marine species were added or false positives increased:

New data was uploaded to S3,

I retrained the model either locally or with SageMaker training jobs,

And deployed the new version using a GitHub-triggered CI/CD pipeline.

✅ Summary of MLOps Workflow Common to Both Projects:
Stage	Tools/Tech
Data Storage	S3, CVAT for labeling
Model Training	Local GPU / SageMaker Training
Version Control	GitHub + SageMaker Model Registry
Containerization	Docker + ECR
Deployment	Flask API → Docker → K8s / SageMaker
Monitoring	Prometheus+Grafana / CloudWatch+Model Monitor
CI/CD	GitHub Actions for Docker Build + Deploy
Retraining	Manual + Automated with data upload triggers
