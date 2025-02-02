> By the end of this module, you'll gain experience in developing apps that use Firebase.

> Module videos:

* [Firebase Overview (+ web hosting demo) [18:04]](https://youtu.be/VQca8zxoHm8)
* [Firebase and Hosting/TensorFlow Demo [23:03]](https://youtu.be/L4zXFVVdx-k)
* [Firebase and Cloud Functions Demo [31:55]](https://youtu.be/WO2vrfYIDmo)
* [[External] What is Firebase [21:44]](https://www.youtube.com/watch?v=9kRgVxULbag)
* [[External] Cloud Functions for Firebase [2:22]](https://www.youtube.com/watch?v=vr0Gfvp5v1A)

<!-- > Module labs:

* [Qwiklabs - Build Apps & Websites with Firebase [20 credits]](https://www.qwiklabs.com/quests/148) -->

## Firebase

> * Module video: [Firebase Overview (+ web hosting demo) [18:04]](https://youtu.be/VQca8zxoHm8)
> * External video: [What is Firebase [21:44]](https://www.youtube.com/watch?v=9kRgVxULbag)

You will most likely have come across Firebase if you have ever dipped into the mobile or web development scene.  You can read all about its fascinating history (it used to be called Envolve) at various blogs ([here](https://hackernoon.com/introduction-to-firebase-218a23186cd7) and [here](https://www.geeksforgeeks.org/firebase-introduction/)), but what we are mainly interested in is how we can use it and how it can apply to cloud applications.

One important consideration is that Firebase is a group of services that can be used for backend development.  We won't be going into every single service that is offered (there are a lot), but will be looking into a handful that can be useful for you (and will point you towards resources that are helpful if you want to explore more).  Figure 1 shows the current list of services (as of Feb. 2021 anyway) that are supported by Firebase:

![Firebase Products](/CloudAppsDev/assets/images/14-products.png "Firebase Products")

> Figure 1: Firebase Products

You might notice some crossover with the Google Cloud services we've seen so far (e.g., Cloud Storage, Cloud Functions, and Cloud Firestore).  These products actually share a common infrastructure and as such are used by both technologies.  An advantage here is that you can save time by already being embedded within the ecosystem of either Google Cloud or Firebase; concepts like access control and billing are the same.  The disadvantage though is that you're tied to a particular ecosystem and it can be difficult to diversify yourself if need be (though you can still do things like reach out to third-party providers via Cloud Functions, for example).  More detail can be found [here](https://firebase.google.com/firebase-and-gcp/).  

> Generally though, if you're looking to make a mobile/web app you may want to start with Firebase, and if you're looking to work on the backend of some product you'll most likely start with Google Cloud (or similar).

Here is a quick overview of how Cloud Functions can tie in with Firebase:

> [[External] Cloud Functions for Firebase [2:22]](https://www.youtube.com/watch?v=vr0Gfvp5v1A)

The following image shows off some quick guides for various platforms.  Note that we're stepping outside our comfort zones here! You can set this up with Unity, with iOS, even with C++!  How nifty!

![Firebase Docs](/CloudAppsDev/assets/images/14-firebase-docs.png "Firebase Docs")

> Figure 2: Firebase Docs

### Firebase Features

Let's take a look at a couple of commonly-used features.  [This article](https://www.makeuseof.com/what-is-google-firebase-why-use-it/) provides a helpful source to dip into it.

**Hosting**

In the module videos (you hopefully already watched), we setup Hosting for our Firebase apps.  These spawn websites hosted by Firebase in a very straightforward manner -- no Apache / nginx setup or configuration required.  We spin up a local website on our local machines, connect it to Firebase, and have Firebase transfer the files upwards (by means of the `public` directory created in your local instance).  You get a generated domain name tied to Firebase, however it can be configurable if you want to set/pay for your own domain.

**Authentication**

To me, one of the most delightful aspects of Firebase apps involves the authentication.  You can **very** easily setup authentication with a multitude of OAuth-based systems, meaning that *you don't have to worry about authentication*!  Figure 3 shows a screenshot of the currently-available services.  The accounts registered with your service get added to your app's database, where you can easily manage users, roles, etc.

![Firebase Authentication Options](/CloudAppsDev/assets/images/14-Firebase-Auth.png "Firebase Authentication Options")

> Figure 3: Firebase Authentication Options

**Database**

There are two databases (currently) available for Firebase: [Firestore Database](https://firebase.google.com/docs/firestore) and [Realtime Database](https://firebase.google.com/docs/database).  Both are of the NoSQL variety (non-relational, document-based), however Realtime Database uses *data synchronization* for handling updates (i.e., if the data changes, all connected devices' views change), whereas Firestore must be queried for updates.  While common SQL commands won't work here, managing the JSON-based NoSQL databases is pretty straightforward.  The following image (via [Firebase Tips and Tricks](https://medium.com/firebase-tips-tricks/how-to-use-cloud-firestore-in-flutter-9ea80593ca40) shows an example of its representation:

![Firestore Database Example](https://miro.medium.com/max/4552/0*aLKZbmwrjqNNtVZw.jpg "Firestore Database Example")

> Firestore Database Example (c/o Peter Haddad@medium)

**Storage**

Last but certainly not least, we have Storage.  These are the Cloud Storage Buckets we have seen before (and yes, it uses the `gs://` pathing as well), where we can store our files in the cloud and reference them fairly easily.  Not a whole lot to go into here as we've worked with buckets before, but here is the Firebase-specific page!  [Firebase Storage](https://firebase.google.com/docs/storage) + [Firebase & Google Cloud: What’s different with Cloud Storage?](https://medium.com/google-developers/firebase-google-cloud-whats-different-with-cloud-storage-a33fad7c2b80) 

![Firebase Storage Example](https://miro.medium.com/max/3200/0*b0FqITXZJvls0BAH "Firebase Storage Example")

> Firebase Storage Example

### Linking up to the Cloud

This [Medium article](https://medium.com/firebase-developers/multi-tenant-applications-with-firebase-and-google-cloud-4d0d02b7d859) (hopefully not paywalled) describes an interesting use of Google Cloud and Firebase together.  Specifically, the focus is on *[multi-tenancy](https://www.redhat.com/en/topics/cloud-computing/what-is-multitenancy)*, or enabling a software instance to serve multiple groups of users.  Think of it as multiple users using cloud-based infrastructure at the same time (e.g., shared hosting, sharing resources, etc.).  Generally there will be some level of customization per user/user group as well.   We'll generally consider our SaaS as multi-tenant applications (whereas the general cloud environment can be considered PaaS).  In a cloud-based environment (such as Google Cloud) multi-tenancy is generally enabled via some sort of identify management framework to enable you to group users together.  This task is accomplished in Google Cloud via [Identity Platform](https://cloud.google.com/blog/products/identity-security/simplifying-identity-and-access-management-of-your-employees-partners-and-customers).  Figure 4 (c/o Google) shows how this framework is structured:

![Context-Aware Access High-Level Architecture](https://storage.googleapis.com/gweb-cloudblog-publish/images/Context-aware_access_high-level_architectu.max-1100x1100.png "Context-Aware Access High-Level Architecture")

> Figure 4: Context-Aware Access High-Level Architecture

Figure 5 (again from Google) shows how multi-tenancy is supported via grouping users into the Google Cloud Identity Platform (GCIP):

<img style="background:#fff" src="https://storage.googleapis.com/gweb-cloudblog-publish/images/customer-of-customer_authentication_structur.max-600x600.png" alt="An example customer-of-customer authentication structure" title="An example customer-of-customer authentication structure" />

> Figure 5: An example of customer-of-customer authentication structure

Here you can see how you are creating *silos* of users, where a silo can represent customer groups, employee categories, etc.  In this environment each tenant (again, user group) has its own (list [c/o Google](https://cloud.google.com/blog/products/identity-security/multi-tenancy-support-identity-platform-now-generally-available)):

> * Unique identifier
> * Users
> * Identity providers and authentication methods
> * Auditing and Cloud IAM configuration
> * Quota allocation
> * Identity Platform usage breakdown

How does this factor in with Firebase?  GCIP can be used programmatically via Firebase to perform tasks such as managing tenants, creating flows for access rights, and possibly onboarding new customers.  Generally, the concept of multi-tenancy is necessary as your organizational needs scale and you need to go from managing single users to groups of users.  

Here is a code listing based on the Medium article above (and hosted as [open-source on Github](https://gist.github.com/hiranya911/9ee933ba2233c49c76cf8dbe35a1df3d#file-create_tenant-go)).  This snippet creates a new tenant using Firebase and Google Cloud (in Go) with specifics for their email configuration:

```go
// https://gist.github.com/hiranya911/9ee933ba2233c49c76cf8dbe35a1df3d#file-create_tenant-go
import (
  "context"
  "log"

  firebase "firebase.google.com/go"
  "firebase.google.com/go/auth"
)

// Initialize the Admin SDK
ctx := context.Background()
app, err := firebase.NewApp(ctx, nil)
if err != nil {
  log.Fatalf("error initializing Firebase SDKt: %v\n", err)
}

// Create a new auth.Client instance
client, err := app.Auth(ctx)
if err != nil {
  log.Fatalf("error initializing auth client: %v\n", err)
}

config := (&auth.TenantToCreate{}).
  DisplayName("ABC Auto Distributors").
  EnableEmailLinkSignIn(true).
  AllowPasswordSignUp(true)

// Access tenant management APIs via client.TenantManager
tenant, err := client.TenantManager.CreateTenant(ctx, config)
if err != nil {
  log.Fatalf("error creating tenant: %v\n", err)
}
```

Most of the code above is administrative in nature, however there are a few interesting blocks.  Towards the end you see a `config :=` block.  This section sets the tenant's name to `ABC Auto Distributors` (this is for onboarding a car dealership to a larger organization) and giving that account access to email sign-in with password sign-up enabled.  What is happening here is that we are programmatically assigning access rights to a group of users (said car dealership).  Users can be added/removed from this tenant and gain the same rights as those already assigned (think of how you might assign users to groups and then assign permissions to those groups in a server-based environment; the principle is similar).

## Examples!

Here are a pair of videos demonstrating some Firebase tasks.  First we'll go through basic hosting and then add in some machine learning (c/o TensorFlow.js):

> * Module video: [Firebase and Hosting/TensorFlow Demo [23:03]](https://youtu.be/L4zXFVVdx-k)
> * [Codelab](https://codelabs.developers.google.com/codelabs/tensorflowjs-firebase-hosting-model)
> * [Issue with NodeJS mentioned in the video](https://timjrobinson.com/fixing-node-gyp-permission-denied-when-running-as-root/)

And here is a long-winded example of hooking up Firebase with Cloud Functions to make a chat application that also scans posted images for adult/violent content (note I couldn't get the final step of the Codelab working):

> * Module video: [Firebase and Cloud Functions Demo [31:55]](https://youtu.be/WO2vrfYIDmo)
> * [Codelab](https://firebase.google.com/codelabs/firebase-cloud-functions)

## A quest!

Homework here!  This will walk you through all the various facets of Firebase!

> * [Cloud Skills Boost Course - Firebase (see Blackboard)](https://www.cloudskillsboost.google/course_templates/649?catalog_rank=%7B%22rank%22%3A1%2C%22num_filters%22%3A1%2C%22has_search%22%3Atrue%7D&search_id=30526248)

## Additional Resources

* [Firebase](https://firebase.google.com/)
* [Firebase Documentation](https://firebase.google.com/docs?authuser=0)
* [Firebase and Google Cloud](https://firebase.google.com/firebase-and-gcp/)
* [Introduction to Firebase](https://hackernoon.com/introduction-to-firebase-218a23186cd7)
* [Firebase - Introduction](https://www.geeksforgeeks.org/firebase-introduction/)
* [What is Firebase?](https://www.makeuseof.com/what-is-google-firebase-why-use-it/)
* [Multi-Tenant Applications with Firebase and Google Cloud](https://medium.com/firebase-developers/multi-tenant-applications-with-firebase-and-google-cloud-4d0d02b7d859)
* [Google Guide](https://cloud.google.com/build/docs/deploying-builds/deploy-firebase)
* [Firebase Tips and Tricks](https://medium.com/firebase-tips-tricks/how-to-use-cloud-firestore-in-flutter-9ea80593ca40)
* [Firebase & Google Cloud: What’s different with Cloud Storage?](https://medium.com/google-developers/firebase-google-cloud-whats-different-with-cloud-storage-a33fad7c2b80) 

<hr size="1" />

*Where noted, the original content was provided by Google LLC and modified for the purpose of the course, without input or endorsement from Google LLC*.
