# VSTS and DevOps

<p align="center">
<img src="media/VSTS.png" width="724"/>
</p>

## High-level flow

-  Zero to DevOps in 9 minutes

-  Create full DevOps pipeline from nothing to a full CI/CD pipeline

## Rough Outline

-  Create a Team Project in VSTS

-  Import source code from github

-  Create a build in VSTS

-  Create a Release pipeline in VSTS

## Key Takeaway

1.  VSTS is the best platform when it comes to DevOps and CI/CD.

2.  VSTS is the most flexible platform that will allow you to
    do anything. Any language, Any platform.

3.  With VSTS, it is incredibly simple to create your full dev
    ops pipeline.

4.  Nothing can compare with VSTS and DevOps when it comes to Azure

## Demo URL's

-  Github repo with sample code:
    <https://github.com/abelsquidhead/VSTSDemoKeynoteDemo1>

## Demo Bits and licenses (Setup)

### Zoomit
<https://technet.microsoft.com/en-us/sysinternals/zoomit.aspx>

### Autohotkey 
<https://www.autohotkey.com/>

## Demo scenario


Deliver scalable, reliable applications faster to meet the ever-changing
demands of your customers as your business grows. Born-in-the-cloud
services built on a rich Microservices platform, free developers from
infrastructure concerns and help them realize the full potential of the
Cloud.

**BikeSharing360** uses different Microservices on their backend built on
different languages. Some of these Microservices include:

<img src="media/1.png" />

Let’s look at how easily VSTS can be used for DevOps. Within minutes, we
can start from nothing and create a full CI/CD system.

## Exercise 1: DevOps Demo 1 (Setup)

Make sure you have a VSTS and Azure account

## DevOps Demo: Productivity, CI/CD with VSTS

**Scenario**: Traditionally, implementing a full CI/CD system is difficult.
With VSTS, this becomes trivial. Within minutes, you can implement a
full CI/CD system that is completely customizable to do anything you
want.

>**Talking Point**: DevOps is the union of People, Process and our Products to enable continuous delivery of value to our end users. This is an inherently difficult process so we definitely need tools and products to help us. VSTS gives us that complete DevOps coverage. From tracking all of our work, checking code in and out, following software dev processes, all the way to the CI/CD pipeline. CI/CD can be extremely complicated. VSTS is the ultimate platform for DevOps. We simplify the whole CI/CD platform so it’s extremely easy to create this full pipeline. Today, we are going to show you how we can start from nothing tofull end to end CI/CD pipeline in minutes!

1. Browse to vsts project page and click on New Project.

   <img src="media/image1.png" width="824" />

   >**Talking Point**: First we will browse to my VSTS instance and from here I will create a new team project.

2. Enter in project name and click create.

   <img src="media/image2.png" width="824" />

   >**Talking Point**: Let’s give our project a name.

3. Click on the **import a repository**.

   <img src="media/image3.png" width="824" />

   <img src="media/image4.png" width="824" />

   >**Talking Point**: And voila, just like that, we have created our Team Project. In the next screen, I can now import my source code in. For this demo, I will import my source code from github.

4. Enter **https://github.com/abelsquidhead/VSTSDemoKeynoteDemo1.git**. Click import. 

   <img src="media/image5.png" />

   >**Talking Point**: Let’s enter in the url to a github repo and that is all it takes to import our source code from github.

5. Click on Set up build.

   <img src="media/image6.png" width="824" />

   >**Talking Point**: After importing in our code, VSTS will take us to the repository page from here, we can easily create a build for our code. Let’s go ahead and create a build for our code.

6. Show the different build templates.

   <img src="media/image7.png" width="824" />

   >**Talking Point**: With the VSTS build system, you can build anything. Java, node.js, C#, swift, whatever you want.

