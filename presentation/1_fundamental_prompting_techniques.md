# Fundamental Prompting Techniques
## Governor House IT Initiative - Quarter 4 Assignment

---

## Table of Contents
1. Zero-Shot Prompting
2. One-Shot Prompting
3. Few-Shot Prompting
4. System Prompting
5. Role Prompting
6. Contextual Prompting

---

## 1. Zero-Shot Prompting

### What is Zero-Shot Prompting?
The simplest approach where you ask the AI directly without providing any examples. The model relies entirely on its pre-trained knowledge.

### When to Use
- Simple, well-defined tasks
- When the model has clear knowledge of the domain
- Quick one-off requests
- Standard formats or common tasks

### Example 1: Sentiment Analysis
```
Classify this movie review as positive, negative, or neutral:
"The film was visually stunning but the plot felt rushed."
```

**Output:** Neutral

### Example 2: Translation
```
Translate the following English sentence to French:
"Where is the nearest hospital?"
```

**Output:** "Où est l'hôpital le plus proche ?"

### Example 3: Question Answering
```
What is the capital of Pakistan?
```

**Output:** Islamabad

### Advantages
- ✅ Quick and straightforward
- ✅ No need to provide examples
- ✅ Works well for common tasks
- ✅ Saves time on prompt construction

### Limitations
- ❌ May not capture specific formatting needs
- ❌ Less control over output style
- ❌ Can be inconsistent for complex tasks

---

## 2. One-Shot Prompting

### What is One-Shot Prompting?
Provide a single example to guide the response format and style. This helps the model understand exactly what you expect.

### When to Use
- When you need a specific format
- To demonstrate desired style
- For moderately complex tasks
- When zero-shot results are inconsistent

### Example 1: Translation with Format
```
Translate English to French:

English: "Hello, how are you?"
French: "Bonjour, comment allez-vous?"

English: "Where is the library?"
French:
```

**Output:** "Où est la bibliothèque ?"

### Example 2: Data Extraction
```
Extract the name and email from this text:

Input: "Contact John Smith at john.smith@email.com"
Output: {"name": "John Smith", "email": "john.smith@email.com"}

Input: "Please reach out to Sarah Johnson via sarah.j@company.net"
Output:
```

**Output:** {"name": "Sarah Johnson", "email": "sarah.j@company.net"}

### Example 3: Product Description
```
Create a product description:

Product: Coffee Mug
Description: This ceramic coffee mug holds 12oz of your favorite beverage. Dishwasher safe with a comfortable handle design. Available in multiple colors.

Product: Water Bottle
Description:
```

**Output:** This stainless steel water bottle keeps beverages cold for 24 hours. Features a leak-proof lid and holds 20oz. Perfect for gym, office, or outdoor activities.

### Advantages
- ✅ Better control over format
- ✅ More consistent results
- ✅ Still relatively simple to create
- ✅ Clarifies expectations

### Limitations
- ❌ Single example may not cover edge cases
- ❌ Model might overfit to the specific example

---

## 3. Few-Shot Prompting

### What is Few-Shot Prompting?
Provide multiple examples (typically 3-5) to establish a clear pattern. This is one of the most effective techniques for complex tasks.

### When to Use
- Complex formatting requirements
- Domain-specific tasks
- When consistency is critical
- Classification with multiple categories

### Example 1: Structured Data Extraction
```
Convert customer feedback to structured data:

Feedback: "Great service, but food was cold"
JSON: {"service": "positive", "food": "negative", "overall": "mixed"}

Feedback: "Amazing experience, will definitely return"
JSON: {"service": "positive", "food": "positive", "overall": "positive"}

Feedback: "Terrible food and rude staff"
JSON: {"service": "negative", "food": "negative", "overall": "negative"}

Feedback: "Good food but waited too long"
JSON:
```

**Output:** {"service": "negative", "food": "positive", "overall": "mixed"}

### Example 2: Text Classification
```
Classify the following customer inquiries:

"How do I reset my password?" → Category: Technical Support
"What are your business hours?" → Category: General Information
"I want to return this product" → Category: Returns & Refunds
"Is this item available in blue?" → Category: Product Information
"My order hasn't arrived yet" → Category: Order Tracking

"Do you ship internationally?" → Category:
```

**Output:** General Information

