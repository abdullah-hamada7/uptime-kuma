# Frontend App (Uptime Kuma)

This is the frontend part of the project. It runs Uptime Kuma using Docker.

## Why I set it up this way

I had to make a few changes from a standard cloud setup because of some limitations.

### 1. Using Vagrant

I couldn't use AWS because my account is suspended (payment issues), and I don't have access to Azure or GCP. I tried LocalStack, but the free version doesn't support the accessing of EC2 instances.

So, I used **Vagrant** to make local virtual machines. This acts just like a real server but runs on my computer.

### 2. Using a Self-Hosted Runner

Since my "servers" are just Vagrant VMs on my laptop, GitHub can't reach them directly.

To fix this, I set up a **Self-Hosted Runner**. This is a small program that runs on my computer, connects to GitHub, and pulls the jobs down to run them locally where it can see the Vagrant VMs.

### 3. Using Ansible instead of Shell Scripts

The task asked for a shell script, but I used **Ansible** instead.

I did this because shell scripts can break easily if you run them more than once or if something unexpected happens. Ansible is safer—it checks if something is already done before trying to do it again. It's also the standard way to manage servers professionally.

---

## Quick Start

1. **Start the Server**:
    Run `vagrant up` in this folder. This starts the local server at `192.168.56.11`.

2. **Setup the Runner**:
    Go to your GitHub Repo > Settings > Actions > Runners and add a "Self-hosted runner" on your machine.

3. **Deploy**:
    Push to `main`. The workflow will trigger your local runner, which uses Ansible to deploy Uptime Kuma to the Vagrant VM.

## Setup Details

**Secrets Required:**

* `SSH_PRIVATE_KEY`: Your Vagrant SSH key.

![image](snapshot.png)
