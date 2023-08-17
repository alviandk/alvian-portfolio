---
title: ChatGPT Writes Tests and Transforms Pair Programming
date: 2023/8/17
description: The saga continues. Dive into ChatGPT's remarkable capabilities in crafting automated Django tests in the latest pair programming journey.
tag: ChatGPT, Python, Unit Testing, Django 
author: Alvian
---


## Continuing the Pair Programming Saga

Recall the exhilarating experience I previously shared about [pair programming](https://alviandk.com/blog/pair-programming-with-chatgpt-navigating-code-challenges-together) with ChatGPT? I was left marveling at the AI's ability to assist developers in real-time, providing precise solutions that truly worked. Yet, it seems that ChatGPT has more tricks up its sleeve! My recent interaction with it plunged me into a new discovery: ChatGPT can also craft comprehensive automated tests. And they're impressive!
![Running Django Tests](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/running-tests.png)

## A Glimpse into the Testing Magic

Prompted by curiosity, I asked ChatGPT: can it write tests for Django? Specifically, for its models and views? As a refresher, Django models are the backbone of the data structure and represent the database layer. On the other hand, views are the presentation layer, crucial for the user experience.

ChatGPT rose to the challenge with flair!

### Testing Django Models

With just a simple prompt, essentially asking ChatGPT to "write tests for these models", it swiftly returned a comprehensive suite of tests.
![Prompt Asking Test for Models](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/model-prompt.png)

[Models source](https://github.com/alviandk/Lets-Vote/blob/main/votes/models.py)

ChatGPT's tests for the models went beyond my expectations. It didn’t just stop at testing the standard fields and relationships. It ventured into the custom methods within the models, reflecting a profound understanding of the Django ORM. ![Result Test for Models](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/model-result.png)

The most impressive part of the test for me is on the testing method part. Since the method is a custom implementation, I am intrigued how on earth ChatGPT can understand the expected result of the method. Seems like ChatGPT is understanding the full context of the chunk of code I've pasted.
![Test models method](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/method-models-tests.png)

[Test models source](https://github.com/alviandk/Lets-Vote/blob/main/votes/test_models.py)

### Testing Django Views

The views in Django are pivotal as they bridge the user with the backend. ChatGPT’s tests for these views considered both the sunny day and rainy day scenarios. It validated expected responses and gracefully handled exceptions, ultimately delivering an end-to-end test suite for the Django app.

#### The Prompt![Prompt Asking Test for Views](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/views-prompt.png)

[Views source](https://github.com/alviandk/Lets-Vote/blob/main/votes/views.py)

#### The Result

These tests encompassed positive scenarios and negative cases – a holistic coverage that one might spend hours to achieve manually.
![Result Test for Views](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/views-result.png)

#### Negative Scenario

Line of code 32 `test_vote_view_without_choice_id` function and Line of code 39 `test_vote_view_with_nonexistent_choice_id` function are covering the negative scenario tests. They are covering test without choice_id and test with nonexistent choice_id scenarios.
![Negative scenario Test for Views](https://d1kkcsa3gp41aj.cloudfront.net/chatgpt-writes-tests-and-transforms-pair-programming/negative-view-tests.png)

[Test views source](https://github.com/alviandk/Lets-Vote/blob/main/votes/test_views.py)

## Beyond Testing - ChatGPT’s Expanding Capabilities

While my recent exploits with ChatGPT centered around automated testing, it's evident that its abilities are vast. From aiding in deployment scripts, optimizing databases, to now churning out automated tests, ChatGPT is an ever-evolving powerhouse in the developer’s toolkit.

## Wrapping Up

Reflecting on the journey, I find myself increasingly in awe of what ChatGPT brings to the table. What could sometimes be hours of pondering over the right test cases, ChatGPT streamlined into moments. It's an AI revolution, and I’m here for it!

If you're navigating the world of tech, I highly recommend diving into ChatGPT. Whether you’re seeking a programming companion or a tester, it's got you covered.