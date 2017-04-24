# Redgate and Visual Studio 2017

<p align="center">
<img src="media/ReadyRoll.jpg"/>
</p>


## Demo Overview



In this demo, Donovan Brown, will show:

**High-level flow**

1.  Redgate Data Tools now available for FREE to all VSE users (in the
    VSE installer)

2.  Don’t let your database slow down your releases, develop and deploy
    your application and your database side-by-side in existing MS tools
    (VS, TFS/VSTS) using Redgate ReadyRoll

3.  Migrations shifts the creation of the database deployment script as
    far left as possible so that it can be reviewed and tested early
    (more control over deployments)

4.  SQL Prompt makes writing SQL code easier and smarter

## Rough Outline

Three of Redgate’s tools are now available to install in Visual Studio
Enterprise – Redgate ReadyRoll Core, Redgate SQL Prompt Core, and
Redgate SQL Search.

Now that BikeSharing360 has been live for a while, we want to start
thinking about maintenance of our bikes – Redgate ReadyRoll makes it
easy to make and deploy these changes. We’ll add a column to the bikes
table that lists the last date that a bike was serviced. We’ll use VSTS
to add these changes to source control, showing how easy it is to make
these deployments and show a preview of what changes will be made.

## Key Takeaways


1.  Don’t let your database slow down your releases, develop and deploy
    your application and your database side-by-side in existing MS tools
    (VS, TFS/VSTS) using Redgate ReadyRoll.

2.  ReadyRoll is an alternative to SSDT Database Projects that allows
    developers to have more control over the end database
    deployment script. ReadyRoll is a migrations-driven approach which
    shifts the creation of the database deployment script left so that
    it can be source controlled and tested early for fast feedback. This
    gives developers more control over exactly how database changes will
    be deployed to the different environments.

3.  SQL Prompt makes writing SQL code easier and smarter

## VSTS and Azure Configuration
For this demo, you will need a VSTS project with the correct code base and a build and release pipeline which compiles and deploys the 
redgate readyroll database project.  You will also need a private VSTS build and release agent hosted in Azure, as well as a database 
server and two Azure databases for the Dev and Prod deployment environments.

### Task 1: Create demo project in VSTS and import the code

1. Browse to your VSTS account and click New Project 

   <img src="media/2017-03-16_13-36-00.jpg" width="624" />
   
2. Give your project a name (RedgateDemoProj) and click Create

   <img src="media/2017-03-16_13-38-22.jpg" width="624" />
   
3. Click import a repository

   <img src="media/2017-03-16_13-42-31.jpg" width="624" />
   
4. Click Import button

   <img src="media/2017-03-16_13-47-15.jpg" width="624" /> 

5. Enter https://github.com/abelsquidhead/VS2017VSTSKeynoteDemo in the Clone URL text box and click Import

   <img src="media/2017-03-16_13-49-07.jpg" width="624" /> 
   
6. Wait for import to complete

   <img src="media/2017-03-16_13-50-47.jpg" width="624" /> 
   
### Task 2: Create private build and release agent for VSTS in Azure

This demo works best if you create your own private VSTS build and release agent.  The following steps describe how to 
create and configure your private agent in an azure VM. In order for the automated unit testing to work, you will also 
need to install VS2015.  The ReadyRoll tasks require .NET 3.5 installed as well.

1. Browse to your azure portal and select Virtual machines

   <img src="media/2017-03-16_13-58-28.jpg" width="624" /> 

2. Click Add

   <img src="media/2017-03-16_14-02-50.jpg" width="624" /> 

3. Enter Visual Studio in the search text box and select Visual Studio Enterprise 2017 on Windows Server 2016 (x64)

   <img src="media/2017-03-16_14-08-31.jpg" width="624" /> 

4. Select Visual Studio Enterprise 2017 on Windows Server 2016 (x64)

   <img src="media/2017-03-16_14-11-06.jpg" width="624" />
   
5. Click Create button

   <img src="media/2017-03-16_14-13-25.jpg" width="624" />

6. Give your VM a name, a user name, password, select your subscritpion, create a new resource group and select a location and click the OK button

   <img src="media/2017-03-16_14-17-07.jpg" width="624" />
   
7. Select DS2 and click Select button

   <img src="media/2017-03-16_14-20-23.jpg" width="624" />
   
