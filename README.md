<body>
    <h1>Simple DevOps Project - Deployment of 2048 Game on AWS using Docker</h1>

  <h2>Project Description</h2>

  <p>Welcome to a hands-on DevOps project where we take the classic game "2048" and bring it to life in the cloud using Docker and Amazon Web Services (AWS). In this journey, we will carefully walk through each step, from containerizing the game to effortlessly deploying it onto the AWS platform.</p>

  <img src="https://i.imgur.com/0SzgRpr.png" height="80%" width="80%" alt="2048 Game Screenshot"/>

</body>
</html>

<h3>The tools utilized in this project are as follows:</h3>
<ul>
  <li>Github</li>
  <li>Visual Studio Code</li>
  <li>Docker</li>
  <li>AWS - Elastic Beanstalk</li>
</ul>
<br />
<p align="center">

<h2>Step 1: Create a Docker File</h2>

<p>Open the terminal and execute the following commands:</p>

<pre><code># Create a new directory for your project
mkdir &lt;directory name&gt;

# Navigate to the newly created directory
cd &lt;directory name&gt;

# Open the project in Visual Studio Code
code .
</code></pre>

<p>After executing the commands, the Visual Studio Code window will open.</p>

<img src="https://i.imgur.com/qAVRTr2.png" height="80%" width="80%" alt="Terminal Screenshot"/>

<p>Create a file “Dockerfile” inside the created directory.</p>

<img src="https://i.imgur.com/wp6I4ra.png" height="80%" width="80%" alt="Dockerfile Creation"/>

<p>Next, type the following script:</p>

<pre><code># Dockerfile: Configure the Docker image for the 2048 game
FROM ubuntu:22.04

# Update package information
RUN apt-get update

# Install necessary dependencies: nginx, zip, and curl
RUN apt-get install -y nginx zip curl

# Configure Nginx to run in the foreground
RUN echo "daemon off;">>/etc/nginx/nginx.conf

# Download and extract the game files from GitHub
RUN curl -o /var/www/html/master.zip -L https://codeload.github.com/jabir000/2048/zip/master
RUN cd /var/www/html/ && unzip master.zip && mv 2048-master/* . && rm -rf 2048-master master.zip

# Expose port 80 for web traffic
EXPOSE 80

# Start Nginx with the specified configuration
CMD ["/usr/sbin/nginx", "-c", "/etc/nginx/nginx.conf"]
</code></pre>

<img src="https://i.imgur.com/Q8DNZbu.png" height="80%" width="80%" alt="Terminal Screenshot"/>

<p>In the new terminal, execute the following commands:</p>

<pre><code># Display the current working directory
pwd

# List the files and directories in the current directory
ls

# Build a Docker image with a specified name (replace &lt;docker image name&gt; with your desired name)
docker build -t &lt;docker image name&gt; .
</code></pre>

<img src="https://i.imgur.com/auHoNLl.png" height="80%" width="80%" alt="Terminal Screenshot"/>

<img src="https://i.imgur.com/26x4zqI.png" height="80%" width="80%" alt="Terminal Screenshot"/>

<pre><code># Start a Docker container in detached mode and map host port 80 to container port 80
docker run -d -p 80:80 &lt;container id&gt;
</code></pre>

<img src="https://i.imgur.com/ylyaISA.png" height="80%" width="80%" alt="Game Running"/>

<img src="https://i.imgur.com/ZCNcup5.png" height="80%" width="80%" alt="Game Running"/>

<p>The container has been successfully created.</p>

<p>To verify if the game is functioning correctly, access it via localhost on port 80.</p>

<img src="https://i.imgur.com/n45axHQ.png" height="80%" width="80%" alt="Game Running"/>

<h2>Deploying to AWS using Elastic Beanstalk</h2>

<p>AWS Elastic Beanstalk is a fully managed Platform as a Service (PaaS) offering from Amazon Web Services.</p>

<p>It simplifies the deployment and management of web applications and services in the cloud.</p>

<p>With support for various programming languages and platforms, developers can easily upload their code and let Elastic Beanstalk handle the provisioning and scaling of the infrastructure.</p>

<p>The service automatically monitors application health and performs auto-scaling to adjust resources based on demand.</p>

<p>This enables developers to focus on building their applications without worrying about the underlying infrastructure complexities.</p>

<h3>Step 1: Create an Application</h3>

<img src="https://i.imgur.com/QPLUjNf.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 2: Select Web Server Environment</h3>

<img src="https://i.imgur.com/E12mPrc.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 3: Give a Name to the Application</h3>

<img src="https://i.imgur.com/t8AR5eR.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 4: Give a Name to the Environment and Provide a Description</h3>

<img src="https://i.imgur.com/ADaFyjB_d.webp?maxwidth=760&fidelity=grand" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 5: Choose Platform Type as Managed Platform and Platform as Docker</h3>

<img src="https://i.imgur.com/5G96c0g.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 6: In this Section, Choose the Option to Upload Your Code and Upload the Docker File You Created</h3>

<img src="https://i.imgur.com/iEnIOxW.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 7: Choose the Free Tier Eligible Option</h3>

<img src="https://i.imgur.com/kFY7bEX.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 8: Skip to Review & Submit</h3>

<img src="https://i.imgur.com/QMw5LGi.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 9: The Environment Creation Has Been Initiated</h3>

<img src="https://i.imgur.com/btuo5uR.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<h3>Step 10: Once the Environment Creation Is Successful, Load the Domain</h3>

<img src="https://i.imgur.com/yHi3uVf.png" height="80%" width="80%" alt="AWS Console Screenshot"/>

<p><b>The game has been successfully deployed to AWS.</b></p>

<br />
<br/>
<p><b>~Hassanat Hussain</b></p>
<!--
 ```diff
- text in red
+ text in green
! text in orange
# text in gray
@@ text in purple (and bold)@@

