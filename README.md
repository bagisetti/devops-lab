# DevOps-lab

This project contains all my local DevOps practice setups, including Jenkins, LocalStack, Etcd, and various sample pipeline projects.

---

## Folder Structure

```bash
❯ tree -L 3 --gitignore
.
├── etcd
│   └── etcd-data
│       └── docker-compose.yml
├── jenkins
│   ├── agent-node-python
│   │   └── Dockerfile
│   ├── docker-compose-minimalist.yml
│   ├── docker-compose.yml
│   └── Dockerfile
├── localstack
│   └── localstack-volume
│       └── docker-compose.yml
├── projects
│   ├── fullstack-angular-lambda
│   │   ├── cloudformation
│   │   ├── docker
│   │   ├── Jenkinsfile
│   │   ├── pipeline.yaml
│   │   ├── README.md
│   │   └── scripts
│   ├── simple-pipeline-yaml
│   │   ├── Jenkinsfile
│   │   ├── Jenkinsfile-Parameterized
│   │   └── pipeline.yaml
│   └── zip-upload-to-s3
│       ├── artifact
│       ├── Jenkinsfile
│       └── pipeline.yaml
└── README.md

15 directories, 15 files
```

---

## How to Setup the Entire DevOps Lab

### 1. Prerequisites

- Docker
- Docker Compose
- Basic Git knowledge

---

### 2. Clone the Repository

```bash
git clone https://github.com/your-username/devops-lab.git
cd devops-lab
```

---

### 3. Jenkins Setup

#### 3.1 Build and Start Jenkins

```bash
cd jenkins
docker compose up -d --build
```

✅ **This will:**
- Build the Jenkins controller.
- Build custom Jenkins agents.
- Start services.
- Mount persistent volumes for Jenkins home.

---

#### 3.2 Access Jenkins

1. Open your browser and navigate to:  
   **[http://localhost:8080](http://localhost:8080)**

✅ **Default behavior:**
- Jenkins is ready.
- Agents (`agent1`, `agent2`) connect automatically after startup, with retries if the master is not ready.

---

### 4. LocalStack Setup (Mock AWS)

```bash
cd localstack
docker compose up -d
```

✅ **This will:**
- Start LocalStack and mock AWS services locally (S3, Lambda, etc).

---

### 5. Etcd Setup

```bash
cd etcd
docker compose up -d
```

✅ **This will:**
- Start a local Etcd cluster, useful for distributed coordination practice.

---

## Important Notes

- Do not push `jenkins/jenkins_home/` or `localstack/localstack-volume/` folders.
- `.gitignore` is properly set to avoid accidental Git tracking.
- All important artifacts are outside these runtime folders.

---

## Tips and Troubleshooting

- **Jenkins Agents**: If agents fail to connect immediately, they will retry until the master is available.
- **Performance**: If builds are slow, ensure the Docker daemon has enough CPU/memory assigned.
- **Cleanup**: Always run `docker compose down -v` to clean volumes when resetting the setup fully.

---