8. Click the OK button

   <img src="media/2017-03-16_14-22-08.jpg" width="624" />
   
9. Click the OK button

   <img src="media/2017-03-16_14-24-34.jpg" width="624" />
   
10. Wait for the deployment to finish

    <img src="media/2017-03-16_15-06-28.jpg" width="624" />
	
11. Login to the VM by clicking on the Connect button

    <img src="media/2017-03-16_15-13-22.jpg" width="624" />
	
### Task 3: Configure the private VSTS build and release agent machine
To configure the private VSTS build and release agent, you will need to install SSMS, VS2015 (so unit tests will build correctly)
and download and configure the VSTS agent.

#### Installing Sql Server Management Studio and install VS2015
1. RDP into your agent machine using the username and password you picked when creating the VM

   <img src="media/2017-03-16_15-15-52.jpg" width="228" />
   
2. Open IE, browse to https://docs.microsoft.com/en-us/sql/ssms/download-sql-server-management-studio-ssms and 
click Download SQL Server Management Studio (16.5.3)

   <img src="media/2017-03-16_15-44-49.jpg" width="228" />
   
3. Click Run

   <img src="media/2017-03-16_15-46-03.jpg" width="228" />
   
4. Click Install

   <img src="media/2017-03-16_15-48-50.jpg" width="346" />
   
5. Wait for SSMS installation to finish, then click Close

   <img src="media/2017-03-16_16-00-02.jpg" width="348" />
   
6. Download and install VS2015 onto this machine


#### Installing and configuring VSTS Agent
1. Browse to your VSTS instance and select the team project you created earlier

   <img src="media/2017-03-16_16-12-06.jpg" width="640" />
   
2. Hover over the gears icon and select Agent queues

   <img src="media/2017-03-16_16-13-30.jpg" width="640" />
   
3. Click Download agent
   
4. Click Download

   <img src="media/2017-03-16_16-22-46.jpg" width="640" />
   
5. Click Save

   <img src="media/2017-03-16_16-23-39.jpg" width="640" />
   
6. After the zip file downloads, open a powershell window and follow the instructions

   <img src="media/2017-03-16_16-26-43.jpg" width="640" />
   
7. After configuring VSTS agent, verify the agent shows up in your Default queue and is green

   <img src="media/2017-03-16_16-33-30.jpg" width="640" />
   
### Task 4: Creating your Azure databases for dev and prod
The Redgate demo pushes database changes to two databases, both hosted in Azure.  One will be used for the Dev environment, one will
be used for the Prod environment.

1. Browse to the Azure portal and click SQL databases

   <img src="media/2017-03-17_8-30-11.jpg" width="640" />
   
2. Click Add

   <img src="media/2017-03-17_9-49-06.jpg" width="640" />
   
3. Enter bikesharing-services-ridesname_dev for Database name, choose your subscription and select Use existing Resource group and select 
the resource group you created for your build and release VM

   <img src="media/2017-03-17_9-50-43.jpg" width="640" />
   
4. Click Configure required settings under Server

   <img src="media/2017-03-17_9-53-59.jpg" width="640" />
   
5. Click Create a new server

   <img src="media/2017-03-17_9-55-03.jpg" width="640" />
   
6. Enter bikesharing-services-dbserver for Server name, enter a Server admin login and password, select a Location and click Select

   <img src="media/2017-03-17_9-57-40.jpg" width="640" />

7. Click Create

   <img src="media/2017-03-17_9-58-37.jpg" width="640" />
   
8. Wait for DB to be created

   <img src="media/2017-03-17_10-00-10.jpg" width="640" />
   
9. Click Refresh

   <img src="media/2017-03-17_9-49-06x.jpg" width="640" />
   
10. Click Add

   <img src="media/2017-03-17_10-03-49.jpg" width="640" />
   
11. Enter bikesharing-services-ridesname_prod for Database name, choose your subscription and select Use existing Resource group and select 
the resource group you created for your build and release VM
   
    <img src="media/2017-03-17_10-06-37.jpg" width="640" />
   
12. Make sure bikesharing-services-dbserver is selected under Server and click Create

    <img src="media/2017-03-17_10-07-15.jpg" width="640" />

13. Wait for prod DB to be created

    <img src="media/2017-03-17_10-09-19.jpg" width="640" />
	


