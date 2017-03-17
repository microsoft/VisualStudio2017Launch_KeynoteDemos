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
   
2. Give your project a name and click Create

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
need to install VS2015.

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

#### Installing Sql Server Management Studio
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
	
30. Click on Variables tab

    <img src="media/2017-03-17_11-17-18.jpg" width="640" />
	
31. Add the follwoing variables. DatabaseServer, DatabaseName, DatabaseUserName, DatabasePassword, ShadowInstanceName

    <img src="media/2017-03-17_11-22-03.jpg" width="640" />
	
	To get the database server, from your azure portal, browse to the dev database.
	
	<img src="media/2017-03-17_11-24-29.jpg" width="640" />
	
	The DatabaseUserName and DatabasePassword are whatever you set when you created these databases and the ShadowInstanceName is Shadow
	
32. Click on the Triggers tab

	<img src="media/2017-03-17_11-26-17.jpg" width="640" />
	
33. Enable Continuous Integration

	<img src="media/2017-03-17_11-27-16.jpg" width="640" />
	
34. Click on the Options tab

	<img src="media/2017-03-17_11-29-33.jpg" width="640" />
	
35. Select Default for Default agent queue

	<img src="media/2017-03-17_11-30-24.jpg" width="640" />
	
36. Click on Save & queue and click on Save & queue

	<img src="media/2017-03-17_11-31-26.jpg" width="640" />
	
	
37. Click on Queue

	<img src="media/2017-03-17_11-32-24.jpg" width="640" />
	
38. Verify build completes successfully

	<img src="media/2017-03-17_11-33-23.jpg" width="640" />


### Task 6: Create release pipeline

## VS Configuration

Install Visual Studio 2017 RC by selecting the “Data storage and
processing workload” and making sure that all three Redgate tools
(Redgate ReadyRoll, Redgate SQL Prompt, and Redgate SQL Search) are
checked.

Open Visual Studio and sign in.


### Task 1: Reset demo repository

1.  Open the command prompt or PowerShell

2.  git clone
    <https://github.com/abelsquidhead/VS2017VSTSKeynoteDemo>

3.  git push origin +5a5d6:master (please use the hash in git before you
    made your changes)

4.  git reset --hard origin/master

### Task 2: Configure Visual Studio

1.  Open **BikeSharing360Redgate.sln** from the folder that you cloned the
    project into.

2.  Open the ReadyRoll window. If it isn’t already there, click
    **ReadyRoll** | **ReadyRoll**

    <img src="media/image1.png" width="554" height="179" />

3.  In the ReadyRoll window at the bottom click the button labeled **Set the target database connection string for this project**
    
    <img src="media/image3.png" width="541" height="285" />

4.  Use the following settings for setting the target database
    connection:

    - **Server name**: git pus

    - **Authentication**: SQL Server Authentication

    - **User name**: MyBikes

    - **Password**: BikesShare360@1

    - **Database name**: bikesharing-services-ridesName\_dev
        
        <img src="media/image4.PNG" width="488" height="274" />

5.  Click **Test Connection**.

6.  Click **OK**.

7.  Open the SQL Server Object Explorer

8.  Click the button labeled **Add SQL Server**.

    <img src="media/image5.PNG" width="164" height="190" />

9.  Enter the following:

    - **Server name**: bikesharing360hlwkn37yuj4vo.database.windows.net

    - **Authentication**: SQL Server Authentication

    - **User name**: MyBikes

    - **Password**: BikesShare360@1

    - **Database name**: master

        <img src="media/image6.PNG" width="488" height="273" />

### Task 3: Reset databases


1.  Open the SQL Server Object Explorer in Visual Studio

2.  Expand the following:

    - bikesharing360hlwkn37yuj4vo.database.windows.net

    - Databases

    - bikesharing-services-ridesName

    - Tables

    - dbo.bikes

    - Columns

      <img src="media/image7.PNG" width="490" height="270" />

3.  If there are any columns other than these ones listed **(Id, SerialNumber, InCirculationSince, StationId)**, right click the column and click **Delete**.

4.  Repeat these steps for **bikesharing-services-ridesName\_dev**.


## Demo

1. Open the project **BikeSharing.Services.RidesName** in your Visual Studio 2017

   <img src="media/image8.png" width="624"/>  

   >**Talking Point**: Managing your database changes and incorporating them into your DevOps pipeline has always been difficult. Keeping track of what scripts need to be run, getting the database states just right is a pain and very error prone. However, there are some fantastic tools from Redgate which help us manage our database changes as well as creating a fully automated CI/CD Pipeline. With each copy of Visual Studio Enterprise, you get Ready Roll, SQL Prompt, and SQL Search for free. Now, with VSE and the included Redgate tools, you can check in and out your database schema right alongside your source code. You can also easily create your CI/CD pipeline which will seamlessly deploy those changes to the database’s in all your environments.

