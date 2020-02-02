# Continuous Delivery of Flask Application on GCP
### Repository from the course 'Data Analysis in the Cloud at Scale (ECE.590.24)

## Project 1
#### Objectives

- Create a Google App Engine application using GCP Cloud Shell environment
- Push source code to Github
- Configure Cloud Build to Deploy Changes on build

---

For a short explanation of this project please watch the demo video on this [respository](./Demo_Continuous_Delivery_of_Flask_Application_on_GCP.mp4) or in [Youtube](https://youtu.be/8gUEr2N6Flg)

#### 1 Start creating a new project on Google Cloud Platform <br> 
![Create project](/Images/Slide1.JPG)

#### 2  Activate Cloud Shell and clone you repository.<br>
In this case we are using this exact repository. 
We are going to run a simple Flask application. Check `main.py` in order to see the different functions available in this app.<br>
> git clone git@github.com:joaquinmenendez/Cloud_Computing_Project_1.git

/* I am assuming that you have already set a SSH Key in your GitHub account. If not you can do it following this [steps](https://docs.cloudera.com/documentation/director/latest/topics/director_gcp_config_tools.html) 

#### 3 Set the current directory into the repo
> cd Cloud_Computing_Project_1

#### 4 Initialize App Engine
> gcloud app create

Google is going to ask in what area you would like to set your app. In my case I selected the area 12 us-central <br>

#### 5 Deploy the app to the web
`gcloud app deploy`

Updating the service will take some minutes the first time we deploy the app. <br>

#### 6 We need to enable certain services in order to run the script `main.py` and allow the communication between Github and Cloud Build

>Enable API Services
>![Enable API Services](/Images/Slide2.JPG 'Enable API Services')<br>

>Enable Cloud Natural Language API
>![Enable Cloud Natural Language API](/Images/Slide3.JPG 'Enable Cloud Natural Language API')<br>

>Enable App Engine Admin API
>![Enable App Engine Admin API](/Images/Slide5.JPG 'Enable App Engine Admin API')<br>

>Enable Cloud Build AP
>![Enable Cloud Build AP](/Images/Slide4.JPG 'Enable Cloud Build AP')<br>

>Grant permissions to Cloud Build to connect with App Engine
>![Grant permissions to Cloud Build to connect with App Engine](/Images/Slide6.JPG 'Grant permissions to Cloud Build to connect with App Engine')<br>

#### 7 Connect your repository with Cloud Build
>Linkng GitHub repo to Cloud Build
>![Linkng GitHub repo to Cloud Build](/Images/Slide7.JPG 'Linkng GitHub repo to Cloud Build')<br>

>Example of linked repository
>![Example of linked repository](/Images/Slide8.JPG 'Example of linked repository')<br>

#### 8 Open your app
`gcloud app browse`

In this case we will see a welcome message in our home page 'Hello World' <br>

>Initial home page
>![Initial home page](/Images/Slide9.JPG)

#### 9 Make some changes in our app

To check that our repository is correctly linked with our App I would made some modifications in this welcome message and I will push this changes in order to trigger a new deploy of my app.
I open `main.py` in a cloned repository my local machine and I modify the welcome message. After I am ok with the changes I commit and push `main.py` to the repository. <br>

> Pushing changes made locally on a file
> ![Pushing changes made locally on main.py](/Images/Slide10.JPG "Pushing changes made locally on main.py")

Cloud Build is going to detect this change and is going to deploy an updated version of my app. <br>
> Updated homepage
> ![Updated homepage](/Images/Slide11.JPG "Updated homepage")