### Task 5: Create build definition
1. Browse to your VSTS demo project and click on the build tab

   <img src="media/2017-03-16_16-40-07.jpg" width="640" />

2. Click on New definition

   <img src="media/2017-03-16_16-38-55.jpg" width="640" />
   
3. Click on Visual Studio

   <img src="media/2017-03-17_10-25-25.jpg" width="640" />
   
4. Click on Apply

   <img src="media/2017-03-17_10-26-12.jpg" width="640" />
   
5. Click on Add Task

   <img src="media/2017-03-17_10-28-46.jpg" width="640" />
   
6. In the search field, type in command

   <img src="media/2017-03-17_10-29-54.jpg" width="640" />
   
7. Drag the command task under the NuGet restore task

   <img src="media/2017-03-17_10-29-54x.jpg" width="640" />
   
8. Click on the Run task

   <img src="media/2017-03-17_10-32-28.jpg" width="640" />
   
9. Type Setup Shadow DB for Display name. Type C:\Program Files\Microsoft SQL Server\130\Tools\Binn\SqlLocalDB.exe for Tool.  Type create $(ShadowInstanceName) -s
for Arguments

   <img src="media/2017-03-17_10-34-02.jpg" width="640" />
   
10. Click on Build solution task

    <img src="media/2017-03-17_10-38-42.jpg" width="640" />

11. In MSBuild Arguments type in:

    /p:DeployOnBuild=true /p:WebPublishMethod=Package /p:PackageAsSingleFile=true /p:SkipInvalidConfigurations=true /p:PackageLocation="$(build.artifactstagingdirectory)\\" /p:TargetServer="$(DatabaseServer)" /p:TargetDatabase="$(DatabaseName)" /p:TargetUserName="$(DatabaseUserName)" /p:TargetPassword="$(DatabasePassword)" /p:ShadowServer="(localdb)\$(ShadowInstanceName)" /p:GenerateSqlPackage=True /p:SkipDriftAnalysis=True

    <img src="media/2017-03-17_10-40-54.jpg" width="640" />
	
12. Click on the Test Assemblies task

    <img src="media/2017-03-17_10-48-04.jpg" width="640" />
	
13. For Test Filter criteria type in TestCategory=Unit Test 

    <img src="media/2017-03-17_10-50-40.jpg" width="640" />
	
15. Click on Add Task

    <img src="media/2017-03-17_10-51-46.jpg" width="640" />
	
16. In the Search field, type in Archive

    <img src="media/2017-03-17_10-54-11.jpg" width="640" />
	
17. Drag the Archive Files task under the Test Assemblies task

    <img src="media/2017-03-17_10-54-11x.jpg" width="640" />
	
18. Click on the Archive files task

    <img src="media/2017-03-17_10-56-00.jpg" width="640" />
	
19. Under Root folder (or file to archive) type in src/BikeSharing.Services.Rides

    <img src="media/2017-03-17_10-57-45.jpg" width="640" />
	
20. Right click Publish symbols path and select Remove selected task(s)

    <img src="media/2017-03-17_10-59-00.jpg" width="640" />
	
21. Right click the Copy Files to task and select Remove selected task(s)

    <img src="media/2017-03-17_11-02-18.jpg" width="640" />
	
22. Click Add Task

    <img src="media/2017-03-17_11-03-34.jpg" width="640" />
	
23. Type copy in the search field

    <img src="media/2017-03-17_11-05-08.jpg" width="640" />
	
24. Drag Copy and Publish Build Artifacts task under the Publish Artifact task

    <img src="media/2017-03-17_11-05-08x.jpg" width="640" />
	
25. Click on Copy Publish Artifact task

    <img src="media/2017-03-17_11-07-53.jpg" width="640" />
	
26. For Display name type Copy Publish Artifact: drop. For Contents type BikeSharing.Services.RidesName/bin/$(BuildConfiguration). 
For Artifact Type select Server.

    <img src="media/2017-03-17_11-09-08.jpg" width="640" />
	
27. Click Add Task

    <img src="media/2017-03-17_11-10-38.jpg" width="640" />
	
28. In the search field, type in copy

    <img src="media/2017-03-17_11-11-53.jpg" width="640" />
	
29. Drag an drop the Copy and Publish Build Artifacts task to the end

    <img src="media/2017-03-17_11-11-53x.jpg" width="640" />
	
