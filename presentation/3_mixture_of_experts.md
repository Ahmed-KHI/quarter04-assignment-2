# Mixture-of-Experts (MoE) and Prompt Engineering
## Governor House IT Initiative - Quarter 4 Assignment

---

## Table of Contents
1. What is Mixture-of-Experts (MoE)?
2. How MoE Works
3. Key Components of MoE
4. MoE in Modern LLMs
5. How MoE Changes Prompt Engineering
6. Best Practices for MoE Models
7. Practical Examples
8. Troubleshooting MoE Models

---

## 1. What is Mixture-of-Experts (MoE)?

### Definition
Mixture-of-Experts (MoE) is a machine learning architecture that divides complex tasks among specialized "expert" neural networks. Instead of using the entire model for every input, MoE activates only relevant experts, making it more efficient while maintaining high performance.

### The Restaurant Analogy 🍽️

Imagine a large restaurant with specialist chefs:

**Traditional Model (Dense):**
- One master chef cooks EVERYTHING
- Makes pizza, sushi, biryani, pasta, desserts
- Always working at full capacity
- Slower and more expensive

**MoE Model:**
- Multiple specialist chefs
- Pizza chef, sushi chef, biryani chef, pasta chef, dessert chef
- A coordinator (router) decides which chef handles each order
- Only 1-2 chefs work at a time
- Faster and more efficient

### Why MoE Matters

**Without MoE (Dense Models like GPT-3):**
```
Input: "Calculate 2+2"
→ Activates ALL 175 billion parameters
→ Uses full computational power
→ Expensive, slower
```

**With MoE (Like GPT-5, Grok):**
```
Input: "Calculate 2+2"
→ Router identifies: "This is math"
→ Activates only the Math Expert (~20B parameters)
→ Other experts stay inactive
→ Faster, cheaper, same quality
```

### Key Advantages

✅ **Efficiency**: Only 10-20% of parameters activate per input
✅ **Scalability**: Can have trillions of parameters but run like a smaller model
✅ **Specialization**: Experts become highly skilled in specific domains
✅ **Cost-Effective**: Lower inference costs despite larger total size

---

## 2. How MoE Works

### The MoE Architecture

```
INPUT: "Explain quantum physics in Urdu"
         |
         ↓
    [ROUTER/GATING NETWORK]
         |
         ↓
   Router analyzes input and decides:
   - This needs Physics Expert
   - This needs Language Expert (Urdu)
   - This needs Explanation Expert
         |
         ↓
    Activates 2-3 out of 16 experts
         |
         ↓
   [Expert 1: Physics]
   [Expert 7: Urdu Language]
   [Expert 12: Explanations]
         |
         ↓
   Combine their outputs
         |
         ↓
   FINAL OUTPUT: "کوانٹم فزکس وہ سائنس ہے..."
```

### Step-by-Step Process

**Step 1: Input Processing**
- User provides a prompt
- Input is tokenized
- Tokens are converted to embeddings

**Step 2: Routing Decision**
- Gating network analyzes tokens
- Assigns probability scores to each expert
- Selects top-k experts (usually k=2 or k=3)

**Step 3: Expert Execution**
- Only selected experts process the input
- Each expert produces an output
- Outputs are weighted by router probabilities

**Step 4: Output Combination**
- Weighted outputs are combined
- Final response is generated
- Unused experts remain dormant (saving compute)

### Mathematical Representation

For each input `x`:

```
1. Router computes probabilities:
   p₁, p₂, p₃, ..., pₙ = Router(x)

2. Select top-k experts (e.g., top-2):
   Selected: Expert₃ (p₃=0.7), Expert₇ (p₇=0.3)

3. Weighted output:
   Output = 0.7 × Expert₃(x) + 0.3 × Expert₇(x)
```

---

## 3. Key Components of MoE

### A. Experts

**What Are They?**
- Specialized sub-networks (feed-forward neural networks)
- Each trained to handle specific types of data or tasks
- Typically 8-256 experts per layer

