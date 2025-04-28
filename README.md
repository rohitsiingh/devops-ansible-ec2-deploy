Of course, Rohit! Here's a professional and simple **README.md** you can use for your GitHub repository:

---

# EC2 Deployment with Ansible and GitHub Actions

This project demonstrates how to deploy a simple web application to an AWS EC2 instance using **Ansible automation**, **NGINX reverse proxy**, and **GitHub Actions** for continuous deployment.

---

## 🛠️ Setup Instructions

1. **Launch an EC2 Instance:**
   - Use Ubuntu 22.04 (or similar).
   - Open ports: **22 (SSH)**, **80 (HTTP)**.
   - Attach a key pair (.pem file) for SSH access.

2. **Clone the Repository:**
   ```bash
   git clone https://github.com/rohitsiingh/your-repo-name.git
   cd your-repo-name
   ```

3. **Configure Ansible Inventory:**
   - Update the `ansible/inventory` file with your EC2 public IP:
     ```
     [webservers]
     your-ec2-public-ip ansible_user=ubuntu ansible_ssh_private_key_file=your-key.pem
     ```

4. **Set up GitHub Secrets:**
   - In your GitHub repository, go to **Settings → Secrets → Actions**.
   - Add a secret named `SSH_PRIVATE_KEY` and paste the contents of your `.pem` file.

5. **GitHub Actions:**
   - A workflow file (`.github/workflows/main.yml`) is already set up.
   - On pushing to the `main` branch, GitHub Actions will trigger an Ansible deployment to your EC2 instance.

---

## 📋 Assumptions

- You have basic knowledge of AWS EC2, GitHub, and Ansible.
- EC2 Security Group allows inbound traffic on ports 22 and 80.
- You are using an Ubuntu-based EC2 instance with public IP access.
- You have administrative SSH access to the EC2 instance using a `.pem` private key.
- The application deployed is a basic HTML page for demonstration purposes.

---

## ✅ How to Test the Deployment

1. **Push a Commit:**
   - Make any code change (e.g., update `index.html`) and push to `main` branch.

2. **Monitor GitHub Actions:**
   - Go to your repo → **Actions tab**.
   - Watch the deployment pipeline run successfully.

3. **Access the Web App:**
   - Open your browser and visit:
     ```
     http://your-ec2-public-ip
     ```
   - You should see the deployed application served via **NGINX**.

4. **Verify NGINX Setup:**
   - SSH into your EC2 instance:
     ```bash
     ssh -i your-key.pem ubuntu@your-ec2-public-ip
     ```
   - Run:
     ```bash
     sudo systemctl status nginx
     ```
   - Ensure NGINX is running and serving on port 80.

---

## 📂 Project Structure

```
ansible/
  ├── inventory
  └── playbook.yml
.github/
  └── workflows/
      └── main.yml
app/
  └── index.html
README.md
```

---