28. Click on the Copy Publish Artifact task

    <img src="media/2017-03-17_11-14-17.jpg" width="640" />
	
29. For Display name type in Copy Publish Artifact: UITests. For Contents type in BikeSharing360.Tests/bin/$(BuildConfiguration). 
For Artifact Name type in drop. For Artifact Type select Server

    <img src="media/2017-03-17_11-16-13.jpg" width="640" />

30. Click on the Build solution task

    <img src="media/2017-03-27_11-31-39.jpg" width="640" />

31. Click on the link next to Solution and then click the Unlink button

    <img src="media/2017-03-27_11-33-39.jpg" width="640" />

32. Enter BikeSharing360Redgate.sln for Solution

    <img src="media/2017-03-27_11-35-12.jpg" width="640" />
	
33. Click on Variables tab

    <img src="media/2017-03-17_11-17-18.jpg" width="640" />
	
34. Add the following variables. DatabaseServer, DatabaseName, DatabaseUserName, DatabasePassword, ShadowInstanceName

    <img src="media/2017-03-17_11-22-03.jpg" width="640" />
	
	To get the database server name and database name, from your azure portal, browse to the dev database.
	
	<img src="media/2017-03-17_11-24-29.jpg" width="640" />
	
	The DatabaseUserName and DatabasePassword are whatever you set when you created these databases and the ShadowInstanceName is Shadow
	
35. Click on the Triggers tab

	<img src="media/2017-03-17_11-26-17.jpg" width="640" />
	
36. Enable Continuous Integration

	<img src="media/2017-03-17_11-27-16.jpg" width="640" />
	
37. Click on the Options tab

	<img src="media/2017-03-17_11-29-33.jpg" width="640" />
	
38. Select Default for Default agent queue

	<img src="media/2017-03-17_11-30-24.jpg" width="640" />
	
39. Click on Save & queue and click on Save & queue

	<img src="media/2017-03-17_11-31-26.jpg" width="640" />
	
	
40. Click on Queue

	<img src="media/2017-03-17_11-32-24.jpg" width="640" />
	
41. Verify build completes successfully

	<img src="media/2017-03-17_11-33-23.jpg" width="640" />


### Task 6: Create release pipeline
The Redgate demo has a release pipeline that deploys an resource group based on an ARM template, deploys the web app to the resource group, deploys the
database schema changes, runs a quick Web Performace Test on the site and then runs some Selenium Automated UI Tests on the new environment (This demo doesn't
actually run selenium tests, it just simulates it). It does this deployment to both the Dev and Prod environment.

1. Browse to your VSTS project and click on Buil & Release tab and select Release

   <img src="media/2017-03-17_13-25-39.jpg" width="640" />
   
2. Click on New definition

   <img src="media/2017-03-17_13-26-50.jpg" width="640" />
   
3. Click on Aure App Service Deployment template and then click Next

   <img src="media/2017-03-17_13-29-18.jpg" width="640" />
   
4. Check Continuous deployment(create release and deploy whenever a build completes) and select the Default queue and click Create

   <img src="media/2017-03-17_13-30-19.jpg" width="640" />
   
5. Rename the environment Dev

   <img src="media/2017-03-17_13-32-44.jpg" width="640" />
   
6. Chose your Azure Subscrption. For App Service name and click Authorize

   <img src="media/2017-03-17_13-35-44.jpg" width="640" />
   
7. For App Service name and enter $(WebSiteName), for Package or folder browse to the BikeShare360.zip file with the ellipses. It should be something
   similar to $(System.DefaultWorkingDirectory)/RedgateDemoProj-Visual Studio-CI/drop/BikeSharing360.zip

   <img src="media/2017-03-17_13-37-13.jpg" width="640" />
   
8. Click on Add tasks

   <img src="media/2017-03-17_13-38-10.jpg" width="640" />
   
9. Click the Add button next to the Azure Resource Group Deployment task

   <img src="media/2017-03-17_13-39-31.jpg" width="640" />
   
10. Click the Close button

    <img src="media/2017-03-17_13-40-36.jpg" width="640" />
   
11. Drag the Azure Deployment task above Deploy Azure App Service task

    <img src="media/2017-03-17_13-41-23.jpg" width="640" />
	