**Example Specializations:**
- Expert 1: Mathematics and calculations
- Expert 2: Creative writing
- Expert 3: Code generation (Python)
- Expert 4: Code generation (JavaScript)
- Expert 5: Urdu language
- Expert 6: Arabic language
- Expert 7: Medical knowledge
- Expert 8: Legal knowledge
- ...and so on

**Real Example - Mixtral 8x7B:**
- Has 8 experts per layer
- Each expert has 7B parameters
- Total: 47B parameters
- Active per input: ~14B parameters (2 experts)

### B. Gating Network (Router)

**Purpose:**
- Decides which experts to activate
- Acts like a traffic controller
- Learned during training

**How It Works:**
```python
# Simplified pseudocode
def router(input_tokens):
    # Analyze input
    scores = compute_expert_scores(input_tokens)
    
    # Get top-k experts
    top_experts = select_top_k(scores, k=2)
    
    # Normalize weights
    weights = softmax(top_experts.scores)
    
    return top_experts, weights
```

**Routing Example:**

Input: "Write a Python function to calculate factorial"

```
Router Analysis:
- "Python" → Triggers Programming Expert
- "function" → Triggers Code Structure Expert
- "calculate" → Triggers Math Expert
- "factorial" → Reinforces Math Expert

Router Decision:
✅ Expert 3 (Python): 0.65 weight
✅ Expert 9 (Math): 0.35 weight
❌ All other experts: Inactive
```

### C. Sparse Activation

**Concept:**
Unlike dense models where all parameters work on every input, MoE activates only a small fraction.

**Comparison:**

| Model Type | Total Parameters | Active Parameters | Efficiency |
|------------|------------------|-------------------|------------|
| GPT-3 (Dense) | 175B | 175B (100%) | Low |
| Mixtral 8x7B (MoE) | 47B | ~14B (30%) | High |
| Grok-1 (MoE) | 314B | ~86B (27%) | High |
| GPT-5 (Speculated MoE) | ~2T | ~400B (20%) | Very High |

**Benefits:**
- ⚡ Faster inference
- 💰 Lower computational cost
- 🔋 Reduced energy consumption
- 📊 Can scale to massive sizes

---

## 4. MoE in Modern LLMs (2025)

### Leading MoE Models

#### GPT-5 (OpenAI) - Speculated
- **Total Parameters:** ~2 trillion (estimated)
- **Active per Token:** ~400B (20%)
- **MoE Status:** Likely (not officially confirmed)
- **Specialization:** Dynamic routing for different reasoning levels
- **Performance:** 74.9% on SWE-bench (coding tasks)

#### Grok 4 (xAI)
- **Total Parameters:** ~500B
- **Active per Token:** Sparse activation
- **MoE Status:** ✅ Confirmed (multi-agent architecture)
- **Specialization:** Expert count undisclosed
- **Performance:** 16.2% on ARC-AGI with Thinking Mode

#### Gemini 2.5 Pro (Google)
- **Total Parameters:** Undisclosed
- **MoE Status:** ✅ Confirmed
- **Specialization:** Advanced reasoning capabilities
- **Features:** Optimized for efficiency and scaling

#### DeepSeek-V3
- **Total Parameters:** 671B
- **Active per Token:** 37B (5.5%)
- **MoE Status:** ✅ Confirmed (DeepSeekMoE)
- **Architecture:** Multi-Head Latent Attention (MLA)
- **Training:** 14.8T tokens for ~$5.6M (highly efficient)
- **Performance:** Competitive with leading models on MMLU, SWE-bench

#### Claude 4 (Anthropic)
- **MoE Status:** ❌ Unknown (likely dense)
- **Parameters:** ~400B (estimated)
- **Note:** Claude 3.5 doesn't use MoE

---

## 5. How MoE Changes Prompt Engineering

### The Fundamental Shift

**Traditional (Dense) Models:**
```
Your Prompt → Entire Model Processes It → Output
(Prompt quality matters, but routing doesn't)
```

**MoE Models:**
```
Your Prompt → Router Analyzes → Selects Experts → Output
(Prompt quality + Expert Selection both matter)
```

