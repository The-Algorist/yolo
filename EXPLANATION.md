Choice of Image:
 - node: alpine :This is because the app is build on node, which requires npm resources. Also the node alpine image is 172mb and does not compromise on security, having 0 vulnerabilities.
 - 
Dockerfile directives used in the creation and running of each container.


Docker-compose Networking (Application port allocation and a bridge network implementation) where necessary.
  - given that the application contains a client and a backend container, they both need to be in communication thus I used a custom network built 
Docker-compose volume definition and usage (where necessary).
Git workflow used to achieve the task.
Successful running of the applications and if not, debugging measures applied.
Good practices such as Docker image tag naming standards for ease of identification of images and containers. 
There is a screenshot of your deployed image on DockerHub, clearly showing the version of the image