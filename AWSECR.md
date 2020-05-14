# Building docker image of the projects and pushing it to AWS ECR

Our EKS deployment consists of running containers with docker images of the care project. The images will be served from a private container registry service provided by AWS called Elastic Container Registry (ECR). To setup the repositories for your care frontend and backend images, head over to AWS ECR console and create a new repository **each** for the backend and frontend.

### Build image

To build the docker image of the care project, first clone the repositories:

`$ git clone https://github.com/coronasafe/care`  
`$ git clone https://github.com/coronasafe/care_fe`

Inside the directory of the project you want to build, use the docker build command for building your required images.

Eg.: If you are in the backend folder, run `$ docker build -t care:latest .`

After the creation of the image, you can verify it by running `$ docker images`

### Push the image to AWS ECR

* Visit the ECR console.
* Select the repository you want to push your image to.
* On the top right corner, you should be able to find `View push commands`
* Follow the steps there to push your docker image to AWS ECR.