### Key Insight
**Small wording changes can steer which experts wake up.**

Because the router chooses experts based on your tokens, your prompt directly influences which specializations activate.

---

### Change #1: Expert-Aware Prompting

#### The Problem
Vague or broad prompts might route to generic experts, leading to mediocre outputs.

#### The Solution
Design prompts to signal specific domains, helping the router select specialized experts.

#### Example 1: Math Problem

**Generic Prompt (may misroute):**
```
Solve 2x + 3 = 7
```

**Expert-Aware Prompt (routes to Math Expert):**
```
Using algebraic expertise, solve the equation:
2x + 3 = 7

Show step-by-step work.
```

**Why It Works:**
- "algebraic expertise" signals Math Expert
- "step-by-step" reinforces structured reasoning
- Higher chance of activating the right expert

#### Example 2: Code Generation

**Generic Prompt:**
```
Create a function to sort data
```

**Expert-Aware Prompt:**
```
Role: Senior Python Developer
Task: Implement a function that sorts a list of dictionaries by a specified key

Requirements:
- Handle missing keys gracefully
- Support ascending/descending order
- Include type hints and docstring

Language: Python
```

**Why It Works:**
- "Python Developer" → Routes to Python Expert
- "function", "type hints", "docstring" → Code Expert
- Clear language specification prevents multi-language confusion

#### Example 3: Multilingual Content

**Generic Prompt:**
```
Translate: "Good morning"
```

**Expert-Aware Prompt:**
```
Language: Urdu
Style: Formal
Task: Translate the following English phrase to Urdu:

English: "Good morning"
Urdu:
```

**Why It Works:**
- "Language: Urdu" → Routes to Urdu Language Expert
- "Formal" → Sets appropriate style expert
- Clear structure prevents mixing languages

---

### Change #2: Enhanced Chain-of-Thought with MoE

MoE's expert specialization amplifies the benefits of CoT prompting because different steps can activate different experts.

#### Example: Multi-Domain Problem

**Prompt:**
```
Scenario: A Pakistani e-commerce startup wants to expand to Saudi Arabia.

Analyze this step by step:
Step 1: Market analysis (use business expertise)
Step 2: Legal requirements (use legal expertise)
Step 3: Cultural considerations (use cultural expertise)
Step 4: Financial projections (use financial expertise)
```

**What Happens with MoE:**
```
Step 1: Router activates → Business Analysis Expert + Regional Market Expert
Step 2: Router activates → Legal Expert + International Law Expert
Step 3: Router activates → Cultural Expert + Middle East Expert
Step 4: Router activates → Financial Expert + Projection Modeling Expert
```

Each step gets the most relevant experts, improving quality across the entire response.

#### Traditional CoT:
```
"Let's think step by step..."
(Single expert handles everything)
```

#### MoE-Optimized CoT:
```
"Let's break this down with domain expertise at each step:

Step 1 (Business Analysis): ...
Step 2 (Legal Compliance): ...
Step 3 (Cultural Fit): ...
Step 4 (Financial Modeling): ...
```

**Result:** Each step leverages specialized experts, improving overall quality.

---

### Change #3: Handling Variability and Consistency

#### The Challenge
MoE routing can introduce variability. The same prompt might activate slightly different experts across runs (especially with temperature > 0), leading to inconsistent outputs.

#### Solutions

**1. Use Lower Temperature**
```
Temperature: 0.0 or 0.1
(Reduces randomness in both generation AND routing)
```

**2. Add Explicit Constraints**
```
You are a [specific role]. Maintain [specific style] throughout.

[Your task here]
```

**3. Use Self-Consistency**
Run the same prompt 3-5 times and select the most common answer (especially for critical tasks).

**4. Provide Strong Domain Anchors**
```
Expert Domain: Financial Analysis
Perspective: Risk-averse investor
Task: Evaluate this startup pitch
```

---

### Change #4: Efficiency in Prompt Design

#### MoE Advantage: Shorter, Focused Prompts Can Be Better

