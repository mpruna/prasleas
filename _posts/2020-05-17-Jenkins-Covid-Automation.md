This project describes a data acquisition and analytics pipeline based on Jenkins, Python and Gogs (a private Github repo).
Jenkins, a CI/CD tool mostly used in DevOps, will automate the complete process. Python scripts will do the heavy lifting. When triggered by Jenkins the scripts will pull the data and generate the analytics.
Gogs will act both as Private and Public repository,
In this project I use COVID-19 public data-sets.

The rise of Corona-19 generated a lot of community initiatives to help fight pandemic.  
On the analytics side John Hopkins University did an admirable job. But there where also other good project.  
See the links below:

[**John Hopkins University**](https://coronavirus.jhu.edu/map.html)    
[**Italy**](https://www.bloccodigitale.com/)    
[**Siscale**](https://covid19.siscale.org/app/kibana#/)   
[**Romania**](https://covid19.geo-spatial.org/)   

Within this project I show how we can use Jenkins to:

* pull data-sets from public sources
* generate the analytics
* publish the analytics

### Project Workflow

![Img](../assets/img/jenkins_pipeline.png)

The workflow can be seen as a chained sequence of steps (build steps). Each successful build step triggers the next build. 

1. Data is available to the public.
2. A Jenkins job listens for new data, and based on a specific action (webhook trigger) it starts build job.
3. A Python script generates the analytics.
4. Analytics results are pushed to the public

### Jenkins architecture

Architecturally, Jenkins is fairly simple. Users of Jenkins create and maintain jobs, or projects. A project
is a collection of steps, also called builds. The term “Build” comes from Jenkins’ heritage as a build
automation system. “Building” software typically refers to the process of compilation, in which high-
level, human-written code is translated to machine code.

Jenkins organizes each project into it's home directory workspace.

### Jenkins directory tree

```jql
├── environment.yml
├── project_env.yml
├── requirements.txt
├── Generate_Analytics
│   ├── Images
│   └── README.md
├── Upload
│   ├── Images
│   ├── README.md
├── Webhook
│   ├── datasets
│   │   ├── getCasesByCounty.json
│   │   ├── getDailyCaseReport.json
│   │   ├── getDeadCasesByCounty.json
│   │   ├── getHealthCasesByCounty.json
│   │   └── romania-counties.json
```

### (1st Job) Pull data 

The first job listens for new data. This is done through a webhook trigger. When new data is available a notification is sent to Jenkins.
Jenkins pull the datasets.
The trigger is based on committed data to a public repo.
But this functionality must be configured.

#### Jenkins setup (Build job setup)


1. Click add new item
2. Choose freestyle project (name it) git it a name
3. In (Source Code Management) choose Git:
    * Repository URL (**add http repository url**): http://localhost:3000/gogs/COVID_Private_Repo.git
    * Choose gogs credentials
4. Build trigger:
    * Check (GitHub hook trigger for GITScm polling)
    

#### Gogs webhook setup:

1. Click Settings; Webhook  
2. Setup Payload URL ```http://localhost:8080/gogs-webhook/?job=Webhook``` 
3. Check (Webhook based on push event)
4. Activate is and test delivery

![Img](../assets/img/gogs_webhook.png)

### (2nd Job | Python Analytics)

1. Create a new job(see previous Jenkins steps 1 and 2)
2. In build section check [execute shell script]:

### Shell commands:
```
py="/home/anaconda3/envs/py37_covidenv/bin/python"
$bash
echo 'conda activate project_env'
home="/var/lib/jenkins/workspace/Generate_Analytics/code"
$py $home/analytics.py
```
The first line tells Jenkins where to look for the python version specific to our project.  
The second line activates the bash shell. Jenkins uses by default sh shell.   
The third line activates this particular python environment. Conda/Anaconda gives the user the opportunity to create "virtual python deployments". These "separated python mediums" can have different libraries.  
Home specifies the location of our code. The last line executes the script.

 
[Link to code](https://github.com/mpruna/Romania_COVID_Analytics/blob/master/code/analytics.py)

### Code breakdown
* the **read_data** function loads the data-sets into pandas dataframe objects.    
* **add_geodata** concatenates geographical coordinates.   
* **get_statistics** calculates the mean/standard deviation /minimum & maximum  values. 
* **fit_fit_4fbprohpet** makes the necessary transformations on the data. The forecasting function requires a two column dataframe.  The ds column represents the day number, and y represents the actual count.  
* **fit_4timeseries** transforms time series data into lists. This manipulation is necessary for the time series plotting function. The series graphs (confirmed;recovered;dead numbers).    
* **plot_map** draws the number Romania map. Color intensity is proportional with count number.  
* **scatter_plot** draws time series data.    
* **forecast_model** does a 22 day forecast.  



 
 
