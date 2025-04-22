# Medical-Chatbot-Generative-AI 💡

A professional-grade medical chatbot application powered by Generative AI, designed to provide intelligent and context-aware responses for medical inquiries. This project leverages **LangChain**, **Flask**, and **Google Gemini** models, with **Pinecone** for efficient vector storage and retrieval.

---

## ✨ Features

- Interactive medical chatbot powered by Google's Gemini model 🩺
- Retrieval-Augmented Generation (RAG) for context-aware responses 📚
- Stores embeddings in Pinecone for fast and efficient retrieval ⚡
- Built with Flask for seamless web deployment 🌐
- CI/CD integration with AWS and GitHub Actions 🚀

---

## 🛠️ Tech Stack

- **Python** 🐍
- **LangChain** 🔗
- **Flask** 🌍
- **Google Gemini (Generative AI)** 🤖
- **Pinecone** 📦

---

## 📋 Prerequisites

Before you begin, ensure you have the following:

- Python 3.10 🐍
- Conda (for environment management) 🧩
- Pinecone and Google API credentials 🔑
- Docker (for deployment) 🐳
- AWS account (for CI/CD deployment) ☁️

---

## 🚀 How to Run Locally

### Step 1: Clone the Repository 📥

```bash
git clone https://github.com/<your-repo>/Medical-Chatbot-Generative-AI.git
cd Medical-Chatbot-Generative-AI
```

### Step 2: Create a Conda Environment 🖥️

```bash
conda create -n medibot python=3.10 -y
conda activate medibot
```

### Step 3: Install Dependencies 📦

```bash
pip install -r requirements.txt
```

### Step 4: Configure Environment Variables ⚙️

Create a `.env` file in the root directory and add your credentials:

```ini
PINECONE_API_KEY="your-pinecone-api-key"
GOOGLE_API_KEY="your-google-api-key"
```

### Step 5: Store Embeddings in Pinecone 📈

Run the script to store embeddings:

```bash
python store_index.py
```

### Step 6: Launch the Application 🌟

Start the Flask server:

```bash
python app.py
```

### Step 7: Access the Chatbot 🌐

Open your browser and navigate to:

```
http://localhost:5000
```

---

## ☁️ AWS CI/CD Deployment with GitHub Actions

### Step 1: Log in to AWS Console 🔑

Access your AWS Management Console.

### Step 2: Create an IAM User for Deployment 🧑‍💻

1. Create an IAM user with the following permissions:
   - `AmazonEC2ContainerRegistryFullAccess`
   - `AmazonEC2FullAccess`
2. Save the `AWS_ACCESS_KEY_ID` and `AWS_SECRET_ACCESS_KEY`.

### Step 3: Create an ECR Repository 📦

1. Create an ECR repository to store your Docker image.
2. Note the URI (e.g., `970547337635.dkr.ecr.ap-south-1.amazonaws.com/medicalchatbot`).

### Step 4: Launch an EC2 Instance 💻

1. Create an EC2 instance (Ubuntu).

2. Install Docker on the EC2 instance:

   ```bash
   sudo apt-get update -y
   sudo apt-get upgrade
   curl -fsSL https://get.docker.com -o get-docker.sh
   sudo sh get-docker.sh
   sudo usermod -aG docker ubuntu
   newgrp docker
   ```

### Step 5: Configure EC2 as a Self-Hosted Runner 🏃

1. Navigate to your GitHub repository: `Settings > Actions > Runners`.
2. Add a new self-hosted runner, select the OS (Ubuntu), and follow the setup instructions on your EC2 instance.

### Step 6: Set Up GitHub Secrets 🔒

Add the following secrets in your GitHub repository (`Settings > Secrets and variables > Actions`):

- `AWS_ACCESS_KEY_ID`
- `AWS_SECRET_ACCESS_KEY`
- `AWS_DEFAULT_REGION` (e.g., `ap-south-1`)
- `ECR_REPO` (e.g., `970547337635.dkr.ecr.ap-south-1.amazonaws.com/medicalchatbot`)
- `PINECONE_API_KEY`
- `GOOGLE_API_KEY`

### Deployment Workflow 🛠️

1. Build the Docker image from the source code 🖼️
2. Push the Docker image to ECR 📤
3. Launch your EC2 instance 🚀
4. Pull the image from ECR to EC2 📥
5. Run the Docker image on EC2 🏃

---

## 📂 Project Structure

```
Medical-Chatbot-Generative-AI/
│
├── app.py                  # Main Flask application for the chatbot
├── store_index.py          # Script to store embeddings in Pinecone
├── templates/              # HTML templates for the web interface
│   └── chat.html           # Chatbot UI template
├── static/                 # Static assets (CSS, JS, etc.)
│   └── style.css           # Styling for the chatbot UI
├── requirements.txt        # Project dependencies
├── .env                    # Environment variables (not tracked in git)
├── README.md               # Project documentation (this file)
├── LICENSE                 # License file
└── .gitignore              # Git ignore file
```

---

## 🤝 Contributing

We welcome contributions! Follow these steps:

1. Fork the repository 🍴
2. Create a feature branch (`git checkout -b feature-branch`) 🌿
3. Commit your changes (`git commit -m "Add feature"`) 💾
4. Push to the branch (`git push origin feature-branch`) 📤
5. Create a Pull Request 📬

---

## 📜 License

This project is licensed under the MIT License. See the LICENSE file for details.

---

🌟 **Happy Coding!** 🌟