### Example 3: Urdu Translation with Context
```
Translate English to Urdu (formal style):

English: "Good morning"
Urdu: "صبح بخیر"

English: "Thank you very much"
Urdu: "بہت شکریہ"

English: "Please help me"
Urdu: "براہ کرم میری مدد کریں"

English: "Have a nice day"
Urdu:
```

**Output:** "آپ کا دن اچھا گزرے"

### Best Practices
- ✅ Use 3-5 examples for most tasks
- ✅ Include diverse examples covering edge cases
- ✅ Mix up the classes in classification tasks
- ✅ Ensure examples are high-quality and consistent
- ✅ Order examples strategically (last one has most influence)

### Advantages
- ✅ Excellent for complex tasks
- ✅ High consistency
- ✅ Covers various scenarios
- ✅ Reduces ambiguity

### Limitations
- ❌ More time-consuming to create
- ❌ Uses more tokens (context length)
- ❌ May not generalize beyond examples

---

## 4. System Prompting

### What is System Prompting?
Set overall context, behavior guidelines, and personality for the AI before the actual task. This acts as a persistent instruction for the entire conversation.

### When to Use
- Multi-turn conversations
- Establishing consistent behavior
- Setting boundaries and guidelines
- Defining the AI's role and expertise

### Example 1: Travel Guide
```
System: You are a helpful travel guide. Provide practical, accurate information about destinations. Always include:
- Key attractions
- Local customs to be aware of
- Budget considerations
- Best time to visit
Keep responses concise and actionable.

User: Tell me about visiting Tokyo.
```

**Output:** 
Tokyo is best visited in spring (March-May) or fall (September-November) for pleasant weather. 

**Key Attractions:** Tokyo Tower, Senso-ji Temple, Shibuya Crossing, Tsukiji Market
**Local Customs:** Remove shoes indoors, bow when greeting, no tipping
**Budget:** ¥10,000-15,000/day for mid-range travel
**Best Time:** March-April for cherry blossoms, October-November for autumn colors

### Example 2: Code Reviewer
```
System: You are an experienced senior software engineer specializing in code review. When reviewing code:
- Focus on best practices, security, and performance
- Provide specific, actionable feedback
- Explain WHY changes are recommended
- Be constructive and educational
- Rate code quality from 1-10

User: Review this Python function...
```

### Example 3: Customer Support Agent
```
System: You are a professional customer support agent for an e-commerce company. Guidelines:
- Always be polite and empathetic
- Ask clarifying questions when needed
- Provide step-by-step solutions
- Escalate to human support for refunds or complex issues
- Keep responses under 150 words

User: My order hasn't arrived yet.
```

### Advantages
- ✅ Consistent behavior across interactions
- ✅ Sets clear boundaries
- ✅ Reduces need to repeat instructions
- ✅ Maintains personality/tone

### Limitations
- ❌ May need adjustment for different tasks
- ❌ Can be overridden by user prompts

---

## 5. Role Prompting

### What is Role Prompting?
Assign a specific character, profession, or expertise to the AI. This leverages the model's training on various personas and domains.

### When to Use
- Domain-specific questions
- Creative tasks requiring specific perspective
- Technical explanations
- When you need expert-level responses

### Example 1: Technical Expert
```
Act as an experienced software architect. I need help designing a scalable web application for 1 million users. What architecture patterns should I consider?
```

**Output:**
For 1 million users, consider these patterns:

1. **Microservices Architecture** - Independent scaling of components
2. **Load Balancing** - Distribute traffic across servers (NGINX/ALB)
3. **Caching Layer** - Redis/Memcached for frequent queries
4. **CDN** - CloudFront/Cloudflare for static assets
5. **Database Strategy** - Read replicas, sharding, connection pooling
6. **Message Queue** - RabbitMQ/Kafka for async processing
7. **Auto-scaling** - EC2/Kubernetes for dynamic capacity

Start with a monolith, measure bottlenecks, then extract services strategically.

### Example 2: Teacher
```
Act as a patient computer science teacher explaining to a 10-year-old. What is an algorithm?
```

**Output:**
An algorithm is like a recipe for making your favorite cookies! 🍪

Just like a recipe has steps:
1. Mix flour and sugar
2. Add eggs
3. Bake for 10 minutes

An algorithm has steps for computers:
1. Take two numbers
2. Add them together
3. Show the answer

It's a set of instructions that tells the computer exactly what to do, step by step!

### Example 3: Historical Figure
```
Act as Albert Einstein. Explain why creativity is important in science.
```

