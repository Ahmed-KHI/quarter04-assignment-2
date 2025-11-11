# Prompt Engineering Assignment 2
## Governor House IT Initiative - Quarter 4

---

## 📋 Assignment Overview

This repository contains the complete submission for **Assignment 2** of the Prompt Engineering course at Governor House IT Initiative. The assignment demonstrates comprehensive understanding of prompt engineering concepts, advanced techniques, and practical implementation through presentations, video notes, and a testing framework.

---

## 📁 Repository Structure

```
assignment-2/
│
├── presentation/
│   ├── 1_fundamental_prompting_techniques.md
│   ├── 2_advanced_prompting_strategies.md
│   └── 3_mixture_of_experts.md
│
├── video-notes/
│   ├── video-1-chatgpt-right-way.md
│   └── video-2-context-engineering.md
│
├── testing-framework/
│   └── prompt-testing-framework.md
│
└── README.md (this file)
```

---

## 📖 Assignment Requirements

As per the [assignment specifications](https://github.com/bilalmk/quarter04/blob/main/prompt_engineering/assignment-2.md), this submission includes:

### ✅ 1. Presentations on Three Topics

**Topics Covered:**
- Fundamental Prompting Techniques
- Advanced Prompting Strategies
- Mixture-of-Experts (MoE)

**Location:** `presentation/` folder

### ✅ 2. Video Notes

**Videos Watched:**
- "How To Use ChatGPT The RIGHT WAY In 2025"
- "Context Engineering Clearly Explained"

**Location:** `video-notes/` folder

### ✅ 3. Testing Framework

**Purpose:** Systematic evaluation of different prompt versions with documentation

**Location:** `testing-framework/` folder

---

## 📚 Detailed Content

### 1. Fundamental Prompting Techniques

**File:** `presentation/1_fundamental_prompting_techniques.md`

**Topics Covered:**
- **Zero-Shot Prompting** - Direct asking without examples
- **One-Shot Prompting** - Single example guidance
- **Few-Shot Prompting** - Multiple examples for pattern establishment
- **System Prompting** - Overall behavior and context setting
- **Role Prompting** - Assigning specific expertise or character
- **Contextual Prompting** - Providing background and constraints

**Key Features:**
- Detailed explanations with theory
- Real-world examples for each technique
- Pakistani context examples (Urdu, local businesses)
- Practical use cases
- Comparison tables
- Best practices
- Advantages and limitations

**Learning Outcomes:**
- Understand when to use each technique
- Know how to structure prompts effectively
- Recognize the differences between techniques
- Apply techniques to real projects

---

### 2. Advanced Prompting Strategies

**File:** `presentation/2_advanced_prompting_strategies.md`

**Topics Covered:**
- **Chain of Thought (CoT)** - Step-by-step reasoning for complex problems
- **Self-Consistency** - Multiple reasoning paths for accuracy
- **Step-Back Prompting** - General principles before specific application
- **ReAct (Reasoning + Acting)** - Combining reasoning with tool use
- **Tree of Thoughts (ToT)** - Exploring multiple solution branches

**Key Features:**
- In-depth explanations of each strategy
- Multiple examples per technique
- Pakistani business scenarios
- Technical and creative applications
- Comparison matrices
- When to use which strategy
- Combining strategies for complex tasks

**Learning Outcomes:**
- Master advanced reasoning techniques
- Handle complex multi-step problems
- Improve accuracy on critical tasks
- Build agentic AI workflows

---

### 3. Mixture-of-Experts (MoE)

**File:** `presentation/3_mixture_of_experts.md`

**Topics Covered:**
- What is MoE and why it matters
- MoE architecture and components
- How routing works
- MoE in modern LLMs (2025)
- Impact on prompt engineering
- Best practices for MoE models
- Troubleshooting MoE issues

**Key Features:**
- Restaurant analogy for understanding MoE
- Technical architecture explanation
- Comparison of MoE models (GPT-5, Grok, Gemini, DeepSeek-V3)
- Expert-aware prompting techniques
- Front-loading domain signals
- Handling multi-domain tasks
- Practical examples with MoE optimization

**Learning Outcomes:**
- Understand MoE architecture
- Write MoE-optimized prompts
- Leverage expert routing effectively
- Troubleshoot inconsistent outputs

---

### 4. Video Notes: ChatGPT Right Way 2025

**File:** `video-notes/video-1-chatgpt-right-way.md`

**Topics Covered:**
- Understanding ChatGPT capabilities in 2025
- Custom instructions and system prompts
- Effective conversation management
- Iterative prompting techniques
- Using roles and personas
- Asking ChatGPT to ask questions
- Markdown and formatting
- Code interpreter and data analysis
- Image generation and vision
- Custom GPTs
- Voice conversation mode
- Common mistakes to avoid
- Advanced techniques
- Productivity workflows
- Pakistani context considerations

**Key Takeaways:**
- Be specific and provide context
- Use iterative refinement
- Leverage custom instructions
- Structure outputs effectively
- Break complex tasks down

---

### 5. Video Notes: Context Engineering

**File:** `video-notes/video-2-context-engineering.md`

**Topics Covered:**
- What is context engineering
- Prompt engineering vs context engineering
- Why context engineering matters
- Retrieval-Augmented Generation (RAG)
- Chunking strategies
- Embedding and vector search
- Metadata filtering
- Reranking
- Context window management
- Practical implementation patterns
- Advanced techniques
- Measuring context quality
- Common pitfalls and solutions
- Tools and technologies

**Key Concepts:**
- Context = What information you show the model
- RAG pipeline: Retrieve → Augment → Generate
- Vector databases for semantic search
- Grounding LLM responses in factual data
- Reducing hallucinations through context

---

### 6. Prompt Testing Framework

**File:** `testing-framework/prompt-testing-framework.md`

**Purpose:**
Systematic testing and documentation of multiple prompt versions to identify the most effective approach for a specific task.

**Task Tested:**
Generating professional product descriptions for e-commerce (Wireless Bluetooth Headphones)

**Versions Tested:**
1. **v1.0** - Basic prompt (baseline)
2. **v1.1** - Added tone guidance
3. **v1.2** - Structured with specific requirements
4. **v2.0** - Few-shot learning with examples
5. **v2.1** - Role-based prompting
6. **v3.0** - Chain of Thought approach
7. **v3.1** - Temperature 0.3 (low, consistent)
8. **v3.2** - Temperature 0.9 (high, creative)

**Framework Includes:**
- Complete prompt text for each version
- Configuration settings (model, temperature, tokens)
- Generated outputs
- Quality assessment
- Issues and observations
- Scores and comparison
- Key findings and recommendations

**Testing Methodology:**
- Incremental improvements (one change at a time)
- Parameter tuning (temperature testing)
- Technique exploration (different prompting methods)
- Systematic documentation
- Comparative analysis

**Key Findings:**
1. Specificity matters most (80% improvement)
2. Few-shot examples create strong patterns
3. Role prompting shifts focus to benefits
4. Temperature significantly affects output
5. Chain of Thought ensures systematic quality

**Winner:** Version 2.1 (Role-based) - Score: 9.5/10

---

## 🎯 Learning Objectives Achieved

### Understanding
✅ Comprehend fundamental and advanced prompting techniques
✅ Understand Mixture-of-Experts architecture
✅ Differentiate between prompt and context engineering
✅ Recognize when to use specific techniques

### Application
✅ Apply appropriate prompting techniques to real tasks
✅ Optimize prompts for MoE models
✅ Implement testing frameworks
✅ Use iterative refinement effectively

### Analysis
✅ Evaluate prompt quality systematically
✅ Compare different prompting approaches
✅ Identify strengths and weaknesses
✅ Make data-driven decisions

### Synthesis
✅ Combine multiple techniques for complex tasks
✅ Create reusable prompt templates
✅ Design systematic testing processes
✅ Build production-ready prompts

---

## 💡 Key Takeaways

### From Fundamental Techniques
- **Zero-shot** is quick but may lack specificity
- **Few-shot** examples are powerful for pattern creation
- **System prompts** ensure consistent behavior
- **Roles** guide perspective and priorities
- **Context** makes responses highly relevant

### From Advanced Strategies
- **Chain of Thought** dramatically improves complex reasoning
- **Self-Consistency** reduces errors through multiple paths
- **Step-Back** grounds solutions in principles
- **ReAct** enables dynamic tool use
- **Tree of Thoughts** explores multiple solutions

### From MoE
- **Small wording changes** can change expert routing
- **Front-load domain signals** for better routing
- **Separate multi-domain tasks** to avoid confusion
- **Temperature control** is critical for consistency
- **Expert-aware prompting** improves output quality

### From Testing
- **Systematic testing** reveals optimal approaches
- **Incremental changes** isolate what works
- **Temperature** dramatically affects tone and creativity
- **Documentation** enables reuse and improvement
- **Iteration** beats perfection on first try

---

## 🛠️ Practical Applications

### For Students
- Writing research papers (structured thinking)
- Learning new concepts (step-back prompting)
- Solving complex problems (CoT, ToT)
- Creating content (role-based prompts)

### For Developers
- Code generation (specific requirements)
- Documentation (consistent formatting)
- Debugging (ReAct with tool use)
- Testing (systematic frameworks)

### For Businesses
- Product descriptions (few-shot patterns)
- Customer support (context engineering)
- Marketing content (role + tone optimization)
- Data analysis (code interpreter integration)

### For Freelancers
- Client deliverables (structured outputs)
- Proposal writing (persuasive techniques)
- Project planning (Tree of Thoughts)
- Time management (productivity workflows)

---

## 📊 Statistics

**Total Content Created:**
- **3** comprehensive presentations
- **2** detailed video note documents
- **1** systematic testing framework
- **8** prompt versions tested and documented
- **100+** practical examples
- **50+** code snippets and templates

**Word Count:**
- Fundamental Techniques: ~6,000 words
- Advanced Strategies: ~8,000 words
- Mixture-of-Experts: ~7,500 words
- Video Notes (Combined): ~9,000 words
- Testing Framework: ~5,500 words
- **Total: ~36,000 words**

**Learning Hours:**
- Research and study: ~10 hours
- Content creation: ~15 hours
- Testing and documentation: ~5 hours
- **Total: ~30 hours**

---

## 🎓 Skills Demonstrated

### Technical Skills
✅ Prompt engineering (fundamental to advanced)
✅ Model configuration (temperature, tokens, top-p)
✅ Context engineering and RAG
✅ Systematic testing and evaluation
✅ Documentation and knowledge management

### Analytical Skills
✅ Comparative analysis
✅ Pattern recognition
✅ Problem decomposition
✅ Critical evaluation
✅ Data-driven decision making

### Communication Skills
✅ Technical writing
✅ Clear explanations
✅ Example creation
✅ Structured documentation
✅ Knowledge synthesis

---

## 🔗 References and Resources

### Course Materials
- [Panaversity Learn Low-Code Agentic AI](https://github.com/panaversity/learn-low-code-agentic-ai)
- [Prompt Engineering Tutorial](https://github.com/panaversity/learn-low-code-agentic-ai/tree/main/00_prompt_engineering)
- [Assignment Specifications](https://github.com/bilalmk/quarter04/blob/main/prompt_engineering/assignment-2.md)

### Videos Watched
- [How To Use ChatGPT The RIGHT WAY In 2025](https://www.youtube.com/watch?v=pv_sAnH_P8Q)
- [Context Engineering Clearly Explained](https://www.youtube.com/watch?v=jLuwLJBQkIs)

### Additional Resources
- OpenAI API Documentation
- Anthropic Claude Documentation
- LangChain Documentation
- Vector Database Guides (Pinecone, Weaviate)

---

## 🚀 How to Use This Repository

### For Learning
1. **Start with Fundamentals** - Read `1_fundamental_prompting_techniques.md`
2. **Progress to Advanced** - Move to `2_advanced_prompting_strategies.md`
3. **Understand MoE** - Study `3_mixture_of_experts.md`
4. **Watch Videos** - Follow along with video notes
5. **Practice Testing** - Apply the testing framework to your tasks

### For Reference
- Use as a quick reference guide
- Copy prompt templates
- Apply best practices
- Learn from examples
- Avoid documented pitfalls

### For Projects
- Adapt prompts to your domain
- Use the testing framework structure
- Implement systematic evaluation
- Document your findings
- Build a prompt library

---

## ✅ Assignment Completion Checklist

- [x] Create presentation on Fundamental Prompting Techniques
- [x] Create presentation on Advanced Prompting Strategies
- [x] Create presentation on Mixture-of-Experts
- [x] Watch and document "How To Use ChatGPT The RIGHT WAY In 2025"
- [x] Watch and document "Context Engineering Clearly Explained"
- [x] Develop comprehensive testing framework
- [x] Test multiple prompt versions systematically
- [x] Document all findings and observations
- [x] Create detailed README
- [x] Organize repository structure
- [x] Include practical examples throughout
- [x] Add Pakistani context where relevant
- [x] Provide actionable recommendations

---

## 📝 Submission Details

**Student Name:** [Mirza Muhammad Ahmed]
**Roll Number:** [00263838]
**Course:** Governor House IT Initiative - Quarter 4
**Subject:** Prompt Engineering
**Assignment:** Assignment 2
**Submission Date:** [11-11-2025]
**Instructor:** [Bilal Muhammad Khan]

---

## 🙏 Acknowledgments

- **Governor House IT Initiative** for providing this learning opportunity
- **Panaversity** for excellent course materials and resources
- **OpenAI, Anthropic, Google** for developing advanced AI models
- **Content Creators** who made educational videos on prompt engineering
- **The AI Community** for sharing knowledge and best practices

---

## 📞 Contact

For questions or discussions about this assignment:

[![GitHub](https://img.shields.io/badge/GitHub-Ahmed--KHI-181717?style=flat&logo=github&logoColor=white)](https://github.com/Ahmed-KHI)
[![Email](https://img.shields.io/badge/Email-m.muhammad.ahmed115%40gmail.com-D14836?style=flat&logo=gmail&logoColor=white)](mailto:m.muhammad.ahmed115@gmail.com)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Mirza%20Muhammad%20Ahmed-0077B5?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mirza-muhammad-ahmed-09b932209)

---

## 📄 License and Usage

This repository is created for educational purposes as part of the Governor House IT Initiative coursework.

**Usage Guidelines:**
- ✅ Use for learning and reference
- ✅ Adapt prompts for your projects
- ✅ Share knowledge with fellow students
- ❌ Do not copy verbatim for assignments
- ❌ Do not claim as your own work

---

## 🎯 Future Work

**Potential Extensions:**
1. Test more LLM models (Claude, Gemini, Llama)
2. Build automated testing pipeline
3. Create domain-specific prompt libraries
4. Develop multilingual testing (Urdu prompts)
5. Implement RAG system with testing framework
6. Compare cost-effectiveness of different approaches
7. Create interactive prompt playground
8. Build production-ready prompt templates

---

## 📈 Personal Reflection

**What I Learned:**
- Prompt engineering is both an art and science
- Systematic testing reveals non-obvious patterns
- Context engineering is critical for production apps
- Small changes in prompts can have large effects
- MoE models require special considerations
- Temperature settings dramatically affect outputs

**What Surprised Me:**
- How much specificity improves results
- The power of few-shot learning
- MoE routing's sensitivity to wording
- Context engineering's complexity
- The importance of systematic testing

**What I'll Apply:**
1. Always start with structured prompts
2. Use testing frameworks for important tasks
3. Front-load domain signals for MoE models
4. Implement iterative refinement
5. Document successful patterns

**Challenges Faced:**
- Understanding MoE routing mechanisms
- Balancing creativity vs. consistency
- Testing enough variations thoroughly
- Organizing large amounts of content
- Creating practical, relevant examples

**Skills Gained:**
- Advanced prompt engineering
- Systematic testing methodology
- Technical documentation
- Knowledge synthesis
- Critical analysis

---

## 💬 Final Thoughts

This assignment has been an incredible deep dive into the world of prompt engineering. The field is rapidly evolving, with new techniques and models emerging constantly. The key takeaway is that **systematic experimentation and documentation** are essential for mastering prompt engineering.

Whether you're using AI for personal projects, professional work, or research, the principles covered here—specificity, structure, iteration, and testing—will serve you well.

**Remember:**
> "The best prompt is the one that consistently gives you the results you need."

Keep learning, keep testing, and keep improving! 🚀

---

**End of README**

---

## 📚 Quick Navigation

- [Assignment Overview](#-assignment-overview)
- [Repository Structure](#-repository-structure)
- [Detailed Content](#-detailed-content)
- [Learning Objectives](#-learning-objectives-achieved)
- [Key Takeaways](#-key-takeaways)
- [How to Use](#-how-to-use-this-repository)
- [Completion Checklist](#-assignment-completion-checklist)
- [Contact](#-contact)

---

*Created with dedication and passion for learning AI and prompt engineering.*

*Governor House IT Initiative - Empowering Pakistan's Future Developers*

🇵🇰 **Made in Pakistan** 🇵🇰
