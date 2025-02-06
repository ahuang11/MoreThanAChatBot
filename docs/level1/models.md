# LLM Models

## Proprietary Models

Proprietary models are developed and maintained by specific companies or organizations. They often come with advanced features, optimizations, and support, but may require a subscription or usage fees.

!!! warning "Privacy Notice for Proprietary Models"
    All interactions with proprietary models are typically sent to and stored on company servers. Do not share sensitive data such as:

    - Personal identifying information
    - Private company data
    - Confidential research
    - Protected health information
    - Financial data
    - Authentication credentials
    
    For sensitive data, consider using [open source models](#open-source-models) that can be run locally instead.

### GPT-4-Mini

Provider: [OpenAI ChatGPT](../providers/#openai-chatgpt)

General purpose, decent context length, cheap, and fast.

Good for:

1. Quick research note organization and summarization
2. Basic code debugging and documentation
3. Initial research question brainstorming
4. Literature search query refinement

### Gemini 1.5 Deep Research

Provider: [Google Gemini](../providers/#google-gemini)

General purpose, very long context length, but requires a paid subscription.

Good for:

1. Searching multiple research papers simultaneously
2. Finding subtle connections across large bodies of research
3. Deeper literature reviews

### Gemini 2.0 Flash

Provider: [Google Gemini](../providers/#google-gemini)

General purpose, very long context length, free (at the current moment), and extremely fast.

Good for:

1. Real-time data analysis feedback during experiments
2. Rapid research presentation preparation
3. Quick validation of methodology sections
4. Interactive exploratory data analysis

### Claude 3.5 Sonnet

Provider: [Anthropic Claude](../providers/#anthropic-claude)

Excels at coding, long context length, but limited messages.

Good for:

1. Complex research software architecture design
2. Write, edit, and execute code with sophisticated reasoning and troubleshooting capabilities

### Mistral Large

Provider [Mistral](../providers/#mistral-ai)

Excels at multi-modal, long context length, and fast. Has free tier.

Good for:
1. Blazing-fast responses (~1000 words/sec)
2. Advanced document & image analysis
3. Local code execution & data exploration
4. Top-tier image generation model

## Open Source Models

Open source models make their weights, architecture, and training code publicly available. They can be run locally on personal hardware or deployed to cloud infrastructure. Most implementations use techniques like quantization to reduce model size and memory requirements. Common formats include GGUF (formerly GGML) and AWQ for efficient deployment.

Advantages:

- Complete control over model deployment and inference
- Ability to fine-tune or modify the model for specific use cases
- No usage fees beyond infrastructure costs
- Privacy benefits since data stays local
- Community-driven improvements and customizations

You can use these models through [offline gateways](../gateways#offline).

### Deepseek R1 70B

Provider: [Deepseek](../providers/#deepseek)

Good at reasoning, long context length, and free.

Good for:

1. Theoretical research development
2. Complex mathematical problem-solving
3. Research methodology validation
4. Hypothesis refinement and testing

### Qwen 2.5 Coder 7B

Provider: [Qwen](../providers/#qwen)

Good at coding, decent context length.

Good for:

1. Efficient research automation scripts
2. Data preprocessing pipelines
3. Statistical analysis implementations
4. Scientific visualization code

### Mistral Small 24B

Provider: [Mistral AI](../providers/#mistral-ai)

Good at reasoning, decent context length.

Good for:

1. Logical argument analysis
2. Experimental design critique
3. Research bias identification
4. Methodology comparison