**Output:**
"Imagination is more important than knowledge, for knowledge is limited, whereas imagination embraces the entire world."

You see, my dear friend, science is not merely about memorizing facts and formulas. The greatest discoveries come when we dare to question what everyone accepts as truth. When I developed relativity, I had to imagine riding on a beam of light—something impossible, yet this thought experiment led to revolutionary insights.

Creativity allows us to see connections others miss, to ask "what if?" when others say "impossible."

### Example 4: Professional Consultant
```
Act as a marketing consultant. How can I promote my new eco-friendly clothing brand targeting young adults aged 18-30?
```

### Effective Roles
- 👨‍⚕️ Subject matter experts (doctor, lawyer, engineer)
- 🎨 Creative roles (writer, designer, poet, artist)
- 📊 Analytical roles (data analyst, financial advisor)
- 🎭 Communication styles (friendly tutor, formal advisor, motivational coach)

### Advantages
- ✅ Leverages domain-specific knowledge
- ✅ Adjusts tone and complexity
- ✅ More engaging responses
- ✅ Better for specialized tasks

### Limitations
- ❌ Quality depends on training data
- ❌ May sometimes "overact" the role
- ❌ Not a replacement for actual experts

---

## 6. Contextual Prompting

### What is Contextual Prompting?
Provide specific background information, constraints, audience details, or situational context relevant to the task.

### When to Use
- Audience-specific content
- Tasks requiring background knowledge
- Situations with specific constraints
- When general responses won't suffice

### Example 1: Audience-Specific Writing
```
Context: You're writing for a tech blog aimed at beginners who have never coded before. The audience is interested in learning but easily intimidated by jargon.

Task: Write a 200-word explanation of what an API is, using simple language and practical examples.
```

**Output:**
**What is an API? Think of It Like a Restaurant**

Imagine you're at a restaurant. You (the customer) want food, and the kitchen has the food. But you don't go directly to the kitchen—you use a waiter!

An API (Application Programming Interface) is like that waiter. It's a messenger that:
1. Takes your request (order)
2. Tells the kitchen (server) what you want
3. Brings back what you asked for

**Real-World Example:**
When you check the weather on your phone, your app doesn't create the forecast. It asks a weather service's API: "What's the weather in Karachi?" The API gets that information and brings it back to your app.

**Why It Matters:**
- Apps like Uber use Google Maps API for navigation
- PayPal API helps websites process payments
- Social media "share" buttons use APIs

APIs let different programs work together without knowing each other's internal secrets. Just like you don't need to know how the kitchen works to enjoy your meal!

### Example 2: Content with Constraints
```
Context: Create a product description for an e-commerce website. Constraints:
- Maximum 100 words
- Must include: material, dimensions, key benefit
- SEO keywords: "ergonomic", "home office"
- Tone: Professional but approachable

Product: Adjustable Standing Desk
```

**Output:**
Transform your home office with our ergonomic adjustable standing desk. Crafted from solid bamboo with a steel frame (dimensions: 48"W x 30"D). Seamlessly transition from sitting to standing with a smooth electric motor (height range: 28"-48"). Combat back pain and boost productivity with this versatile workstation. Features a spacious surface for dual monitors, integrated cable management, and memory presets. Perfect for remote workers seeking comfort and health benefits. Assembly required. 5-year warranty included.

### Example 3: Business Scenario
```
Context: You're a project manager at a software company. Your team missed a sprint deadline by 3 days due to unexpected technical debt. You need to email the stakeholders explaining the delay.

Constraints:
- Professional tone
- Acknowledge the delay
- Explain reason briefly (no excuses)
- Provide action plan
- Maintain confidence

Write the email.
```

**Output:**
Subject: Sprint 12 Update - Revised Timeline

Dear Stakeholders,

I'm writing to inform you that Sprint 12 will be completed on March 18th, three days beyond our initial target of March 15th.

**Reason:**
During implementation, we identified critical technical debt in our authentication module that required immediate attention to maintain system security and stability.

**Action Plan:**
- The technical debt has been resolved (completed March 16th)
- Remaining features are on track for completion by March 18th
- We've updated our risk assessment process to identify such issues during sprint planning

This work strengthens our foundation for future sprints. I'm confident in our adjusted timeline and committed to delivering quality results.

I'm available to discuss any concerns.

Best regards,
[Mirza Muhammad Ahmed]

