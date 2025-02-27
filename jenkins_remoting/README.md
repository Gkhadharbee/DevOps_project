# <p align="">Jenkins Remoting Layer
## <p align="">About the project</p>
   This project establish a communication channel between the controller(master) and agents(Slaves) Nodes.
It is responsible for transmitting data, executing commands, and maintaining a stable connection between different components in a Jenkins setup.

## Overview  
* Remoting is a library used by Jenkins to establish a communication channel between the controller and agents.
* It operates over various transport protocols, such as JNLP, SSH, WebSockets, and direct TCP.
* Provides serialization and deserialization of Java objects across nodes.
* Used for running builds and executing commands on remote agents.

## Pre-requisites
* Understanding about the Jenkins Remoting
* Jenkins installation
* Jenkins Master Node & Agent or Slave Node
* Plugins installation
* Verify Agent Connectivity to the Controller
* Pipeline Job to use remote agents

## <p align="">Steps</p>

### <p align="">Step1:</p>

### <p align="">Understand Jenkins Remoting</p>
Jenkins Remoting is a library that enables communication between Jenkins master (controller) and agents (nodes). It allows executing build tasks on remote machines.

### <p align="">Step2:</p>

#### <p align="">Install and Configure Jenkins</p>
1. Download and Install Jenkins
2. Start Jenkins and set up an admin user.
3. Install Required Plugins
Go to Manage Jenkins → Manage Plugins.
Install the following:
* SSH Slaves Plugin (if using SSH-based agents).
* JNLP (Java Web Start) Agent Plugin (for remoting-based agents).

### <p align="">Step3:</p>

#### <p align="">Set Up Jenkins Agent (Node)</p>
1. Using JNLP (Java Web Start)
2. Go to Manage Jenkins → Manage Nodes.
3. Click on New Node, provide a name, and select Permanent Agent.
Configure:
* Remote Root Directory (e.g., /home/jenkins/ or C:\Jenkins\).
* Labels (optional).
* Usage: Keep as “Use this node as much as possible”.
* Launch method: Choose “Launch agent by connecting it to the master”.
* Save the node configuration.

### <p align="">Step4:</p>

#### <p align="">Download and Start the Jenkins Agent</p>
On the agent machine, open a terminal.
1. Download the agent.jar:

```bash
wget http://<JENKINS_URL>:8080/jnlpJars/agent.jar
```

2. Run the agent using the following command:

```bash
java -jar agent.jar -jnlpUrl http://<JENKINS_URL>:8080/computer/<NODE_NAME>/slave-agent.jnlp -secret <SECRET_KEY> -workDir "<WORK_DIRECTORY>"
```

3. Replace <JENKINS_URL>, <NODE_NAME>, and <SECRET_KEY> with actual values.
4. You can find the secret key under Manage Nodes → Select the Node.

### <p align="">Step5:</p>

#### <p align="">Verify Agent Connectivity</p>
1. Go to Manage Jenkins → Manage Nodes.
2. The node should be in Connected status.
3. Run a test job to verify it executes on the agent.

### <p align="">Step6:</p> 
1. Configure Jenkins Pipeline to Use Remote Agents
2. Create a new Pipeline Job in Jenkins.
3. Use the following pipeline script:

```bash
pipeline {
    agent {
        label 'remote-agent'
    }
    stages {
        stage('Build') {
            steps {
                echo 'Running on a remote agent!'
                sh 'hostname'
            }
        }
    }
}
```
Save and run the pipeline.

### <p align="">Step7:</p>

#### <p align="">Secure Jenkins Remoting</p>
* Use authentication with Jenkins credentials.
* Set up firewalls to allow only necessary traffic.
* Use SSH tunnels or VPNs for secure communication.
* Disable the remoting protocol when not in use (Manage Jenkins → Security Settings).

