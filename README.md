# Exp 6: Jenkins CI Pipeline with Maven

## Prerequisites

- Java 11+
- Maven 3.6+
- Git
- Jenkins with the following plugins:
  - Pipeline
  - Maven Integration

---

## Git Setup Commands

```bash
git config --global user.email "your@email.com"
git config --global user.name "YourName"
git init
git add .
git commit -m "first Maven project for Jenkins"
git remote add origin git@github.com:yourusername/exp6-jenkins-ci
git config --global push.autoSetupRemote true
git push origin main
```

---

## SSH Key Generation

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

Add the contents of `~/.ssh/id_ed25519.pub` to your GitHub account under **Settings → SSH and GPG keys**.

---

## Jenkins Job Setup

1. Open [http://localhost:8080](http://localhost:8080) in your browser.
2. Click **New Item**, name it `Maven-CI`, select **Pipeline**, and click **OK**.
3. Scroll to the **Pipeline** section and paste the contents of `Jenkinsfile` into the **Pipeline script** box.
4. Check **Use Groovy Sandbox** → click **Save**.
5. Click the **play button / Build Now** on the dashboard.
6. Click the build number → **Console Output** → verify `BUILD SUCCESS`.

> **Before running the Jenkins job**, update the `url` field in `Jenkinsfile` with your actual GitHub repository URL.

---

## Test Locally Before Pushing

```bash
# Compile the project
mvn compile

# Run tests
mvn test

# Package into a JAR
mvn package

# Run the app
java -cp target/my-app-1.0-SNAPSHOT.jar com.coll.cmrit.App
```

Expected output: `Hello from Jenkins CI!`