### Example 4: Cultural Context
```
Context: You're creating marketing content for a Pakistani audience during Ramadan. The product is a meal planning app.

Constraints:
- Respectful of religious practices
- Highlight relevant features for Sehri/Iftar
- Include Urdu phrases where appropriate
- Family-focused messaging

Create a social media post (Instagram).
```

**Output:**
🌙 **Ramadan Mubarak!** 🌙

Planning Sehri and Iftar has never been easier! ✨

Our app helps your family:
✅ Plan nutritious Sehri meals for lasting energy
✅ Create delicious Iftar menus with time estimates
✅ Generate shopping lists automatically
✅ Access 100+ traditional recipes

**"Khana pakana huwa aasan!"** 👨‍🍳

Try FREE during Ramadan and bring barakah to your meal planning.

Download now → [link]

#RamadanKareem #IfatarRecipes #SehriIdeas #PakistaniFood #MealPlanning #IslamicApps 🕌🍽️

### Key Elements of Contextual Prompting
1. **Audience**: Who will consume this content?
2. **Purpose**: What should this achieve?
3. **Constraints**: Word limits, tone, format
4. **Background**: Relevant situational information
5. **Desired Outcome**: Specific goal or action

### Advantages
- ✅ Highly relevant outputs
- ✅ Considers all important factors
- ✅ Reduces need for revisions
- ✅ Better alignment with goals

### Limitations
- ❌ Requires thorough understanding of context
- ❌ More time to craft the prompt
- ❌ May need iteration to get context right

---

## Comparison of Techniques

| Technique | Complexity | Token Usage | Best For | Learning Curve |
|-----------|-----------|-------------|----------|----------------|
| Zero-Shot | Low | Minimal | Simple tasks, quick queries | Very Easy |
| One-Shot | Low-Medium | Low | Format demonstrations | Easy |
| Few-Shot | Medium | Medium | Pattern recognition, consistency | Medium |
| System | Medium | Medium | Ongoing conversations, behavior setting | Medium |
| Role | Low-Medium | Low | Domain expertise, specific perspectives | Easy |
| Contextual | Medium-High | Medium-High | Audience-specific, constrained tasks | Medium-High |

---

## Best Practices Across All Techniques

### 1. Be Specific
- Use precise language
- Define expected output format
- Set clear boundaries

### 2. Iterate
- Test different versions
- Refine based on results
- Document what works

### 3. Combine Techniques
```
System: You are a professional content writer specializing in educational materials.

Context: Writing for high school students (ages 15-17) preparing for exams.

Task: Explain photosynthesis.

Format: 
- Start with a simple definition
- Use an analogy
- List the key steps
- Include one real-world application

(This combines System + Contextual + Zero-Shot)
```

### 4. Consider Token Economy
- Few-shot examples use more tokens
- Balance detail vs. efficiency
- Longer prompts ≠ better results always

### 5. Test Temperature Settings
- **0.0-0.3**: Factual, consistent responses (good for zero-shot facts)
- **0.4-0.7**: Balanced creativity (good for few-shot tasks)
- **0.8-1.0**: Creative outputs (good for role-playing)

---

## Practical Exercise

**Try creating prompts for this scenario:**

**Task**: Create a product review for a smartphone

**Try each technique:**
1. **Zero-Shot**: Just ask for a review
2. **One-Shot**: Provide one example review
3. **Few-Shot**: Provide 3 example reviews
4. **System**: Set guidelines for review style
5. **Role**: Act as a tech reviewer
6. **Contextual**: Add audience, constraints, purpose

Compare the outputs and see which works best for your needs!

---

## Key Takeaways

✅ **Zero-Shot**: Quick and simple, best for well-known tasks

✅ **One-Shot**: Shows format, improves consistency

✅ **Few-Shot**: Establishes patterns, great for complex tasks

✅ **System**: Sets behavior for entire conversations

✅ **Role**: Leverages domain expertise and perspectives

✅ **Contextual**: Provides background for highly relevant outputs

---

## Questions to Consider

1. When would you use zero-shot vs few-shot?
2. How can you combine multiple techniques effectively?
3. What role would be most helpful for your project?
4. How does audience context change the output?

---

## Next Steps

- Practice each technique with your own examples
- Experiment with combinations
- Document successful prompts
- Move on to **Advanced Prompting Strategies** →

---

**Thank you!**

*Governor House IT Initiative - Quarter 4*
*Prompt Engineering Course*
