---
title: Custom Integration of GitLab System Hooks with Slack
date: 2023/8/8
description: Overcome default Slack integration limitations, enable user mentions, and streamline communication for increased productivity.
tag: Slack, Gitlab, Automation, GCP 
author: Alvian
---


### Introduction

  

In software development, efficient collaboration and streamlined communication are essential for successful project management. Integrating GitLab, a popular version control system, with Slack, a widely-used team messaging platform, can significantly enhance team productivity. However, the default Slack integration has some shortcomings, like the inability to mention GitLab users involved in specific actions. In this blog post, we'll explore a custom approach to bridge this gap by triggering merge request events, mapping user IDs, and enabling direct user mentions.

  

### Shortcoming of Default Slack Integration

The default Slack integration with GitLab lacks the ability to mention the specific GitLab users responsible for creating or reviewing merge requests (MRs). This limitation hinders effective communication within teams and makes it challenging to assign responsibilities or resolve issues promptly.

  

### Cost-Efficient On-Premise GitLab Setup

To save costs, our system does not set up email notifications on GitLab. While this approach can be cost-effective, it can also hinder communication and collaboration in the absence of timely notifications.

  
  

### Custom Approach to Slack Integration

To address the limitations of the default Slack integration, we developed a custom approach leveraging GitLab System Hooks and Slack's APIs. Here's a step-by-step guide to implementing this custom integration:

  

#### Step 1: Create Custom API on GCP Cloud Function
- Set up a Google Cloud Platform (GCP) account and navigate to Cloud Functions. ![Create Cloud Function](https://d1kkcsa3gp41aj.cloudfront.net/custom-integration-of-gitlab-system-hooks-with-slack-overcoming-limitations-for-mentioning-slack-user-with-default-gitlab-slack-integration/create-cf.png)
- Create a new function to handle incoming webhook payloads from GitLab.
- Transform the incoming data to extract relevant information such as user IDs, event types, and merge request details. [Gitlab merge request event hooks documentation](https://mekar-gitlab.com/help/administration/system_hooks#merge-request-events)
  
#### Step 2: Enable System Hooks on GitLab
- Log in to your GitLab account with administrative privileges.
- Go to "Settings" > "Webhooks" and select "System Hooks."
- Create a new webhook URL to send events to the designated endpoint with the value is url of the Google Cloud Function created on step 1. ![Enable Gitlab Hooks](https://d1kkcsa3gp41aj.cloudfront.net/custom-integration-of-gitlab-system-hooks-with-slack-overcoming-limitations-for-mentioning-slack-user-with-default-gitlab-slack-integration/enable-gitlab-hooks.png)

#### Step 3: Map User IDs on GitLab to Slack Member IDs

- Maintain a mapping between GitLab user IDs and their corresponding Slack member IDs. ![Mapping user id](https://d1kkcsa3gp41aj.cloudfront.net/custom-integration-of-gitlab-system-hooks-with-slack-overcoming-limitations-for-mentioning-slack-user-with-default-gitlab-slack-integration/user-id-mapping.png)
- Ensure the mapping remains updated to facilitate accurate user mentions.

#### Step 4: Process the Payload and Trigger Slack Mentions

- Within the custom Cloud Function, process the transformed data.
- For merge request events, use the user mappings to directly mention the relevant GitLab users involved in the request and the requester upon merging. ![Slack mention about merge request](https://d1kkcsa3gp41aj.cloudfront.net/custom-integration-of-gitlab-system-hooks-with-slack-overcoming-limitations-for-mentioning-slack-user-with-default-gitlab-slack-integration/slack-mr-mention.png)
  
### Conclusion

By implementing this custom integration between GitLab System Hooks and Slack, we have effectively overcome the shortcomings of the default Slack integration. This approach enables seamless communication and immediate user mentions for involved parties in merge requests, thereby enhancing collaboration and productivity within development teams. Remember to maintain the mapping between GitLab user IDs and Slack member IDs to ensure accurate and efficient mentions in your Slack channels. With this custom integration in place, your team can focus on building exceptional software while maintaining effective communication and collaboration throughout the development process.

### Disclaimer

It is important to note that the custom integration described in this blog post is tailored to our specific use case, where the engineering team comprises fewer than 10 users. This approach has been effective for our small team in terms of efficiently handling merge request events and direct user mentions on Slack.

For larger engineering teams, the scalability and performance of this custom integration may require further consideration. As the team size increases, maintaining an up-to-date mapping of user IDs and Slack member IDs can become more complex and time-consuming. Additionally, the processing and handling of incoming webhook payloads might require optimization to ensure timely and accurate user mentions in Slack channels.

Before implementing this custom integration, I recommend thoroughly assessing your team's specific needs, size, and technical requirements. Larger teams may benefit from more sophisticated solutions or third-party integrations that are better suited to handle communication at scale.