7. Click **ASP.NET (PREVIEW)** and then click Apply.

   <img src="media/image8.png" width="824" />

   <img src="media/image9.png" width="824" />
   

   >**Talking Point**: We even have templates built out for common types of projects. Azure projects, android projects, iOS projects, node js. Any language, Any platform. In this demo, we need to create a build for an asp.net app. So let’s choose the ASP.NET template.

   <img src="media/image10.png" width="824" />

   >**Talking Point**: And that is literally all it takes for us to create a working build in VSTS. The build system in VSTS is a glorified task runner. It runs one task after another. Here is the list of tasks that the build will run. I wanted to point out that VSTS is updated multiple times per day. What that means is that new features are constantly lighting up. For instance, if we look at our Test Assemblies task, you’ll notice that it has a flag. This means that there are multiple versions of this task that you can choose from.

   <img src="media/image11.png" width="824" />

   >**Talking point**: If you click on the Version drop down, you can select the preview version 2 of this testing task.

8. Click Run only impacted tests, run tests in parallel on multi-core machines, Code coverage enabled.

   <img src="media/image12.png" width="824" />

   <img src="media/image13.png"  />

   >**Talking Point**: New for vsts, we have the ability to now use Code Coverage to calculate what lines of code have changed so what tests need to be run. Test Impact is now built into VSTS. Of course, we still have the ability to run tests in parallel and to gather code coverage information is just a checkbox.

9. Click Save & queue, select Save & queue. 

   <img src="media/image14.png" width="824" />

   Click on the Agent queue dropdown and select Hosted, then click Queue button.

   <img src="media/image15.png" />

   >**Talking Point**: Now let’s save and queue up this build, and this brings up the Queue build dialog where we can set queue time variables, and we can also choose what agents will perform our build. Out of the box, you can use your own private agents, or our hosted agents on windows and linux boxes. For this demo, we will go ahead and select a Hosted windows build. This way, we don’t even need to have any infrastructure in house to perform our builds.

10. Click the Edit button.

    <img src="media/image16.png" width="624" />

    >**Talking Point**: This will take you to a page where you can watch the build happen in real time. The build takes a while to complete, so while it’s executing, let’s look at some more features in build.

11. Click Add Task.

    <img src="media/image17.png" width="824" />

    >**Talking Point**: Like I said earlier, VSTS build is a glorified task runner, where it runs one task after another. If you want to add tasks, just click Add Task which will take you to a list of all the out of the box tasks.

12. Type azure in the search box. 

    <img src="media/image18.png" width="824" />

    >**Talking Point**: There are so many Tasks out of the box, we actually had to implement a search so we can find our tasks quickly. For instance, if I type Azure in the search, you can see all the azure tasks out of the box. Because we are Microsoft, we have super tight integration into Azure. Basically, anything you want to do in azure, we already have pre-built task that will let you perform those tasks easily.

13. Clear out the search. Then scroll and show the prebuilt tasks.

    <img src="media/image19.png" width="824" />

    >**Talking Point**: But it’s not just azure. We have prebuilt tasks that let you do java builds, android builds, ios builds, ftp files, manipulate NuGet etc.

14. Click on Check out our Marketplace.

    <img src="media/image20.png" width="824" />

    >**Talking Point**: But what if there’s something you want the build to do that doesn’t exist out of the box?. The first thing you should do is go check out the Markplace. Here, we’ve created an ecosystem where people can upload their custom build and release tasks.

    <img src="media/image21.png" width="824" />

    >**Talking Point**: See if someone has already created a task for you. If they have, just download it and start using it. If they haven’t, you can easily create your own custom task. Custom tasks are nothing more than powershell script or node.js. Bundle it together with any artifacts the task will need, upload it to VSTS and bam, just like that, you’ve created your own custom task. We have open sourced all of our build and release tasks. So if you want samples on how to do things, go to github and download any of our tasks to see how to best build a custom task for VSTS.

15. Go back to the build page. Click on the Variables tab. 

    <img src="media/image22.png" width="824" />

    >**Talking Point**: Now, all you need to do is drag and drop whatever tasks you need into the process. Next, you would fill in the parameters to the individual tasks. VSTS build also has the ability to set build variables including secret variables for things like passwords, connection strings etc. If you click on the lock and lock a variable, it will encrypt that variable both in place and in flight. Once locked, no one can unlock it and get the variables so build variables can be completely secured.

