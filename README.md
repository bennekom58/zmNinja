# Bewaking58
This is a forked version of [zmNinja](https://github.com/pliablepixels/zmNinja) application, modified and customized for personal purposes. Please do not use this repo, instead check the original app which is great and supported!

## Compiling
This was done using Debian 8.1 Jessie 64bit:

1. **Linux basics for building form source:**
```bash
sudo apt-get install build-essential git curl
```

2. **Java Development Kit and Runtime Environment (from backports):**
```bash
echo -e "\ndeb http://http.debian.net/debian jessie-backports main" | sudo tee -a /etc/apt/sources.list && sudo apt-get update && sudo apt-get install -t jessie-backports openjdk-8-jdk && sudo update-java-alternatives --set java-1.8.0-openjdk-amd64 && java -version
```

3. **NodeJS v6.11.2:**
```bash
wget https://deb.nodesource.com/node_6.x/pool/main/n/nodejs/nodejs_6.11.2-1nodesource1~jessie1_amd64.deb && sudo dpkg -i nodejs_6.11.2-1nodesource1~jessie1_amd64.deb && nodejs -v
```

4. **NPM v5.8.0:**
```bash
sudo npm install -g npm@5.8.0 && npm -v
```

5. **Avoid NPM sudo-hell:**
```bash
mkdir -p ~/.npm-packages/bin && npm config set prefix ~/.npm-packages && npm list -g --depth=0 && echo -e "\nexport PATH=$HOME/.npm-packages/bin:\$PATH" >> ~/.bashrc && source ~/.bashrc
```

6. **Cordova, iONIC, Bower (also set backend to legacy):**
```bash
npm install -g cordova ionic bower && ionic config set -g backend legacy && ionic info
```

7. **Some more build-requirements (gulp, node-sass, async, jshint):**
```bash
npm install -g gulp && npm install node-sass async jshint
```

8. **Apache Maven 3.1.1:**
```bash
wget http://apache.hippo.nl/maven/maven-3/3.1.1/binaries/apache-maven-3.1.1-bin.tar.gz && sudo tar -zxf apache-maven-3.1.1-bin.tar.gz -C /usr/local && sudo mv /usr/local/apache-maven-3.1.1 /usr/local/maven && echo -e "\nexport M2_HOME=/usr/local/maven\nexport M2=\$M2_HOME/bin\nexport MAVEN_OPTS=\"-Xms256m -Xmx512m\"\nexport PATH=\$M2:\$PATH" >> ~/.profile && source ~/.profile && mvn -v
```

9. **Android SDK+Platform 23 with GoogleApi & Play:**
```bash
wget https://dl.google.com/android/repository/sdk-tools-linux-3859397.zip -O sdk-tools-linux.zip && mkdir -p ~/android/sdk && unzip sdk-tools-linux.zip -d ~/android/sdk/ && echo -e "\nexport ANDROID_HOME=$HOME/android/sdk\nexport PATH=$HOME/android/sdk/tools/bin:$HOME/android/sdk/platform-tools:\$PATH" >> ~/.bashrc && source ~/.bashrc && sdkmanager "platform-tools" "platforms;android-23" "add-ons;addon-google_apis-google-23"  "extras;google;google_play_services" && sdkmanager update
```

10. **Gradle 4.6:**
```bash
sudo wget https://services.gradle.org/distributions/gradle-4.6-bin.zip -O /opt/gradle-4.6-bin.zip && sudo unzip /opt/gradle-4.6-bin.zip -d /opt && echo -e "\nexport GRADLE_HOME=/opt/gradle-4.6\nexport PATH=/opt/gradle-4.6/bin:\$PATH" >> ~/.bashrc && source ~/.bashrc && gradle -v
```

9. **Prepare the build:**
```bash
cordova prepare
``` 

### Android
2. **Build the `.apk`:**
```bash
ionic cordova build android
```

### Desktop
Here comes the steps for building the desktop app...
