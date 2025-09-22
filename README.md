
# DevOps Self-Study Lab Project
![CI](https://github.com/andriysmyk/flask_docker_nginx_vagrant/actions/workflows/ci.yaml/badge.svg)
![Deploy](https://github.com/andriysmyk/flask_docker_nginx_vagrant/actions/workflows/deploy.yaml/badge.svg)


This project is a local full-stack DevOps lab built as part of my self-study journey.  
It demonstrates key DevOps concepts including containerization, reverse proxying, CI/CD automation, and self-hosted runners inside a Vagrant VM (Ubuntu 22.04).

> The app runs locally in a virtual machine and is automatically deployed via GitHub Actions CI/CD.

---

##  Tech Stack

- **Python + Flask** — Simple web application  
- **Docker + Docker Compose** — Containerized deployment  
- **Nginx** — Reverse proxy for the Flask app  
- **GitHub Actions** — CI/CD pipeline  
- **Vagrant + VirtualBox** — Ubuntu-based virtual machine  
- **SSH** — Secure deployment  

---

##  Project Structure

```
flask_docker_nginx_vagrant/
├── app/                  # Flask web app
│   ├── app.py
│   ├── __init__.py
│   └── requirements.txt
├── tests/                # Unit tests (pytest)
│   └── test_app.py
├── Dockerfile
├── docker-compose.yml
├── Vagrantfile
└── .github/workflows/ci.yml
```

---

##  Usage Instructions

### 1. Launch the VM

```bash
vagrant up
vagrant ssh
```

### 2. Run the App in Docker (inside the VM)

```bash
cd /vagrant
docker-compose up -d
```

- Flask app: [http://localhost:8000](http://localhost:8000)  
- Via Nginx: [http://localhost:8080](http://localhost:8080)  

---

##  CI/CD with GitHub Actions

On every push to the `main` branch:

- Python dependencies are installed  
- Tests are run with `pytest`  
- GitHub Actions SSH into the VM and redeploy containers

###  Example Deployment Step

```yaml
- name: Deploy to VM
  run: |
    ssh -o StrictHostKeyChecking=no vagrant@<VM_IP> << 'EOF'
      cd /vagrant
      docker-compose down
      docker-compose up -d --build
    EOF
```

- SSH keys are securely handled via GitHub Secrets

---

##  Project Goals

- Practice Infrastructure as Code (IaC)  
- Automate deployments with CI/CD  
- Simulate real-world DevOps workflows  
- Build confidence with Linux, Docker, and GitHub Actions  

---

##  Next Steps

- Integrate monitoring (Zabbix)  
- Add container healthchecks & alerts  
- Try deploying to a cloud platform (AWS / DigitalOcean)  

---


## 🤝 Let's Connect

I’m currently seeking DevOps opportunities in **London, UK 🇬🇧**.  
Feel free to reach out or leave feedback!

👉 [LinkedIn Profile](https://www.linkedin.com/in/andriysmyk)