16. Click the Triggers Tab. 

    <img src="media/image23.png" width="824" />

    The triggers tab takes you to the screen that lets you determine when builds are triggered. You can trigger your builds manually, through Continuous Integration and even with a schedule.

17. Click the enable switch. 

    <img src="media/image24.png" width="824" />

    >**Talking point**: To turn on Continuous Integration, just flip the switch and chose which branch you want to monitor and build.

18. Click the Options tab.

    <img src="media/image25.png" width="824" />

    >**Talking Point**: The options tab lets you set build properties, build number format, lets you choose which build agents you use etc. It even allows you to create bug work item on build failure. We just made this build a CI build, which means every developer checkin will kick off a build. So we get a lot of build failures. This is perfectly fine and by design. Fail early and fail often right? However, often times, CI build failures get lost in the noise, so if we can automatically create a bug when a build fails, this bug will haunt the devs until they go back in and fix their build problems!

19. Click Retention tab.

    >**Talking Point**: VSTS builds also lets you determine how long you want to keep builds around.

20. Click History tab.

    <img src="media/image26.png" width="824" />

    >**Talking Point**: And VSTS tracks all changes you make to your build definition.

21. Click Save & Queue and select Save. Add a save comment **Initial save of build**.

    <img src="media/image27.png" width="824" />

    >**Talking Point**: If we save a build and give it a comment, you can see it show up in a list. You can also do diff’s between different build definitions and even roll your build definitions back to a prior build.

22. Click the ellipses next to an older build change.

    <img src="media/image28.png" width="824" />

    >**Talking Point**: You even have the ability to compare two build definitions and to roll back to a previous build definition.

23. Click on Summary, then click on the latest build that just completed.

    <img src="media/image29.png" width="824" />

    <img src="media/image30.png" width="824" />

    >**Talking Point**: Ok, let’s go back to our build, this brings us to our build summary page where we can see all the builds that have ran and if we click on an individual build, we are able to see the build details.

    <img src="media/image31.png" width="824" />

    >**Talking Point**: And from this build report, we’re able to see any build issues that happened, any work items associated to this build, who made what changes and why, the Test Results and also the Code Coverage. VSTS will even guide us through this DevOps process, and will notice that we don’t have a release for this build definition, and will provide us a link to do this.

24. Click the Create release link.

    <img src="media/image32.png" width="824" />

    >**Talking Point**: To create a release for this build, we will go ahead and click the Create release link.

25. Click Yes.

    <img src="media/image33.png"/>

    >**Talking Point**: This will bring up the Create release definition dialog that informs us no release definitions exist for this specific build definition and asks if we want to create a new one.

26. Click Yes.

    <img src="media/image34.png" />

    >**Talking Point**: This will bring up the Create release definition dialog that informs us no release definitions exist for this specific build definition and asks if we want to create a new one.

27. Select Azure App Service Deployment with Performance Test.

    <img src="media/image35.png"  />

    >**Talking Point**: And this brings us to a list of release templates we can use. Once again, because we are Microsoft, we have SUPER tight integration into Azure. Anything you want to do in Azure, we have prebuilt tasks that make the deployment simple. Because we are using a web app for this demo, we will select Azure App Service Deployment With Performance Test and click Next.

28. Click Build, Continuous deployment checkbox and Create button.

    <img src="media/image36.png"/>

    >**Talking Point**: The next screen asks us what build we want to use for this deployment. Out of the box, we support both VSTS builds (of course) and also Jenkins builds. You also have the ability to make this a Continuous Deployment by checking the CD checkbox.

    <img src="media/image37.png" width="824" />

    >**Talking Point**: And just like that, we create a deployment template. Here you can see our first task is to deploy our app to Azure. Because VSTS knows who I am, I can click the Azure Subscription drop down and it will show me all the Azure Subscriptions I am part of.

    <img src="media/image38.png" width="824" />

    >**Talking Point**: I’ll go ahead and pick one of my subscriptions, then click Authorize, and now I’m ready to start deploying my app to my azure subscription.