2. Right click solution and **add | new | project**

   <img src="media/image9.png" width="624"/>                                         
   
   >**Talking Point**: To create a database project from scratch is super easy, just right click your solution, add new project, click on the SQL server node in the tree and select ReadyRoll SQL Server Database project
   
3. Expand **bikesharing-services-ridesName\_dev** database in SQL Server Object Explorer. Expand the Tables folder. 

   <img src="media/image10.png" width="624"/>                                        
   
   >**Talking Point**: We’ve already created one for this demo and it is already connected to our dev instance.                                                   
   
4. Right click **dbo.bikes** and select **View Designer**.

   <img src="media/image11.png" width="624"/>               
   
   >**Talking Point**: If I need to change the schema of my database, all I need to do is just change the schema in SQL Server Object Explorer or SSMS or whatever tool of choice and make my change to the DB schema. ReadyRoll detects those changes you made to your dev database and will add the correct migration script to your project.                              
   
5. In the Designer window, add a **new SQL column**. Set its name to **LastServicedAt**, its data type to **datetime2(7)**, and make sure the checkbox under **allow nulls** is checked. 

   <img src="media/image12.png" width="624"/>
   
   >**Talking Point**: In this project, I’m going to need to add a new column to the bikes table. I need to add a LastServicedAt column.                          
   
6. Click **update** in the top left corner.

   <img src="media/image13.png" width="624"/> 
   
   >**Talking Point**: When I’m done modifying my database, I go ahead and click the update and it will update my dev database.                                    

7. Open the ReadyRoll window by clicking the **ReadyRoll Core Edition** tab at the bottom, then click the **Refresh button**.

   <img src="media/image14.png" width="624" />
   
   >**Talking Point**: Next, I go into the ReadyRoll window and click refresh. This will do a schema compare between my dev database and what ReadyRoll thinks my database is currently, and will automatically generate the migration script.
   
8. Double click on the row. A tab will open displaying the changes between our old and new schema.                                                                 
   <img src="media/image15.png" width="624"/>

   >**Talking Point**: To see exactly what it found, we can go ahead and double click on the changes, this will bring up a diff of the changes.
   
9. Click **generate script(s)** for all database changes that are pending import.

   <img src="media/image16.png" width="624" />
   
   >**Talking Point**: To bring this migration script into the solution, I’ll go and click the Import and generate script button.

10. Rename the migration script to **0002\_add\_servicing\_date\_column.sql”**. After renaming, make sure you click the save all button so the renamed file is saved and the project reference is saved.

    <img src="media/image17.png" width="624" />
    
    >**Talking Point**: Lets change the name of the imported script so it’s easier to read.
    
11. Double click the migration script **(0002\_add\_servicing\_date\_column.sql)** to open it. In the new SQL query file, type the below code snippet at the end (after the last “GO”)

    ````
    GO
    UPDATE dbo.bikes SET LastServicingAt = InCirculationSince
    GO

    ````
    After typing this make sure you save the file.
    
    <img src="media/image18.png" width="624"/>

    >**Talking Point**: It’s super easy for us to prepopulate this column with data too. Just double click the migration script and modify it.
    Notice how SQL Prompt Core offers suggestions and gives quality of life improvements for writing SQL code?

12. Select these new lines and click the **Execute** button **(or press ctrl-shift-e)** to run this code on the dev database. Click **Mark as Deployed** in the **Script Status** window.
    
    <img src="media/image19.png" width="624"/>                                                       
   
    >**Talking Point**: We’ll go ahead and run this script to populate the new column with data in our dev database. Since we haven’t serviced our bikes yet, LastServicing = InCirculationSince. ReadyRoll also makes it easy to add NOT NULL columns without a DEFAULT.

13. Check code back into **VSTS** and go to VSTS portal and check out the build in progress.

    <img src="media/image20.png" width="624"/>

    <img src="media/image21.png" width="624"/>
   
    >**Talking Point**: So now that we made those changes, let’s check in our code. This will kick off our build. As you can see, the build is just a simple straight forward build. The build takes a while so let’s again take a look at a build that has already gone through. Notice in our build report, it lists the tables that have changed. Also, if we click on Database script, we can actually see the migration scripts that get run for the deployments.

14. Go to **release**, show the task. Click on old release, show the database deployment preview section and also the Database script tab.

    <img src="media/image22.png" width="624" /> 
                                                             
    <img src="media/image23.png" width="624" />  
                                                             
    <img src="media/image24.png" width="624" />

    >**Talking Point**: Now our build is linked to RM, so when we get a successful build, it kicks off our CD pipeline where we can easily deploy the database changes using prebuild release ReadyRoll Task. Once again, the release takes a while so let’s look at a prior release. We can see exactly what tables were changed, what migrations were ran. We can look at the Data script tab and see the exact script used as well. 
   