12. Select your subscription in Azure subscriptions.  
    Enter $(WebSiteName) for Resource group.  
	Select West US for Location. 
	Select $(System.DefaultWorkingDirectory)/RedgateDemoProj-Visual Studio-CI/drop/BikeSharing360.IaC/WebSite.json for Template.
	Select $(System.DefaultWorkingDirectory)/RedgateDemoProj-Visual Studio-CI/drop/BikeSharing360.IaC/WebSite.parameters.json for Template parameters
	Enter -hostingPlanName $(WebSiteName) for Override template parameters

    <img src="media/2017-03-17_13-47-22.jpg" width="640" />
	
13. Click Add tasks

    <img src="media/2017-03-17_13-48-54.jpg" width="640" />
	
13. Scroll down and click the Add button next to Deploy ReadyRoll Database Package and then click Close

    <img src="media/2017-03-17_13-49-40.jpg" width="640" />
	
13. Click on Deploy to

    <img src="media/2017-03-17_13-51-48.jpg" width="640" />
	
14. For Package to Deploy, enter $(System.DefaultWorkingDirectory)/RedgateDemoProj-Visual Studio-CI/drop/Release/BikeSharing.Services.RidesName_DeployPackage.ps1
    For Release Version, enter $(Release.ReleaseId)
	For Target SQL Server Instance, enter $(DatabaseServer)
	For Target Database Name, enter $(DatabaseName)
	For Database Username enter $(DatabaseUserName)
	For Database Password enter $(DatabasePassword)
	
    <img src="media/2017-03-17_13-54-52.jpg" width="640" />
	
15. Click on Add tasks

    <img src="media/2017-03-17_14-02-03.jpg" width="640" />
	
16. Click on Test, then click on the Add button next to Cloud-based Web Performance Test and then click Close

    <img src="media/2017-03-17_14-03-18.jpg" width="640" />
	
17. Click on Quick Web Performance Test

    <img src="media/2017-03-17_14-05-07.jpg" width="640" />
	
18. For Website URL enter http://vs2017launchbikeshare360d.azurewebsites.net/
    For Test Name enter Homepage
	
	<img src="media/2017-03-17_14-06-42.jpg" width="640" />
	
19. Click on Add tasks

    <img src="media/2017-03-17_14-07-52.jpg" width="640" />
	
20. Click on Test then scroll down and click the Add button next to Visual Studio Test and then click Close

    <img src="media/2017-03-17_14-09-06.jpg" width="640" />
	
21. Click on Test Assemblies

    <img src="media/2017-03-17_14-10-59.jpg" width="640" />
	
22. For title enter Selenium Automated UI Tests: Dev for the title
    Select Version 2
	For Test filter criteria enter TestCategory=UITest
	For Test runtitle under REorting options, enter Selenium Dev UI Tests

    <img src="media/2017-03-17_14-13-32.jpg" width="640" />
    <img src="media/2017-03-17_14-16-22.jpg" width="640" />
	
23. Click on the ellipses on the Dev environment and select Configure variables

    <img src="media/2017-03-17_14-18-18.jpg" width="640" />
	
24. Enter bikesharing-services-ridesname_dev for the DatabaseName.
    For WebSiteName, enter VS2017LaunchBikeShare360D (this name does need to be unique so you may need to give your website a unique name. 
	If you need to change the website name, make sure you use the same name when you use it in the website url).
	click OK

    <img src="media/2017-03-17_14-41-15.jpg" width="640" />
	
25. Click on Variables

    <img src="media/2017-03-17_14-21-58.jpg" width="640" />
	
26. Enter in variables for DatabaseServer, DatabaseUserName and DatabasePassword.  You can find the database server name by browsing to your Azure portal
browsing to your dev database.  The DatabaseUserName and DatabasePassword are what you set them when you created the database server.

    <img src="media/2017-03-17_14-25-00.jpg" width="640" />
    <img src="media/2017-03-17_14-25-26.jpg" width="640" />
	
27. Click on Environments

    <img src="media/2017-03-17_14-28-10.jpg" width="640" />
	
28. Click on Add enviroment and then select Clone selected Environments

    <img src="media/2017-03-17_14-29-10.jpg" width="640" />
	
29. Select Specific users, then enter yourself as an approver.  Make sure Default is selected for the agent queue and click Create

    <img src="media/2017-03-17_14-30-48.jpg" width="640" />
	