**Why:**
- Clear, concise prompts help the router make better decisions
- Verbose prompts can confuse routing
- Early tokens have the most influence on expert selection

#### Bad (Verbose, Confusing):
```
So, I was thinking, you know, like, about this thing where I need to, um, calculate something related to, you know, percentages and stuff, like if I have this discount situation...
```

**Good (Clear, Focused):
```
Calculate the final price:
- Original price: $100
- Discount: 20%
```

**Best (Expert-Aware + Concise):
```
Math problem:
Original price: $100
Discount: 20%
Final price: ?
```

#### Front-Load Domain Signals

Put the clearest task and domain cues in the **first few lines** to help the router lock onto the right experts early.

**Example:**
```
Role: Financial Analyst
Task: 10-K variance analysis
Output: Tabular summary + bullet risks

[Then provide context/data]
```

---

### Change #5: Avoid Multi-Domain Confusion

#### The Problem
Mixing multiple unrelated domains in one prompt can cause router confusion, leading to:
- Oscillating between experts
- Suboptimal expert activation
- Lower quality outputs

#### Example of Confusion

**Bad Prompt (Mixes Domains):**
```
Write Python code to scrape legal documents about marketing strategies and visualize them in Arabic.
```

**What Happens:**
```
Router struggles:
- "Python code" → Programming Expert?
- "legal documents" → Legal Expert?
- "marketing strategies" → Marketing Expert?
- "visualize" → Data Viz Expert?
- "Arabic" → Arabic Language Expert?

Result: Router activates generic experts or oscillates
```

#### Better Approach: Separate Tasks

**Step 1:**
```
Role: Python Developer
Task: Create a web scraper for PDF documents
Output: Python code with BeautifulSoup
```

**Step 2:**
```
Role: Legal Analyst
Task: Identify key clauses in legal documents
Context: [Scraped documents]
```

**Step 3:**
```
Role: Marketing Strategist
Task: Extract marketing insights from documents
Context: [Previous analysis]
```

**Step 4:**
```
Role: Data Visualization Expert
Language: Arabic
Task: Create visualization of insights
```

---

## 6. Best Practices for MoE Models

### DO MORE OF THIS ✅

#### 1. Front-Load Domain Signals
Put the clearest task and domain cues **at the beginning** of your prompt.

**Example:**
```
✅ Role: Financial analyst
✅ Task: 10-K variance analysis
✅ Output: Tabular summary + bullet risks

[Then provide data]
```

#### 2. Use Domain-Specific Vocabulary
The router keys off tokens. Use clear, on-topic terms instead of clever phrasing.

**Bad:**
```
❌ "Help me with number stuff for my shop"
```

**Good:**
```
✅ "Perform financial analysis for retail business:
- Revenue projections
- Cost breakdown
- Profit margins"
```

#### 3. Separate Mixed Tasks
If combining coding, legal, and marketing, break into sequential steps.

**Bad:**
```
❌ "Create a legal-compliant marketing dashboard in Python"
```

**Good:**
```
✅ Step 1: Define legal compliance requirements
✅ Step 2: Design marketing dashboard layout
✅ Step 3: Implement in Python
```

#### 4. Match Examples to Task
Few-shot examples should be in the **same domain, format, and language** as your goal.

**Example:**
```
Task: Generate Urdu product descriptions

Example 1 (Urdu product description):
"یہ پروڈکٹ..."

Example 2 (Urdu product description):
"یہ سروس..."

Now create: [Your product]
```

#### 5. Be Explicit About Language and Style
```
✅ Language: Urdu
✅ Style: Formal, technical
✅ Audience: IT professionals
✅ Length: 200-250 words
```

Multilingual MoE models often have language-specialized experts.

#### 6. Stabilize When Consistency Matters
```
✅ Temperature: 0.0
✅ Top-p: 0.9
✅ Provide strong role/context
```

#### 7. Keep RAG Context Clean
In Retrieval-Augmented Generation:
```
✅ Put task summary BEFORE documents
✅ Keep documents on-topic
✅ Remove noisy/irrelevant passages
```

