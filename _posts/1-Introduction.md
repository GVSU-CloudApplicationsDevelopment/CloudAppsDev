Welcome to Cloud Application Development!  This module will introduce you to the basics of cloud computing.

***

> By the end of this module, you should understand the underlying concepts of cloud computing, be able to setup your GCP account and billing, and create and use a remote virtual machine.

> Module videos:
> * [Google - What is the cloud? [42:36]](https://www.youtube.com/watch?v=JtUIQz_EkUw)
> * [Intro to the Cloud [8:14]](https://youtu.be/AtRZiBrxKnI)
> * [Cloud Billing [8:24]](https://youtu.be/V4hIVODKm20)
> * [Cloud Computing Costs [14:40]](https://youtu.be/huFVLTuPbrs)
> * [Cloud Providers [7:46]](https://youtu.be/NvYXa7RM658)
> * [Lab 1 Overview (Setup / Virtual Machines) [21:31]](https://youtu.be/IImFXvMWzM8)
> * [Lab Environments [8:36]](https://youtu.be/PEjyIlvl-88)

> Module labs:
> * Getting to know you (Internal to Blackboard)
> * [CIS680 Lab 1 - Intro. to Google Cloud](https://gvsu-cloudapplicationsdevelopment.github.io/CloudAppsDev/codelabs/CIS680-Lab1-Setup/)

*** 

For this course we will be using [Google Cloud Platform](https://cloud.google.com/) as our cloud provider, however others such as [Amazon Web Services (AWS)](https://aws.amazon.com/) and [Microsoft Azure](https://azure.microsoft.com/) are common as well.  While each provides their own particular flavor, understanding the basics should enable you to transition between one and the other as necessary.

Plus, assuming you are registered for the course at GVSU, you will receive free cloud computing credits (contact me on Blackboard).  If you somehow stumbled across this you can get [free credits via Google](https://cloud.google.com/free), however you're on your own with those.

What is the cloud?  [Put this lovely video on in the background and listen to it! [42:36]](https://www.youtube.com/watch?v=JtUIQz_EkUw)

> Note, this material is liberally based upon the materials provided by [Google's Cloud Computing Fundamentals course](https://edu.google.com/programs/cloud-computing-curriculum/?modal_active=none).

## What is Cloud Computing?

> Module Video: <a href="https://youtu.be/AtRZiBrxKnI" target="_blank">Intro to the Cloud [8:14]</a>

Hi there!  For this course I'm going to assume you have some base knowledge of what cloud computing is in theory.  You'll be getting a lot of practice to flesh that out! If not, watch the 'What is the cloud' video above!

To summarize, there are approximately five fundamental characteristics for cloud computing (c/o Google).  This list will most likely evolve over time (much like the 5 V's of Big Data have somehow become thirty-something), however they present a nice starting point:

![Five fundamental characteristics](/CloudAppsDev/assets/images/1-characteristics.png "Five fundamental characteristics")

> Figure 1: Five fundamental characteristics

One of the core benefits is that the cloud computing resources are (generally) always online.  They are *on-demand* and *self-service*, meaning that the user/customer does not need to worry about the massive infrastructure necessary to support it.  You get the benefits of the service without the configuration!

They are also accessible (over a network) from any location, generally via some sort of API call or browser interface.

Scalability is a lovely feature as well.  Consumers are allocated resources for their project via a large pool of available resources, scaling as necessary to meet the needs of the project.  Moreover, this scalability is available wherever the resources are, worldwide.  You select the region and you receive the resources at that location, enabling geographic considerations as well.  For example, if you wanted a load-balanced web server, you could host it at a location near your clients and provide secondary access points at other locations (where traffic would be routed based on how overworked the servers are or by geographic location of your clients).

Elasticity is another cloud feature, meaning that you can easily scale upwards and downwards as necessary.  You pay for what you use, no matter how large or how small the workload.  Once you shut off or disable the resource, you no longer have to pay (unless if it is some sort of persistent storage).

## Cloud Computing Costs

> Module Video: <a href="https://youtu.be/V4hIVODKm20" target="_blank">Cloud Billing [8:24]</a>

> Module Video: <a href="https://youtu.be/huFVLTuPbrs" target="_blank">Cloud Computing Costs [14:40]</a>

The most important concept to understand about cloud computing is that it is **not** free.  Each moment a virtual machine is on, each API call, each image access in a storage bucket will cost money.  

Repeat after me:

**CLOUD COMPUTING IS NOT FREE.**

Unless if you are running a business with unlimited funds, you don't want to see charges start to accrue on your account that could be avoided.  That means:

1. Shut down your virtual machine when you are done.

    Here is a screenshot of an Ubuntu 20 virtual machine with a default configuration.  Note how much it costs to run monthly.  **This is the cost for simply leaving the machine up and running**, i.e., TURN IT OFF WHEN YOU'RE DONE.

    ![GCP cost calculator](/CloudAppsDev/assets/images/1-costs.png "GCP cost calculator")

    > Figure 2: Cost Calculator

2. Set up stringent access rights to all your API calls, cloud functions, etc.
3. Do not publish any access keys, API ID's, passwords, etc. to version control (e.g., GitHub, BitBucket, etc.).  Keep in mind that if you *accidentally* push something identifiable that it can be **easily discovered** by checking commit history.  
4. Set *quotas* for your users to ensure that they don't accidentally drain your account!

## Google Cloud vs. AWS vs. Azure

> Module Video: <a href="https://youtu.be/NvYXa7RM658" target="_blank">Cloud Providers [7:46]</a>

There are several players in the game (i.e., the battle for cloud dominance) as of this point, however the big three are Google, Microsoft, and Amazon.  Whichever you end up using is more than likely going to come down to enumerating a list of tradeoffs, business decisions, and personal preferences.  

As of December 2020, AWS owns an astonishing 62% of the cloud market, with Microsoft (Azure) coming in at 20% and Google (GCP) with 12%.  

> *Source: [https://medium.com/weekly-webtips/google-cloud-vs-aws-vs-azure-bafb554e036](https://medium.com/weekly-webtips/google-cloud-vs-aws-vs-azure-bafb554e036)*

Really, there isn't one "good" answer for which you should pick.  We'll now list out some considerations for you to ponder.

### Cloud Provider Considerations

![Gartner Report - Cloud Market Share](/CloudAppsDev/assets/images/Cloud-Gartner-report.png "Gartner Report - Cloud Market Share")

> Figure 2: Cloud Market Share

Considerations consistently change with respect to cloud providers.  Here, I am going to very briefly summarize some of the pros and cons for the big three providers with a massive caveat that these points can and will change.  

> *Source: [https://www.datamation.com/cloud-computing/aws-vs-azure-vs-google-cloud-comparison.html](https://www.datamation.com/cloud-computing/aws-vs-azure-vs-google-cloud-comparison.html)*

**Amazon Web Services**

* Pros:
  - Existing dominance in market
  - Mature and enterprise-ready
  
* Cons:
  - Can have a higher cost than competitors

**Microsoft Azure**

* Pros:
  - Pre-existing familiarity with Microsoft products (e.g., Windows Server, Sharepoint, Active Directory, etc.)
  - Tightly-coupled with Microsoft ecosystem

* Cons:
  - Issues with enterprise-readiness
  - Technical support problems

**Google Cloud**

* Pros:
  - Success with containers/orchestration
  - Prominent in research-oriented areas (e.g., machine learning, big data analysis)
  - Massive scale
  - *Works well with education (cough cough)*
* Cons:
  - Tend to be a 'secondary partner' as they not as prominent in the cloud game

## Qwiklabs Options

Before we get into the lab, let's talk a little bit about [Qwiklabs](https://www.qwiklabs.com/).  By now, you should've received credits from Qwiklabs (separately from Google Cloud!).  Qwiklabs are self-guided labs that walk you through a particular topic, where each lab is essentially a self-contained instance.  Essentially each Qwiklab is sandboxed in that whatever you create lives and dies within that particular instance.

The reason we're talking about them here is that later on in this class you'll have to go through some for homework, however you're more than welcome to start digging into them now if you want to learn a particular topic (or want a different perspective on the topic at hand).  A neat thing with Qwiklabs is that some of them use AWS instead of Google Cloud.

At present we were not able to get free credits for AWS (you can sign up for the free tier, however that's a "forever" thing and I'd rather not burn out your accounts on class projects), but if you want experience in that realm feel free to make use of the credits!

## Term Projects

Hey, we'll do a term project too!  You should start thinking early about the type of project you'd like to work on.  The overall plan for the semester is to walk through some of the more commonly-used cloud technologies, building up in complexity as we go.  You'll have some build-up assignments to get you moving forward on it (propose an idea, demonstrate progress, etc.), however I'd like you to start constructing an idea sooner rather than later to shoot towards.

At present, you should be able to flip through all the topics we'll be going through.  Perhaps you want to make the next great scheduling application, or the world's best browser-based MMO, or even a Zoom usurper.  You have access to the *entirety* of Google Cloud at your disposal here, so feel free to have fun with it!  What I am looking for are **attainable** proofs-of-concept, not necessarily fully-polished and production-ready applications.  It should demonstrate your experience and knowledged gained throughout the semester.  There will be requirements for the number of separate services to include, however you need your grand idea to get started.  

## Google Cloud Account Setup (Lab)

> Module Video: <a href="https://youtu.be/IImFXvMWzM8" target="_blank">Lab 1 Overview (Setup / Virtual Machines) [21:31]</a>

> (Another) Module Video: <a href="https://youtu.be/PEjyIlvl-88" target="_blank">Lab Environments [8:36]</a>

Time for your first lab assignment!  This will get you up and running with a Google Cloud account, walk you through the web interface, and have you create a web server.  

**Ensure you download the lab manual from Blackboard!**

Click here for your first lab: [CIS680 Lab 1 - Intro. to Google Cloud](https://gvsu-cloudapplicationsdevelopment.github.io/CloudAppsDev/codelabs/CIS680-Lab1-Setup/)

## Additional Resources
* [Google Cloud Platform](https://cloud.google.com/)
  * [Free credits via Google](https://cloud.google.com/free)
* [Amazon Web Services (AWS)](https://aws.amazon.com/)
* [Microsoft Azure](https://azure.microsoft.com/)
> [Google Cloud vs AWS vs Azure](https://medium.com/weekly-webtips/google-cloud-vs-aws-vs-azure-bafb554e036)

---

*Where noted, the original content was provided by Google LLC and modified for the purpose of the course, without input or endorsement from Google LLC*.