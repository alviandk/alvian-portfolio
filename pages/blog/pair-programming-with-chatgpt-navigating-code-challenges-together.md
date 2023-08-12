---
title: Pair Programming with ChatGPT – Navigating Code Challenges Together
date: 2023/8/12
description: Exploring the future of coding collaboration, I paired up with OpenAI's ChatGPT to tackle a Django challenge, discovering a dynamic and efficient way to enhance the development process.
tag: ChatGPT, Python, Backend Developer, Django 
author: Alvian
---


**Introduction**

Ever wondered if it's possible to do pair programming without another human? Well, it is. And it's not as futuristic as you might think. Let's explore a recent experience I had with OpenAI's ChatGPT.


**The Challenge**

Recently, I've been heavily relying on ChatGPT to enhance my workflow. On this particular occasion, I embarked on creating a simple app geared towards blogging about load testing Python applications with Kubernetes. 

I need to develop a simple app for the load test object. So, I was creating a Django project with a feature to calculate the vote percentage for a list of choices associated with a question. Sounds simple, right? However, while the logic was relatively straightforward, getting it to play nicely with Django's ORM was the real challenge.

Driven by a mix of curiosity and, let's be honest, a bit of laziness, I threw my challenge to ChatGPT. I presented it with the Django model snippets and pondered if it could do the heavy lifting for me. To my amazement, ChatGPT rose to the occasion, delivering a tailored solution that fit seamlessly into my existing code!


**Enter ChatGPT**

For those unfamiliar, ChatGPT is a variant of the GPT (Generative Pre-trained Transformer) models from OpenAI. But instead of generating stories or answering questions, its primary focus is engaging in interactive conversations.

I turned to ChatGPT for assistance with my Django challenge, and it was like having a real-time coding buddy. The dialogue began with an overview of the existing models. I showed the bot the `Question`, `Choice`, and `VoteChoice` models and expressed my intention.



**A Dialogue of Iterations**

The essence of our collaboration with ChatGPT revolved around continuous iterations. Here's a brief breakdown of how our dialogue unfolded:

**The Dataset:** Imagine we have a dataset where three users voted. Two of them chose the first choice, while one went for the second choice. ![The Data](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/the-data.png)

**Laying Down the Foundations: The Django Models**

I initiated the conversation by providing ChatGPT with the foundational Django models that encapsulated the voting system:


```
class Question(BaseModel):
    text = models.CharField(max_length=255)

    def __str__(self):
        return f'{self.id}: {self.text}'

class Choice(BaseModel):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    text = models.CharField(max_length=255)

    def __str__(self):
        return f'{self.id}: {self.text}'

class VoteChoice(BaseModel):
    question = models.ForeignKey(Question, on_delete=models.CASCADE)
    choice = models.ForeignKey(Choice, on_delete=models.CASCADE)

    def __str__(self):
        return f'{self.question.text} {self.choice.text}'
```
        

This structure presents a simple voting mechanism, where `Question` defines the poll, `Choice` lists out the possible voting options, and `VoteChoice` captures the actual choices made by the participants.

**Initial Interaction:** ChatGPT initially provided a correct, yet not entirely efficient solution. It correctly calculated the percentage based on the given example, but the solution involved multiple queries.
![First Solution](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/first-solution.png)

**Refinement 1: Consolidation:** Recognizing the need to reduce database hits, I nudged ChatGPT towards making the calculations using a single query. It's always a balancing act between readability and optimization, but in this context, efficiency was a priority.
![Single Query Solution](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/single-query-solution.png)

**Refinement 2: Targeted Querying:** Next, we dove deeper into optimization. Instead of querying all fields, I expressed the need to fetch only the necessary ones. This not only speeds up the query but also reduces memory usage, a crucial aspect for scalable applications. ![Optimized Query Solution](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/optimized-query.png)

**Final Refinement: Integration:** The final step was to make the solution more reusable. I asked ChatGPT to integrate the optimized logic into the `Question` model as a method. This encapsulation ensures that any time we need the voting percentages, it's just a method call away, keeping the main codebase clean and readable. ![Integrated Query Solution](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/integrated-solution.png)

To give you a tangible sense of the outcome, I'll be sharing screenshots of the API percentage results. It's a testament to the precision and applicability of the solution we crafted together. Remember, it's not just about getting the right answer, but getting it in a way that seamlessly integrates into your existing infrastructure, and ChatGPT did just that. ![API Result](https://d1kkcsa3gp41aj.cloudfront.net/pair-programming-with-chatgpt-navigating-code-challenges-together/api-result.png)


**The Optimization Journey**

What stood out was not just the delivery of a correct solution, but the drive towards optimization. After I pointed out the need to make the query more efficient, ChatGPT promptly incorporated `values_list` into the solution, reducing both memory usage and data transfer.

**Code Repository on GitHub**

For those who are curious about the complete code, I've uploaded it to a GitHub repository. There you can find the full implementation, along with other related components of the project. This repository provides a practical hands-on look at the discussed solution and will be a valuable resource for anyone looking to implement a similar feature in Django. [https://github.com/alviandk/Lets-Vote](https://github.com/alviandk/Lets-Vote) 

**Conclusion: Pair Programming with AI**

Pair programming is traditionally a human-human activity. However, with advancements like ChatGPT, the definition is expanding. The experience underscored a few things:

1.  **Interactive Feedback Loop:** Just like with a human partner, the interactive feedback loop is essential. The capacity to instantly react to a proposed solution and guide the conversation made the entire experience productive.
    
2.  **Incremental Progress:** ChatGPT didn't land on the perfect solution immediately. There were iterations, underscoring the essence of real-world development – it’s a journey, not a destination.
    
3.  **Learning Opportunity:** Just like in a pair programming session with a colleague, I walked away having learned something new about Django's ORM and query optimization.
    

In the landscape of development, AI isn't just a tool to get answers. It's becoming a collaborative partner, ready to engage in the iterative, sometimes messy, but always rewarding process of coding.

Pair programming with AI doesn't replace the human touch, but it adds a new dimension to the coding journey, making it a tool every developer should consider having in their toolkit.