Noisy context can misroute tokens.

---

### DO LESS OF THIS ❌

#### 1. Avoid Vague Indirection
```
❌ "You know what I mean..."
❌ "Something like that thing we discussed..."
❌ "Help me with that stuff..."
```

Weakens routing signals.

#### 2. Don't Bury the Task
```
❌ [500 words of context]
    [Finally, the actual task at the end]
```

Early tokens matter most for routing.

#### 3. Don't Mix Formats in One Prompt
```
❌ "Write code + poetry + SQL query + legal analysis"
```

Split it into separate prompts.

#### 4. Avoid Ambiguous Examples
Few-shot examples from different domains confuse the router.

```
❌ Example 1: Math problem
❌ Example 2: Creative writing
❌ Example 3: Code
Now solve: [Math problem]
```

---

## 7. Practical Examples

### Example 1: Code Review (MoE-Optimized)

**Prompt:**
```
Role: Senior Python Code Reviewer
Expertise: Performance optimization, security, best practices
Task: Review the following Python function

Code:
def process_users(users):
    result = []
    for user in users:
        if user['active'] == True:
            result.append(user['name'])
    return result

Output Format:
1. Issues found (with severity)
2. Specific recommendations
3. Improved code
```

**Why This Works:**
- Clear role signals Programming + Python Expert
- "Performance", "security" signals specific sub-experts
- Structured output format guides response

---

### Example 2: Multilingual Content (MoE-Optimized)

**Prompt:**
```
Language: Urdu
Audience: Pakistani small business owners (age 30-50)
Style: Simple, encouraging, practical
Task: Write a 150-word guide on starting social media marketing

Output Structure:
- Opening (motivational)
- 3 key steps
- Closing (call to action)
```

**Why This Works:**
- Explicit language directive → Urdu Expert
- Audience context → Appropriate complexity
- Style guidelines → Tone Expert
- Structure → Ensures completeness

---

### Example 3: Business Analysis (MoE-Optimized)

**Prompt:**
```
Role: Business Strategy Consultant
Industry: SaaS startups
Task: Analyze product-market fit

Context:
- Product: AI resume builder
- Target: Pakistani fresh graduates
- Price: Rs. 1000 for premium features

Analysis Framework:
Step 1: Market size estimation
Step 2: Problem validation
Step 3: Solution fit assessment
Step 4: Competitive landscape
Step 5: Revenue model viability
Step 6: Final recommendation

Use Pakistani market data where applicable.
```

**Why This Works:**
- Clear role and industry → Business Expert
- Structured analysis → Guides expert through steps
- Context specificity → Activates relevant regional knowledge
- Framework → Each step may activate different experts

---

### Example 4: Mixed Task - Done Right

**Bad Approach (Single Confused Prompt):**
```
❌ Create a Python script that analyzes legal contracts and generates Urdu summaries with sentiment visualization
```

**Good Approach (Sequential, Clear):**

**Prompt 1:**
```
Role: Python Developer
Task: Create a script to extract text from PDF legal contracts
Requirements:
- Use PyPDF2 or pdfplumber
- Handle multi-page documents
- Return clean text

Output: Python code only
```

**Prompt 2:**
```
Role: Legal Analyst
Task: Identify key clauses in this contract

Contract Text: [Output from Prompt 1]

Output Format:
- Parties involved
- Key obligations
- Payment terms
- Termination clauses
- Risk factors
```

**Prompt 3:**
```
Role: Translator
Source: English legal text
Target: Urdu (formal)
Task: Translate the following legal summary

[Output from Prompt 2]

Requirements:
- Maintain legal terminology accuracy
- Formal tone
- 150-200 words
```

**Prompt 4:**
```
Role: Data Visualization Expert
Task: Create sentiment visualization code

Data: [From Prompt 2]
Output: Python code using matplotlib/seaborn
Style: Professional, clean
```

---

## 8. Troubleshooting MoE Models