29. In App Service name, type in **$(WebsiteName)**.

    <img src="media/image39.png" width="824" />

    >**Talking Point**: For App Service name, I’m going to type in a Deployment Variable, that way, I can easily clone my environments and all I need to change are my deployment variables.

30. In App Service URL type in **WebsiteURL**.

    <img src="media/image40.png" width="824" />

    >**Talking Point**: For the AppService URL, this will return the actual URL that is deployed, and we will pass this to a release variable so we can use it elsewhere.

31. Click Add tasks.

    <img src="media/image41.png" width="824" />

    >**Talking Point**: One of the things I want to do is use a good DevOps practice called Infrastructure as Code, where right along side my source code, I’ve also defined what my infrastructure will look like and when I deploy, I also on the fly deploy my infrastructure. So in my source code, I have my infrastructure defined as an ARM template. To deploy my infrastructure to azure, let’s Add a task.

32. Click the Add button next to Azure Resource Group Deployment Task and click the Close button.

    <img src="media/image42.png" />

    >**Talking Point**: And select Azure Resource Group Deployment so before we deploy our web app, we deploy the Resource Group where the web app will be sitting in.

33. Drag and drop the Azure Deployment task to the top of the list.

    <img src="media/image43.png" width="824" />

    >**Talking Point**: This will add the task to the bottom of the list where we can now drag and drop it to the beginning of the list.

    <img src="media/image44.png" width="824" />

    >**Talking Point**: Now let’s select the right subscription, for the resource group let’s use our variable $(WebsiteName), for location, let’s choose Central US.

34. Click the Ellipses next to For Template and browse to **Linked Artifacts | AbelTestProj (Preview)-CI (Build) | drop | BikeSharing360.IaC | WebSite.json** (yours will look slightly different). And click the OK button.

    <img src="media/image45.png" width="824" />

    <img src="media/image46.png" />

    >**Talking Point**: For Template, it’s looking for the ARM template so let’s select the ellipses, where we can browse to our ARM template.

35. Click the Ellipses next to For Template and browse to **Linked Artifacts | AbelTestProj (Preview)-CI (Build) | drop | BikeSharing360.IaC | WebSite.parameters.json** (yours will look slightly different). And click the OK button.

    <img src="media/image47.png" width="824" /> 
                                                             
    <img src="media/image48.png"  />

    >**Talking Point**: Now for the template parameters, hit the ellipses and browse to the parameters file.

36. For Override template parameters type **-hostingPlanName $(WebsiteName)**. 

    <img src="media/image49.png" width="824" />

    >**Talking Point**: For the override template parameters, lets’s add in **-hostingPlanName $(WebsiteName)**.

    <img src="media/image50.png" width="824" />

    >**Talking Point**: Now let’s add our variable WebsiteName and WebsiteURL. In the Dev environment, click on the ellipses and select configure variables.

    <img src="media/image51.png" width="824" />

    >**Talking Point**: Click on +Variables, enter WebsiteName for name and Bikeshare360D for Value.

    <img src="media/image52.png" width="824" />

    >**Talking Point**: Click on +Variable and enter WebsiteURL with an empty value.

    <img src="media/image53.png" width="824" />

    >**Talking Point**: Now let’s configure our web performance test by clicking on it and and for Website URL we’ll add the parameter $(WebsiteURL) and for Test Name we’ll add HomepageTest.

    <img src="media/image54.png" width="824" />

    >**Talking Point**: Now that we have our dev environment set up, we can easily create our QA and Prod environment by clicking on Add environment and selectin Clone selected environment.

    <img src="media/image55.png" />

    >**Talking Point**: This brings up our Add new environment dialog where we can select approvers for the approval gates for this environment.  Each environment has two approval gates.  Into the environment and out of the environment.  You can add lists of people and every person on the list needs to approve in order to pass the gate.  Or you can assign groups of people and if one person in a group approves, it passes through the gate.  Or you can have a combination of lists and groups. For the demo, I’ll just add myself as a Pre-Deployment approver.  I’ll click on Specific users and add myself.

    <img src="media/image55.png" />

    >**Talking Point**: This will create the new environment.

