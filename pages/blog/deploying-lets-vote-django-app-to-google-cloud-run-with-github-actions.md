---
title: Deploying "Lets Vote" Django App to Google Cloud Run with GitHub Actions
date: 2023/8/19
description: Journeying through the deployment of the "Lets Vote" app, this article details the strategic choice of using Google Cloud Run, the familiar yet challenging terrain of GitHub Actions, and the unique hurdles faced with the deployment process.
tag: Github Action, Python, Django, CI/CD, Lets Vote
author: Alvian
---


After the success of building "Lets Vote" through pair programming with ChatGPT, the next logical step was deployment. Having used GitHub Actions before, I knew its capabilities, but this deployment presented its own unique set of challenges.

### Google Cloud Run: A Strategic Choice

Why Cloud Run? Two reasons. Auto-scaling and cost-efficiency. In an era where app traffic is unpredictable, paying only for the compute resources I use was a winning proposition. Additionally, Cloud Run’s ability to automatically scale as per user demand fit perfectly with what "Lets Vote" needed.

### GitHub Actions and My Experience

I had used GitHub Actions before and was fairly comfortable with its workflow. So, I began by setting up the deployment process in `.github/workflows/cloudrun.yml`, ensuring it met the specific needs of "Lets Vote".

In terms of security, I took a more advanced route than the usual JSON key method for authentication. I followed the current best practice by adopting the Workload Identity Provider. This choice provided my Cloud Run service with its own unique identity, significantly boosting security. It also removed the necessity for long-term credentials, relying instead on short-lived identity tokens for interactions with Google Cloud services. This made sure that the sensitive parts of my project were well-protected.

### Challenges with Workload Identity Provider

The configuration of Google's Workload Identity Provider was more difficult than I had expected. After nearly 20 attempts at getting the settings right, I turned to extensive documentation, tried multiple configurations, and consulted with other developers in online communities.

**Setting up identity provider to connect with github screenshooted
Trial and error to filling the right value format screenshooted**

### Setting Up Service Account Permissions

Configuring the correct permissions for the service account turned out to be a puzzle. Each misconfiguration presented a new error in the CI/CD pipeline, requiring me to act as a detective, tracing back steps, understanding the issue, and resolving it one by one.
**screenshot of what went wrong each step
the final listed permissions required screenshooted**

### The Final Deployment

When "Lets Vote" was finally live on Google Cloud Run, it felt like a significant achievement. Beyond just deploying an app, it was a journey filled with challenges, learning, and persistence.
**the final cloudrun.yaml source screenshooted**

### Looking Forward: The Next Adventure

With "Lets Vote" successfully deployed on Google Cloud Run, I am gearing up for the next chapter of this saga - load testing. The app has been built, and now, it's time to put it to the test. But that, dear reader, is a tale for another day.

### Conclusion

This experience reinforced the idea that every project, regardless of how familiar the tools might seem, has something new to teach. Overcoming the challenges with the Workload Identity Provider and the service account permissions provided valuable lessons. For anyone considering a similar deployment, be prepared for challenges, but also for the immense learning and satisfaction that comes with solving them.

The process of bringing "Lets Vote" to Google Cloud Run, with all its highs and lows, has been nothing short of enlightening. As I eagerly look forward to sharing the results of the load tests, I take a moment to appreciate the lessons learned, the challenges overcome, and the knowledge gained in this deployment chapter.