### Problem 1: Inconsistent Answers Across Runs

**Symptoms:**
- Same prompt gives different quality results
- Sometimes gets it right, sometimes doesn't

**Solutions:**
✅ Add sharper domain anchors at the top
✅ Reduce temperature to 0-0.2
✅ Include one very short, in-domain example
✅ Use more specific vocabulary

**Example Fix:**
```
Before:
"Explain photosynthesis"

After:
Role: Biology Teacher (High School Level)
Topic: Photosynthesis
Style: Simple explanation with examples
Temperature: 0.1

Explain photosynthesis.
```

---

### Problem 2: Model "Misses" Required Skill

**Symptoms:**
- Asked for math, got general text
- Asked for code, got pseudo-code
- Asked for formal tone, got casual

**Solutions:**
✅ Use explicit skill tags
✅ Show target format in tiny example
✅ Front-load the skill requirement

**Example Fix:**
```
Before:
"Write a proof for the Pythagorean theorem"

After:
Task Type: Mathematical proof (rigorous)
Level: University undergraduate
Style: Formal mathematical notation

Prove the Pythagorean theorem:
- Use geometric approach
- Include diagram description
- Show all steps
```

---

### Problem 3: Mixed-Topic Responses

**Symptoms:**
- Answer contains unrelated information
- Switches between topics mid-response

**Solutions:**
✅ Split the request into steps
✅ Ask for plan first, then execute
✅ Use section headers

**Example Fix:**
```
Before:
"Analyze this startup pitch covering business model, tech stack, and market opportunity"

After:
Role: Startup Analyst
Task: Comprehensive pitch analysis

Please analyze in this exact order:

Section 1: Business Model Analysis
[Wait for completion]

Section 2: Technology Stack Evaluation  
[Then continue]

Section 3: Market Opportunity Assessment
[Then continue]
```

---

## Routing-Friendly Prompt Template

### Universal Template for MoE Models

```
System/Intro:
  Role: <domain persona>
  Task: <crisp objective>
  Audience: <who/level>
  Language: <one language only>
  Output: <format + constraints>

Instructions:
  1) <step>
  2) <step>
  3) <step>

Examples (optional, tightly matched):
  <short in-domain example(s)>

Context (if any, trimmed to essentials):
  <RAG snippets or data>

Now solve the task.
```

### Example Using Template:

```
System/Intro:
  Role: Senior Python Developer
  Task: Debug performance issue
  Audience: Development team
  Language: English
  Output: Issue analysis + optimized code

Instructions:
  1) Identify performance bottlenecks
  2) Explain why they occur
  3) Provide optimized version
  4) Show performance comparison

Context:
def slow_function(data):
    result = []
    for i in range(len(data)):
        for j in range(len(data)):
            if data[i] > data[j]:
                result.append(data[i])
    return result

Now solve the task.
```

---

## Key Takeaways

### 1. MoE is About Efficient Specialization
- Multiple experts, only a few activate per input
- Like having specialists on-call instead of generalists always working

### 2. Your Prompt Influences Expert Selection
- Clear domain signals → Better expert routing
- Vague prompts → Generic expert activation
- Front-loaded context → Better routing decisions

### 3. Prompt Engineering Principles Still Apply
- Clarity matters even more
- Structure guides the model
- Examples should match domain
- Iterate and test

### 4. MoE Amplifies Prompt Quality
- Good prompts → Excellent results (right experts)
- Poor prompts → Mediocre results (wrong experts)
- The gap between good and bad prompts is wider with MoE

### 5. Not Everything Needs MoE Optimization
- Simple queries work fine with basic prompts
- Complex, multi-domain tasks benefit most
- Critical tasks warrant expert-aware prompting

---

## Comparison: Dense vs MoE Prompting

| Aspect | Dense Models | MoE Models |
|--------|-------------|------------|
| **Prompt Sensitivity** | Medium | High |
| **Domain Specificity** | Helpful | Critical |
| **Early Token Importance** | Important | Very Important |
| **Multi-Domain Tasks** | Okay in one prompt | Better split |
| **Consistency** | More consistent | Needs temperature control |
| **Language Specification** | Helpful | Essential |
| **Example Matching** | Good practice | Mandatory |

