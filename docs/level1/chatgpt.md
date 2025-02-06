# ChatGPT

## What is ChatGPT?

You might remember the day back in Novemeber 2022 when our data world, as we knew it, changed. News headlines appeared announcing the launch of ChatGPT, a generative artificial intelligence chatbot developed by OpenAI.

### ChatGPT Interface:
![image](https://github.com/user-attachments/assets/031040e2-4dcb-4e4f-a04d-9213435c5995)

### How does ChatGPT work?
![image](https://github.com/user-attachments/assets/19c70f63-5890-4dd3-b251-5635d4c0303c)

To use CHatGPT, create an account, and let's dive into some conservation examples!


## What prompts should I use?

As a "Generative Pre-Trained Transformer" (the GPT part of ChatGPT), the more specific your prompt, the better.

For example, the ***New York Times*** wrote about an example where ChatGPT outperformed doctors at diagnosing illness because ChatGPT used entire patient histories. <https://www.nytimes.com/2024/11/17/health/chatgpt-ai-doctors-diagnosis.html>  
![image](https://github.com/user-attachments/assets/c48ba71f-71bd-4fb2-a23d-9ff7ee5fa015)

Like in medicine, what if you want to use ecological data to make an important conservation decision?

**This introduces the importance of how you use prompts in large language models.**

### Some examples
- **Poor:**
  ![image](https://github.com/user-attachments/assets/7cf46749-7780-4938-8541-7a48caa749ca)

- **Better:**  
  ![image](https://github.com/user-attachments/assets/7b3035a2-c228-4e4e-a5c9-cac52fa6897b)

## Prompt Guides

Check out these guides for promting large language models:

Prompt engineering overview: <https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/overview>  
![image](https://github.com/user-attachments/assets/2c8fa5bc-82a4-455e-bcc3-3378e5111c12)

Prompt engineering: <https://platform.openai.com/docs/guides/prompt-engineering>  
![image](https://github.com/user-attachments/assets/dd793f5b-b8bb-4b8f-828d-63226d36d268)


## Environmental Example

**Extracting Water Rights from 100s of pdfs**

Imagine you're a scientist in California who needs to create a data set on water quality rights. You've downloaded pdfs from the [eWRIMS Database](https://www.waterboards.ca.gov/waterrights/water_issues/programs/ewrims/). But alas, all of the information you need are in the scanned pages of long pdfs. How do you quickly extract this information without it taking all day (or week) to do manually? Let's use ChatGPT to help us.

There are multiple ways to go about this, but let's look at a summary of one pdf. This can help with a general overview of the content:  
![image](https://github.com/user-attachments/assets/bac32db6-9692-4ecf-a338-f7246b2a5132)  
There are more details ChatGPT spits out too.

Next, let's make an output file of important inofrmation:  
![image](https://github.com/user-attachments/assets/835fab5a-4fe9-43e9-bc11-a4cb57065944)

Now, let's further refine the output to give more specifics that we want:  
![image](https://github.com/user-attachments/assets/80ae61f7-37c6-48cb-90eb-ad2ad76aff0d)

Hooray! We have the columns we need. Now, you have a framework to use to extract this information from all your other pdfs.

Eventually, you may run into this error with a free account and uploads, which is a limitation.  
![image](https://github.com/user-attachments/assets/c2f67c25-d7e9-4483-9546-b9da90ae4aee)

Instead of uploading pdfs, you may want to give ChatGPT all of the links to the documents instead.

Note that ChatGPT **may be wrong!**  
For example strawberry actually has 3 letters, not 2!  
![image](https://github.com/user-attachments/assets/bc7bae70-55c8-4794-a52c-c199eefaa967)  
See how this output compares with DeepSeek [on our other example tab](https://ahuang11.github.io/MoreThanAChatBot/level1/deepseek/).

It's always good to validtate the output. In the example above, you may want to manually check pdf inputs along the way and refine your prompts accordingly. Play around with your prompts, and harness the power of large language models for good. Happy prompting!
