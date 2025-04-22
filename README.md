Medical Chatbot Generative AI
A medical chatbot powered by Generative AI using Google's Gemini model, LangChain, Flask, and Pinecone for vector storage. This chatbot provides answers to medical queries by leveraging Retrieval-Augmented Generation (RAG).
Project Structure

app.py: Main Flask application file containing routes and chatbot logic.
init.py: Initialization script for dependencies.
helper.py: Utility functions for the chatbot.
prompt.py: Custom prompt templates for the chatbot.
store_index.py: Script to store embeddings in Pinecone.
style.css: Stylesheet for the chatbot UI.
templates/chat.html: HTML template for the chatbot interface.
.env: Environment file for API keys (Pinecone and OpenAI).
requirements.txt: List of Python dependencies.
Dockerfile: Docker configuration for containerization.
LICENSE: Project license file.

Tech Stack

Python
LangChain
Flask
Google Gemini (Generative AI)
Pinecone (Vector Database)

How to Run?
Prerequisites

Python 3.10
Conda (for environment management)
Pinecone and OpenAI API keys
Docker (for containerized deployment)

Steps
1. Clone the Repository
git clone https://github.com/<your-repo>/Medical-Chatbot-Generative-AI.git
cd Medical-Chatbot-Generative-AI

2. Create a Conda Environment
conda create -n medibot python=3.10 -y
conda activate medibot

3. Install Requirements
pip install -r requirements.txt

4. Configure Environment Variables
Create a .env file in the root directory and add the following:
PINECONE_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
OPENAI_API_KEY="xxxxxxxxxxxxxxxxxxxxxxxxxxxxx"

5. Store Embeddings in Pinecone
python store_index.py

6. Run the Application
python app.py

Open your browser and navigate to http://localhost:5000 to access the chatbot.
AWS CI/CD Deployment with GitHub Actions
1. Login to AWS Console

Access the AWS Management Console.

2. Create IAM User for Deployment

Create an IAM user with the following permissions:
AmazonEC2ContainerRegistryFullAccess
AmazonEC2FullAccess



3. Create ECR Repository

Create an ECR repository to store the Docker image.
Note the URI: 970547337635.dkr.ecr.ap-south-1.amazonaws.com/medicalchatbot

4. Launch an EC2 Instance

Create an EC2 instance (Ubuntu).

5. Install Docker on EC2
sudo apt-get update -y
sudo apt-get upgrade
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
sudo usermod -aG docker ubuntu
newgrp docker

6. Configure EC2 as a Self-Hosted Runner

In GitHub: Navigate to Settings > Actions > Runners > New self-hosted runner.
Select the OS (Ubuntu) and follow the instructions to configure the runner.

7. Set Up GitHub Secrets
Add the following secrets in your GitHub repository settings:

AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
AWS_DEFAULT_REGION
ECR_REPO
PINECONE_API_KEY
OPENAI_API_KEY

Deployment Workflow

Build the Docker image of the source code.
Push the Docker image to AWS ECR.
Launch the EC2 instance.
Pull the Docker image from ECR to EC2.
Run the Docker image on EC2.

License
This project is licensed under the terms specified in the LICENSE file.