30. Rename environment to Prod

    <img src="media/2017-03-17_14-32-21.jpg" width="640" />
	
31. Click on Quick Web Performance Test Homepage

    <img src="media/2017-03-17_14-33-58.jpg" width="640" />
	
32. For Website Url enter http://vs2017launchbikeshare360p.azurewebsites.net/

    <img src="media/2017-03-17_14-36-02.jpg" width="640" />
	
33. Click on the ellipses in the Prod environment and select Configure variables

    <img src="media/2017-03-17_14-36-53.jpg" width="640" />
	
34. For DatabaseName enter bikesharing-services-ridesname_prod
    For WebSiteName enter VS2017LaunchBikeShare360P
	Click OK
	
    <img src="media/2017-03-17_14-38-32.jpg" width="640" />	
	
35. Click Save
	
    <img src="media/2017-03-17_14-45-03.jpg" width="640" />	
	
36. Click OK

    <img src="media/2017-03-17_14-45-48.jpg" width="640" />	
	
This completes building out the release pipeline. DO NOT KICK OFF A RELEASE AT THIS TIME.  The release pipeline will fail until we configure the databases
to use Readyroll migrations.  We will do this in the next section.


## Demo machine configuration

Make sure your demo machine has git installed as well as Visual Studio 2017 with the Data storage and processing workload
installed.  Make sure all 3 Redgate tools are checked (Redgate ReadyRoll, Redgate SQL Prompt and Redgate SQL Search).

### Task 1: Clone Repo
1. Browse to your VSTS project and click on the Code tab

   <img src="media/2017-03-17_14-58-11.jpg" width="640" />	
	
2. Click on Clone

   <img src="media/2017-03-17_14-59-11.jpg" width="640" />	
	
3. Click on Clone in Visual Studio and then select Visual Studio

   <img src="media/2017-03-17_15-02-05.jpg" width="640" />	
   
4. Click Allow

   <img src="media/2017-03-17_15-03-28.jpg" width="640" />
   
5. Sign into your account

   <img src="media/2017-03-17_15-04-52.jpg" width="640" />

6. Choose where you want to clone the repo and click Clone

   <img src="media/2017-03-17_15-09-11.jpg" width="640" />
   


### Task 2: Configure Visual Studio

1.  Open **BikeSharing360Redgate.sln** from the folder that you cloned the
    project into.

2.  Open the ReadyRoll window. If it isn’t already there, click
    **ReadyRoll** | **ReadyRoll**

    <img src="media/image1.png" width="554" height="179" />

3. Click View then select SQL Server Object Explorer

   <img src="media/2017-03-17_15-20-08.jpg" width="640" />
	
4. open up (localdb)\ProjectsV13 and see if there is a database named BikeSharing.Services.RidesName.
   <img src="media/2017-03-17_15-27-43.jpg" width="640" />  
	
   If there isn't, create one by right clicking the Databases folder and select Add New Database
   <img src="media/2017-03-17_15-28-56.jpg" width="640" />

   For Database Name enter BikeSharing.Services.RidesName and click OK
   <img src="media/2017-03-17_15-30-01.jpg" width="640" />
  
5. click the Deploy in the readyroll window
   <img src="media/2017-03-17_15-30-01x.jpg" width="640" />

6. Open the BikeSharing.Services.RidesName database up and make sure the baseline database deployed to your local database

   <img src="media/2017-03-17_15-40-15.jpg" width="640" />
   
7. Click on Add SQL Server

   <img src="media/2017-03-17_15-45-28.jpg" width="640" />
   
8. Enter the server name (you can get this from your azure portal). Select SQl Server Authentication for Authentication. Enter the user name
and password you create when you created the database server in Azure, click Remeber Password and select master for the Database Name
and click Connect

   <img src="media/2017-03-17_15-46-58.jpg" width="640" />
   
9. Open up the cloud database you just added to verify that your dev and prod databases are there

   <img src="media/2017-03-17_15-51-04.jpg" width="640" />
 
### Task 3: Configure the Dev and Prod database to use ReadyRoll migrations
  
1. Click on Configure database connection

   <img src="media/2017-03-17_16-03-23.jpg" width="640" />
   
2. Click on Show connection Properties

   <img src="media/2017-03-17_16-04-23.jpg" width="640" />
   
