# SlackUp Jenkins – Trigger Jenkins from Slack (/build) + CI alerts

This project connects **Slack** and **Jenkins** so that developers can trigger builds directly from Slack using a slash command (`/build dev|qa|prod`) and get real-time notifications (🚀 start, ✅ success, 📎 console link) in the team channel.

---

## 🚀 Features
- Slack slash command `/build` triggers Jenkins pipeline
- Supports parameters: `dev | qa | prod`
- Jenkins posts build status and console URL back to Slack
- ChatOps style CI/CD for faster collaboration

---

## 🛠️ Tech Stack
- **Slack App** – Slash Commands, Bot User, Incoming Webhooks  
- **Jenkins** – Slack Notification plugin, Generic Webhook Trigger plugin  
- **ngrok** – expose Jenkins (localhost) to the internet securely  

---

## ⚙️ Setup
1. Create Slack app → add scopes (`chat:write`, `chat:write.public`, `commands`)  
2. Add Slash Command `/build` → point Request URL to Jenkins webhook endpoint  
3. Install app to workspace → copy Bot token (xoxb-…)  
4. Run `ngrok http 8080` → copy HTTPS forwarding URL  
5. Jenkins:
   - Install Slack Notification + Generic Webhook Trigger plugins  
   - Add Slack config (workspace = `devops-team`, default channel = channel ID, custom bot user ✅)  
   - Add pipeline job with Jenkinsfile (this repo)  
   - Enable Generic Webhook Trigger (token, JSONPath param for `SLASH_TEXT`)  
6. In Slack, `/invite @jenkins-ci` to the channel (`#ci-alerts`)  

---

## ▶️ Usage
In Slack `#ci-alerts` channel, type:
# slackup-jenkins
Slack + Jenkins CI/CD integration project
---

## 📂 Repo Structure
slackup-jenkins/
├── Jenkinsfile
├── README.md
└── docs/
    └── screenshots/   (to be added later)

