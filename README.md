# How to Install Apache Maven on Ubuntu 14.04/ 16.04

Sometimes it's too difficult to install some thing very simple in your machine, I was working on maven and one day my maven started creating errors once I uninstall it was very diffcult for me to reinstall maven. I have wasted complete day, so I have created the repository with complete steps for installing maven that worked for me... :) 
Hope it will help you too...


### Introduction

Apache Maven is a free and open source project management tool used for Java projects. You can easily manage a project's build, reporting, and documentation from a central piece of information using Apache Maven. Apache Maven provides a complete framework to automate the project's build infrastructure.

In this, you will learn how to install Apache Maven on Ubuntu 16.04.

### Prerequisites

*   A Ubuntu 14.04/ 16.04 server.
*   A non-root user with sudo privileges created on your server.

### Step 1: Update your server

First, update your system to the latest stable version by running the following command:

    sudo apt-get update -y
    sudo apt-get upgrade -y (not required)

### Step 2: Install Java( Ignore this step if already installed)

Apache Maven requires Java to be installed on your server. By default, Java is not available in Ubuntu's repository. Add the Oracle Java PPA to Apt with the following command:

    sudo add-apt-repository ppa:webupd8team/java

Next, update your Apt package database with the following command:

    sudo apt-get update -y

Install the latest stable version of Oracle Java 8.

    sudo apt-get install oracle-java8-installer

Verify the Java version by running the following command:

    java -version

Output:

    java version "1.8.0_91"
    Java(TM) SE Runtime Environment (build 1.8.0_91-b14)
    Java HotSpot(TM) 64-Bit Server VM (build 25.91-b14, mixed mode)

### Step 3: Install Apache Maven

You can download the latest stable version of Apache Maven from its official website, otherwise you can download it directly with the following command:

    cd /opt/
    wget http://www-eu.apache.org/dist/maven/maven-3/3.3.9/binaries/apache-maven-3.3.9-bin.tar.gz

Once the download has completed, extract the downloaded archive.

    sudo tar -xvzf apache-maven-3.3.9-bin.tar.gz

Next, rename the extracted directory.

    sudo mv apache-maven-3.3.9 maven 

### Step 4: Setup environment variables

Next, you will need to setup the environment variables such as `M2_HOME`, `M2`, `MAVEN_OPTS`, and `PATH`. You can do this by creating a `mavenenv.sh` file inside of the `/etc/profile.d/` directory.

    sudo nano /etc/profile.d/mavenenv.sh

Add the following lines:

    export M2_HOME=/opt/maven
    export PATH=${M2_HOME}/bin:${PATH}

Save and close the file, update its permissions, then load the environment variables with the following command:

    sudo chmod +x /etc/profile.d/mavenenv.sh
    sudo source /etc/profile.d/mavenenv.sh

### Step 5: Verify installation

Once everything has been successfully configured, check the version of the Apache Maven.

    mvn --version

You should see the following output:

    Apache Maven 3.3.9 (bb52d8502b132ec0a5a3f4c09453c07478323dc5; 2015-11-10T22:11:47+05:30)
    Maven home: /opt/maven
    Java version: 1.8.0_101, vendor: Oracle Corporation
    Java home: /usr/lib/jvm/java-8-oracle/jre
    Default locale: en_US, platform encoding: ANSI_X3.4-1968
    OS name: "linux", version: "3.13.0-32-generic", arch: "amd64", family: "unix"

Congratulations! You have successfully installed Apache Maven on your Ubuntu 14.04/ 16.04 server.