37. Click on the name Copy of Dev and change it to QA. Click on the Ellipses and select configure variables and change BikeShare360D to BikeShare360QA and click OK.

    <img src="media/image57.png" width="824" />

    <img src="media/image58.png" width="824" />

    >**Talking Point**: Let’s change the name to QA, and then let’s change the parameter WebsiteName to BikeShare360QA.

38. Follow the previous instructions to create another cloned environment, name it Prod and change the WebsiteName variable to be BikeShare360P. Click Save.

    <img src="media/image59.png" width="824" />

    >**Talking Point**: Now let’s do the same thing and create a Prod environment and we will call the Website Name BikeShare360P and then lets save the release definition.

    <img src="media/image60.png" width="824" />

    >**Talking Point**: And now we have created a release definition.  Even though we have this set up so that any successful build will trigger this release, we can also release manually by clicking on the Release and selecting Create Release.

39. Click Create.

    <img src="media/image61.png"  />

    <img src="media/image62.png" width="824" />

    >**Talking Point**: This brings up the create new release dialog where we can choose the build we want to release and also the environments. Now we can watch the relase in realtime by clicking on the release and selecting Logs.

40. Click on the Ellipses next to the release definition name and select Edit.

    <img src="media/image63.png" width="824" />

    <img src="media/image64.png" width="824" />

    >**Talking Point**: Once again, this takes a while, so let’s go back to the release definition to see some more features. Just like the build, Release Management is a glorified task runner where you run one task after another. If you want to add or change the order of tasks, just click the Add tasks button.

41. Show the marketplace, then click Close.

    <img src="media/image65.png"/>

    >**Talking Point**: This brings up the task catalog where you can chose whatever out of the box tasks you want to execute.  Once again, because we are Microsoft, we have a ton of azure related tasks so whatever you want to do in azure, there are pre-built tasks in place for you.  Just like the build, if you want the release to do something that doesn’t exist out of the box, go to the market place and see if someone has created a release task that does what you want it to do.  If they have, download and use it.  And if they haven’t, create your own prebuild task.  Again, a custom task is nothing more than powershell script or node.js.  So if you can do something from the command line, you can make our build/release system do it too.  What that means is you legitimately can make this build and release system do whatever you want it to do.

42. Click on Releases.

    <img src="media/image66.png" width="824" />

    <img src="media/image67.png" width="824" />

    >**Talking Point**: Now let’s go back and see how our release is going. Double click the release. 

    <img src="media/image67.png" width="824" />

    >**Talking Point**: Here we can see our Release Summary.  We have Released into Dev and it’s now waiting for an approval before deploying into QA.  If we ran automated UI tests, you would be able to see them, the work items associated with this deployment and since we ran load tests, we can also see our load tests.

43. Browse to Azure Portal and click on Resource Groups. 

    <img src="media/image68.png" width="824" />

    >**Talking Point**: And just to prove that we actually did deploy into azure, let’s look at our azure portal.

44. Type in BikeShare360.

    <img src="media/image69.png" width="824" />

    <img src="media/image70.png" width="824" />

    >**Talking Point**: Now let’s filter our Resource Groups by BikeShare360. Now select the Bikeshare360D Resource Group.

45. Click on BikeShare360D app Service.

    <img src="media/image71.png" width="824" />

    >**Talking Point**: Here you can see we have created an app service plan, application insight and also the app service itself, select the appservice.

46. Now click the URL.

    <img src="media/image72.png" width="824" />

    >**Talking Point**: And here you can see, we deployed our app into our dev environment.
