---

## Future of MoE and Prompting

### Trends to Watch

**1. More Experts, Finer Specialization**
- Current: 8-256 experts
- Future: 1000+ micro-experts for very specific tasks

**2. Learnable Routing**
- Future models might learn your prompting style
- Personalized expert selection

**3. Explicit Expert Selection**
- Users might be able to choose experts manually
- "Use Math Expert + Code Expert for this task"

**4. Hybrid Architectures**
- Combining dense layers (general knowledge) + MoE layers (specialized tasks)

**5. Domain-Specific MoE Models**
- Medical MoE, Legal MoE, Code MoE
- Pre-trained experts for specific industries

---

## Practical Exercise

**Task:** Create two versions of a prompt for each scenario, comparing generic vs MoE-optimized

### Scenario 1: Math Problem
```
Generic:
[Your prompt]

MoE-Optimized:
[Your improved prompt]
```

### Scenario 2: Multilingual Content
```
Generic:
[Your prompt]

MoE-Optimized:
[Your improved prompt]
```

### Scenario 3: Code Generation
```
Generic:
[Your prompt]

MoE-Optimized:
[Your improved prompt]
```

---

## Summary

### MoE in One Sentence
**MoE models have specialized experts that activate based on your input tokens, so clear, domain-specific prompts at the start of your message help route to the right experts, dramatically improving output quality.**

### Bottom Line for Prompt Engineering
MoE doesn't change the foundation of prompt engineering, but it **raises the leverage** of clear, early, domain-specific signals because they literally decide which specialists inside the model wake up for your tokens.

---

## Resources for Further Learning

### Research Papers
- "Mixture-of-Experts with Expert Choice Routing" (Google, 2022)
- "Switch Transformers: Scaling to Trillion Parameter Models" (Google, 2021)
- "DeepSeekMoE: Towards Ultimate Expert Specialization" (2024)

### Model Documentation
- Mixtral 8x7B (Mistral AI)
- Grok-1 Architecture (xAI)
- Google's Switch Transformers

### Tools
- Test prompts on different MoE models
- Compare routing behavior
- A/B test generic vs expert-aware prompts

---

## Questions to Consider

1. How does MoE change your current prompting approach?
2. Which of your tasks would benefit most from expert-aware prompting?
3. How can you restructure multi-domain prompts for better routing?
4. What domain signals are most relevant to your work?

---

## Next Steps

✅ Practice identifying domain signals in your prompts
✅ Experiment with front-loading context
✅ Test same prompt with different domain anchors
✅ Compare results across temperature settings
✅ Document routing-friendly templates for your use cases

---

**Thank you!**

*Governor House IT Initiative - Quarter 4*
*Prompt Engineering Course*

---

## Appendix: MoE Model Comparison Table

| Model | Organization | MoE Status | Total Params | Active Params | Key Features |
|-------|--------------|------------|--------------|---------------|--------------|
| **GPT-5** | OpenAI | Likely (unconfirmed) | ~2T | ~400B (20%) | Dynamic routing, reasoning levels |
| **Grok 4** | xAI | ✅ Confirmed | ~500B | Sparse | Multi-agent, ARC-AGI optimized |
| **Gemini 2.5 Pro** | Google | ✅ Confirmed | Undisclosed | Undisclosed | Advanced reasoning, scalable |
| **DeepSeek-V3** | DeepSeek | ✅ Confirmed | 671B | 37B (5.5%) | Cost-effective, MLA architecture |
| **Claude 4** | Anthropic | Unknown | ~400B (est.) | N/A | Likely dense (based on Claude 3.5) |
| **Mixtral 8x7B** | Mistral | ✅ Confirmed | 47B | ~14B (30%) | Open source, efficient |
| **Grok-1** | xAI | ✅ Confirmed | 314B | ~86B (27%) | Open weights available |

*Data as of 2025*