3. Click on the database server you set in Azure under Recent Connections, then change the Database name to the dev database and click OK

   <img src="media/2017-03-17_16-04-23.jpg" width="640" />
   
4. Click Deploy BikeSharing.Services.RidesName in the ReadyRoll window

   <img src="media/2017-03-17_16-07-17.jpg" width="640" />
   
5. Click the ReadyRoll Core Edition tab

   <img src="media/2017-03-17_16-08-31.jpg" width="640" />
   
6. Click on Configure database connection

   <img src="media/2017-03-17_16-09-31.jpg" width="640" />
   
7. Click on the dev database under recent connections, then under Database name, select the prod database and click OK

   <img src="media/2017-03-17_16-10-38.jpg" width="640" />
 
8. In the ReadyRoll window, click on Deploy BikeSharing.Services.RidesName

   <img src="media/2017-03-17_16-12-18.jpg" width="640" />
   
9. Click on the ReadyRoll Core Edition tab

   <img src="media/2017-03-17_16-13-35.jpg" width="640" />
   
   
10. Click on Configure database connection

    <img src="media/2017-03-17_16-14-20.jpg" width="640" />
   
11. Enter (localdb)\ProjectsV13 for Server Name, Authentiation, choose Windows Authentication, under Database Name select 
BikeSharing.Services.RidesName and click OK

    <img src="media/2017-03-17_16-15-26.jpg" width="640" />
   
   
This finishes configuring the demo machine.

## Demo

1. Open the solution **BikeSharing360Redgate.sln** in your Visual Studio 2017

   <img src="media/2017-03-27_10-33-12.jpg" width="640"/>  

   >**Talking Point**: Managing your database changes and incorporating them into your DevOps pipeline has always been difficult. Keeping track of what scripts need to be run, getting the database states just right is a pain and very error prone. However, there are some fantastic tools from Redgate which help us manage our database changes as well as creating a fully automated CI/CD Pipeline. With each copy of Visual Studio Enterprise, you get Ready Roll, SQL Prompt, and SQL Search for free. Now, with VSE and the included Redgate tools, you can check in and out your database schema right alongside your source code. You can also easily create your CI/CD pipeline which will seamlessly deploy those changes to the database’s in all your environments.

2. Right click solution and **add | new | project**

   <img src="media/2017-03-27_10-41-58.jpg" width="640"/>                                         
   
   >**Talking Point**: To create a database project from scratch is super easy, just right click your solution, 
   add new project, click on the SQL server node in the tree and select ReadyRoll SQL Server Database project.
   We've already created a ReadyRoll project so let's just jump into it (Click Cancel)
   
3. Expand **bikesharing-services-ridesName** database in SQL Server Object Explorer. Expand the Tables folder. 

   <img src="media/2017-03-27_10-48-38.jpg" width="640"/>                                        
   
   >**Talking Point**: This ReadyRoll db project is already connected to our dev db instance.                                                   
   
4. Right click **dbo.bikes** and select **View Designer**.

   <img src="media/2017-03-27_10-49-47.jpg" width="640"/>               
   
   >**Talking Point**: If I need to change the schema of my database, all I need to do is just change the schema in SQL Server 
   Object Explorer or SSMS or whatever tool of choice and make my change to the DB schema. ReadyRoll detects those changes you made 
   to your dev database and will add the correct migration script to your project.                              
   
5. In the Designer window, add a **new SQL column**. Set its name to **LastServicedAt**, its data type to **datetime2(7)**, and 
   make sure the checkbox under **allow nulls** is checked. 

   <img src="media/2017-03-27_10-54-14.jpg" width="640"/>
   
   >**Talking Point**: In this project, I’m going to need to add a new column to the bikes table. I need to add a LastServicedAt column.                          
   
6. Click **update** in the top left corner. Then click Update Database.

   <img src="media/2017-03-27_10-55-57.jpg" width="640"/> 

   <img src="media/2017-03-27_10-57-08.jpg" width="640" />
   
   >**Talking Point**: When I’m done modifying my database, I go ahead and click the update and it will update my dev database.                                    

7. Open the ReadyRoll window by clicking the **ReadyRoll Core Edition** tab at the bottom, then click the **Refresh button**.

   <img src="media/2017-03-27_10-59-18.jpg" width="640" />
   
   >**Talking Point**: Next, I go into the ReadyRoll window and click refresh. This will do a schema compare between my dev database 
   and what ReadyRoll thinks my database is currently, and will automatically generate the migration script.
   
8. Double click on the row. A tab will open displaying the changes between our old and new schema.  
   <img src="media/2017-03-27_11-01-33.jpg" width="640" />

   <img src="media/2017-03-27_11-02-53.jpg" width="640"/>

   >**Talking Point**: To see exactly what it found, we can go ahead and double click on the changes, this will bring up a diff of 
   the changes.
   
9. Click **Import and generate script** for all database changes that are pending import.

   <img src="media/2017-03-27_11-04-10.jpg" width="640" />
   
   >**Talking Point**: To bring this migration script into the solution, I’ll go and click the Import and generate script button.

10. Rename the migration script to **0002\_add\_servicing\_date\_column.sql”**. After renaming, make sure you click the save all button so the renamed file is saved and the project reference is saved.

    <img src="media/2017-03-27_11-06-32.jpg" width="640" />
    
    >**Talking Point**: Lets change the name of the imported script so it has a more descriptive migration script name.
    
11. Double click the migration script **(0002\_add\_servicing\_date\_column.sql)** to open it. In the new SQL query file, type the below code snippet at the end (after the last “GO”)

    ````
    GO
    UPDATE dbo.bikes SET LastServicedAt = InCirculationSince
    GO

    ````
    After typing this make sure you save the file.
    
    <img src="media/2017-03-27_11-13-04.jpg" width="640"/>

    >**Talking Point**: It’s super easy for us to prepopulate this column with data too. Just double click the migration script 
    and modify it. Notice how SQL Prompt Core offers suggestions and gives quality of life improvements for writing SQL code?

12. Select these new lines and click the **Execute** button **(or press ctrl-shift-e)** to run this code on the dev database. 
    Click **Mark as Deployed** in the **Script Status** window.
    
    <img src="media/2017-03-27_11-13-45.jpg" width="640"/>  

    <img src="media/2017-03-27_11-16-10.jpg" width="640" />                                                     
   
    >**Talking Point**: We’ll go ahead and run this script to populate the new column with data in our dev database. Since we 
    haven’t serviced our bikes yet, LastServicing = InCirculationSince. ReadyRoll also makes it easy to add NOT NULL columns 
    without a DEFAULT. (There is no data in the database so 0 rows will be affected.  If you add some data, then this will
    look better)

13. Click Refresh (Verify Script) in the ReadyRoll window

    <img src="media/2017-03-27_11-18-17.jpg" width="640" />

    <img src="media/2017-03-27_11-19-21.jpg" width="640" />

    >**Talking Point**: Before checking in our code, let's verify that our script is correct.  Notice how the ReadyRoll
    window now shows the script with a big green check.

13. Check code back into **VSTS** and go to VSTS portal and check out the build in progress and also previous succesful
    build report

    <img src="media/2017-03-27_11-24-38.jpg width="640" />

    <img src="media/2017-03-27_13-53-30.jpg" width="640"/>

    <img src="media/2017-03-27_13-54-53.jpg" width="640"/>
   
    >**Talking Point**: So now that we made those changes, let’s check in our code. This will kick off our build. As you can see, 
    the build is just a simple straight forward build. The build takes a while so let’s again take a look at a build that has 
    already gone through. Notice in our build report, it lists the tables that have changed. Also, if we click on Database script, 
    we can actually see the migration scripts that get run for the deployments.

14. Go to **release**, show the task. Click on old release, show the database deployment preview section and also the Database script tab.

    <img src="media/2017-03-27_13-56-43.jpg" width="640" /> 
                                                             
    <img src="media/2017-03-27_13-57-46.jpg" width="640" />  
                                                             
    <img src="media/image24.png" width="640" />

    >**Talking Point**: Now our build is linked to RM, so when we get a successful build, it kicks off our CD pipeline where we 
    can easily deploy the database changes using prebuild release ReadyRoll Task. Once again, the release takes a while so let’s 
    look at a prior release. We can see exactly what tables were changed, what migrations were ran. We can look at the Data script tab and see the exact script used as well. 
   
## Resetting demo
To reset the demo, browse to dev prod and local database and delete the extra column you added.  Then removed the 002 migration script
from Source and check everything back in.
