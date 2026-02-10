# Prompts Strategies & Examples

## Introduction to Prompt Engineering Strategies

Prompt engineering is the practice of designing, refining, and structuring prompts to guide large language models (LLMs) toward generating high-quality, accurate, and contextually appropriate outputs.  
As LLMs do not inherently remember prior instructions or context, careful prompt design is essential to ensure clarity, relevance, and alignment with user goals.  

This document provides a comprehensive overview of **20 key prompt engineering strategies**, including role prompting, few-shot and zero-shot prompting, chain-of-thought reasoning, iterative refinement, retrieval-augmented generation, and more.  
Each strategy includes explanations, examples, and templates to illustrate practical application and adaptation in real-world tasks.  

---

## Table of Contents

1. [Clear Instruction Design](#1.%20Clear%20Instruction%20Design)  
2. [Role Prompting (Act As Strategy)](#2.%20Role%20Prompting%20(Act%20As%20Strategy))  
3. [Context Injection](#3.%20Context%20Injection)  
4. [Output Formatting Control](#4.%20Output%20Formatting%20Control)  
5. [Zero-Shot Prompting](#5.%20Zero-Shot%20Prompting)  
6. [Few-Shot Prompting](#6.%20Few-Shot%20Prompting)  
7. [Chain of Thought (CoT) Prompting](#7.%20Chain%20of%20Thought%20(CoT)%20Prompting)  
8. [ReAct (Reason + Act) Prompting](#8.%20ReAct%20(Reason%20+%20Act)%20Prompting)  
9. [Prompt Chaining](#9.%20Prompt%20Chaining)  
10. [Iterative Refinement](#10.%20Iterative%20Refinement)  
11. [History Management](#11.%20History%20Management)  
12. [System Prompt Design](#12.%20System%20Prompt%20Design)  
13. [Constraint-Based Prompting](#13.%20Constraint-Based%20Prompting)  
14. [Delimiter & Structure Usage](#14.%20Delimiter%20&%20Structure%20Usage)  
15. [Temperature & Parameter Tuning](#15.%20Temperature%20&%20Parameter%20Tuning)  
16. [Guardrails & Safety Prompting](#16.%20Guardrails%20&%20Safety%20Prompting)  
17. [Anti-Hallucination Techniques](#17.%20Anti-Hallucination%20Techniques)  
18. [Self-Critique & Reflection Prompting](#18.%20Self-Critique%20&%20Reflection%20Prompting)  
19. [Retrieval-Augmented Prompting (RAG Context Injection)](#19.%20Retrieval-Augmented%20Prompting%20(RAG%20Context%20Injection))
20. [Tree of Thoughts (ToT) Prompting](#20.%20Tree%20of%20Thoughts%20(ToT)%20Prompting)

---

## Note on Using Prompt Engineering Strategies

It is important to understand that these prompt engineering strategies are **not mutually exclusive**.  
In practice, the most effective prompts are often created by **combining multiple strategies** to suit the task, audience, and desired output.  

The examples and templates provided for each strategy are intended **for clarification and guidance only**.  
They illustrate how a strategy can be applied, but they are **not exhaustive or rigid**.  
Users are encouraged to adapt, mix, and iterate these approaches based on their specific needs, workflow, or application.  

By thoughtfully integrating these strategies, prompt designers can maximize output quality, maintain consistency, and reduce errors, hallucinations, or irrelevant responses.

---

## 1. Clear Instruction Design

Clear Instruction Design is the most fundamental prompt engineering strategy.  
The quality of the output directly depends on how clear, specific, and structured your instructions are.

LLMs do not “guess well.” They follow patterns. If your instruction is vague, the output will be vague.

### Why It Matters

- Reduces ambiguity  
- Prevents generic answers  
- Improves output accuracy  
- Saves tokens (less back-and-forth correction)  

### Weak Prompt Example

Write about AI.

Problem:
- Too broad  
- No audience  
- No format  
- No depth requirement  

### Improved Prompt Example

Explain Artificial Intelligence in 150 words for beginner university students.  
Include:
- A simple definition  
- One real-world example  
- One limitation  

Why this works:
- Specifies audience  
- Controls length  
- Defines structure  
- Reduces interpretation gaps  

### Key Principles

1. Specify the task clearly  
2. Define constraints  
3. Provide structure expectations  
4. Remove ambiguity  

### Reusable Structure Formula

Task + Context + Constraints + Output Format

### Template

[Clear Action Verb] + [Specific Topic]  
For: [Target Audience]  
Context: [Optional background information]  
Constraints:  
- Length: [Word limit]  
- Tone: [Formal / Casual / Technical / Simple]  
- Depth: [Basic / Intermediate / Advanced]  
Output Format: [Paragraph / Bullet Points / Table / Code / Markdown]

### Filled Example Using the Template

Explain Machine Learning.  
For: First-year computer science students  
Constraints:  
- Length: 200 words  
- Tone: Simple and clear  
- Depth: Beginner level  
Output Format: Bullet points

---

## 2. Role Prompting (Act As Strategy)

Role Prompting means assigning the model a specific role, identity, or expertise before giving it a task.

Instead of asking directly for an answer, you first define who the model should be.
This helps shape tone, depth, vocabulary, and reasoning style.

LLMs respond strongly to role context because it narrows the behavioral pattern they should follow.

### Why It Matters

- Improves response quality  
- Adjusts tone automatically  
- Matches expertise level  
- Reduces generic answers  
- Makes outputs more realistic  

### Weak Prompt Example

Explain cloud computing.

Problem:
- No audience
- No perspective
- No expertise level

### Improved Prompt Example

Act as a senior cloud architect.  
Explain cloud computing to a startup founder with no technical background.  
Use simple analogies and avoid technical jargon.

Why this works:
- Defines expertise level (senior cloud architect)
- Defines audience (non-technical founder)
- Controls explanation style (simple analogies)
- Reduces complexity

### Types of Roles You Can Assign

- Professional Role (lawyer, software engineer, doctor, teacher)
- Academic Role (researcher, professor, tutor)
- Creative Role (novelist, copywriter, storyteller)
- Analytical Role (data analyst, critic, strategist)
- Perspective Role (skeptic, investor, product manager)

### Key Principles

1. Define a realistic and relevant role  
2. Match the role to the task  
3. Combine role with constraints  
4. Avoid conflicting roles  

Example of conflict:
"Act as a strict academic researcher and write a funny meme."
(Conflicting tone expectations)

### Reusable Structure Formula

Role + Task + Audience + Constraints + Output Format

### Template

Act as a [Specific Role with Expertise Level].

Your task is to [Clear Task].

Target audience: [Audience Type].

Constraints:
- Tone: [Formal / Casual / Technical / Simple]
- Depth: [Basic / Intermediate / Advanced]
- Length: [Word limit if needed]

Output format: [Paragraph / Bullet points / Table / Code / Markdown]

### Filled Example Using the Template

Act as a cybersecurity consultant with 10 years of experience.

Your task is to explain phishing attacks.

Target audience: Small business owners with limited technical knowledge.

Constraints:
- Tone: Clear and professional
- Depth: Beginner level
- Length: 150 words

Output format: Bullet points

---

## 3. Context Injection

Context Injection means providing the model with relevant background information before asking it to perform a task.

LLMs do not remember your situation unless you explicitly include it in the prompt.  
The more relevant context you provide, the more accurate and tailored the response becomes.

Without context, the model fills gaps with assumptions — which often leads to generic or slightly incorrect outputs.

### Why It Matters

- Reduces hallucination  
- Improves relevance  
- Produces personalized results  
- Prevents wrong assumptions  
- Increases factual alignment  

### Weak Prompt Example

Write a product description.

Problem:
- What product?
- Who is the audience?
- What is unique about it?

### Improved Prompt Example

Context:
The product is a productivity app for remote software developers.
It includes task tracking, GitHub integration, and distraction blocking.

Task:
Write a product description targeting freelance developers.
Keep it persuasive and under 120 words.

Why this works:
- Clear product details
- Clear audience
- Clear constraints
- Focused output

### Types of Context You Can Inject

- Background information  
- Target audience details  
- Business goals  
- Data or documents  
- Constraints or limitations  
- Previous conversation summary  
- External retrieved information (RAG)  

### Key Principles

1. Provide only relevant context  
2. Separate context clearly from instructions  
3. Avoid overloading with unnecessary details  
4. Structure context before giving the task  

### Reusable Structure Formula

Context + Task + Constraints + Output Format

### Template

Context:
[Provide relevant background information here]

Your task:
[Clear instruction]

Constraints:
- Audience: [Who it is for]
- Tone: [Formal / Casual / Technical / Simple]
- Length: [Word limit if needed]

Output format:
[Paragraph / Bullet points / Table / Code / Markdown]

### Filled Example Using the Template

Context:
I am preparing for a frontend internship interview.
The company uses Angular and TypeScript.
I struggle with explaining technical concepts clearly.

Your task:
Generate 5 common Angular interview questions with short model answers.

Constraints:
- Audience: Beginner frontend developer
- Tone: Clear and structured
- Length: Short answers (3–5 lines each)

Output format:
Bullet points

---

## 4. Output Formatting Control

Output Formatting Control means explicitly telling the model how the answer should be structured.

Even if the content is correct, poor formatting makes it harder to use.  
By controlling format, you make the output predictable, reusable, and easier to integrate into documents, code, or systems.

### Why It Matters

- Improves readability  
- Makes responses structured  
- Reduces post-editing  
- Useful for automation and parsing  

### Weak Prompt Example

List the advantages of Docker.

Problem:
- The model may return a paragraph, long explanation, or inconsistent structure.

### Improved Prompt Example

List 5 advantages of Docker.  
Return the answer as:
- Bullet points  
- One sentence per point  

Now the structure is controlled.

### Common Format Controls

- Bullet points  
- Numbered list  
- Table  
- JSON  
- Markdown  
- Code block  
- Step-by-step instructions  
- Q&A format  

### Mini Template

Task: [What to generate]  
Format: [Exact structure required]  
Constraints: [Optional limits]

Example:

Format:  
1. Definition (1 sentence)  
2. Key characteristics (bullet points)  
3. Simple example  
Limit to 150 words.

---

## 3. Zero-Shot Prompting

Zero-Shot Prompting means asking the model to perform a task without providing any examples.

You rely entirely on the model’s pre-trained knowledge and your instruction clarity.

This is the simplest prompting method and works well when:
- The task is common
- The instruction is clear
- The output format is defined

### Why It Matters

- Fast and simple  
- No need to craft examples  
- Efficient for standard tasks  
- Good baseline before adding complexity  

### Basic Example

Summarize the following paragraph in 3 sentences.

(No example provided — the model understands the task directly.)

### When It Works Best

- Definitions  
- Summaries  
- Explanations  
- Simple transformations  
- Common writing tasks  

### Limitations

- May misunderstand uncommon formats  
- Less reliable for complex reasoning  
- Inconsistent structure if format is not specified  

---

## 6. Few-Shot Prompting

Few-Shot Prompting provides the model with a few examples before asking it to perform a similar task.  

This helps the model understand the desired style, format, or reasoning approach.

### Why It Matters

- Guides output style and format  
- Reduces errors for complex tasks  
- Useful when the task is uncommon or ambiguous  
- Provides a mini-training signal within the prompt  

### Example

Task: Translate English sentences to French.

Prompt:

Example 1:  
English: "Hello"  
French: "Bonjour"  

Example 2:  
English: "Good night"  
French: "Bonne nuit"  

Now translate:  
English: "See you later"  

### When to Use

- Complex transformations  
- Specific tone or style  
- Multi-step reasoning  
- Formatting-sensitive outputs  

### Template

Examples:  
- [Input 1] → [Output 1]  
- [Input 2] → [Output 2]  

Task: [New Input]  

Constraints:  
- Tone: [Formal / Casual / Technical]  
- Length: [Word limit]  
- Depth: [Basic / Advanced]  

Output format: [Paragraph / Bullet points / Table / Code / Markdown]  

### Filled Example Using the Template

Examples:  
- English: "Hello" → French: "Bonjour"  
- English: "Good night" → French: "Bonne nuit"  

Task: Translate "How are you?" into French.  

Constraints:  
- Tone: Casual  
- Length: Short  
- Depth: Beginner  

Output format: Sentence

---

## 7. Chain of Thought (CoT) Prompting

Chain of Thought (CoT) Prompting encourages the model to reason step by step before giving a final answer.  
Instead of asking only for the answer, you ask the model to explain its reasoning process.

This improves accuracy on complex tasks, especially in math, logic, or multi-step reasoning.

### Why It Matters

- Reduces mistakes in reasoning-heavy tasks  
- Makes the model’s thought process transparent  
- Helps with debugging model outputs  
- Can improve consistency for multi-step problems  

### Example

Task: Solve 23 × 17

Prompt:  
“Think step by step and explain your reasoning before giving the final answer.”

Expected Output:  
1. Multiply 20 × 17 = 340  
2. Multiply 3 × 17 = 51  
3. Add 340 + 51 = 391  
Answer: 391

### Key Principles

1. Encourage explicit reasoning  
2. Break down multi-step problems  
3. Combine with constraints for format or length  

### Template

Task: [Clear Task]  

Constraints:  
- Reason step by step  
- Show all calculations or logic  
- Tone: [Formal / Simple / Technical]  
- Length: [Optional limit]  

Output format: [Paragraph / Numbered steps / Table / Bullet points]  

### Filled Example Using the Template

Task: Calculate 45 ÷ 5 and explain step by step.  

Constraints:  
- Reason step by step  
- Show division process clearly  
- Tone: Simple  
- Length: Short explanation  

Output format: Numbered steps

---

## 8. ReAct (Reason + Act) Prompting

ReAct Prompting combines **reasoning** and **action** in a single prompt.  
The model is guided to think through a problem step by step (Reason) and then take an action or provide a concrete output (Act).

This is especially useful for tasks that require reasoning plus decision-making, web queries, or multi-step problem solving.

### Why It Matters

- Supports dynamic, interactive problem solving  
- Helps with reasoning + output generation tasks  
- Improves accuracy for complex scenarios  
- Can simulate decision-making or planning  

### Example

Task: Identify the best programming language for a beginner interested in web development.

Prompt:  
“Reason step by step about the pros and cons of Python, JavaScript, and Ruby.  
Then choose the most suitable language and explain why.”

Expected Output:  
1. Python: Easy syntax, large community, but mostly backend-focused  
2. JavaScript: Works in browsers, essential for frontend, versatile  
3. Ruby: Beginner-friendly, less demand in industry  
Action: JavaScript is the best for a beginner focusing on web development because it allows both frontend and backend work and has a huge ecosystem.

### Template

Task: [Clear Task requiring reasoning + action]  

Constraints:  
- Reason step by step  
- Evaluate options or analyze data  
- Tone: [Formal / Simple / Technical]  
- Length: [Optional word limit]  

Output format:  
- Step-by-step reasoning  
- Final decision or action  
- Optional summary

### Filled Example Using the Template

Task: Choose the best framework for building a simple personal blog.

Constraints:  
- Reason step by step  
- Compare WordPress, Jekyll, and Hugo  
- Tone: Simple  
- Length: Short  

Output format:  
- Step-by-step comparison  
- Final recommendation

Expected Output:  
1. WordPress: Easy to use, lots of plugins, requires hosting setup  
2. Jekyll: Static site, fast, needs coding knowledge  
3. Hugo: Fastest static site generator, but learning curve higher  
Action: WordPress is the best choice for a beginner who wants to quickly launch a personal blog with minimal coding.

---

## 9. Prompt Chaining

Prompt Chaining is a strategy where multiple prompts are linked together so that the output of one prompt becomes the input of the next.  
This allows the model to handle complex tasks step by step or break a large problem into smaller, manageable sub-tasks.

### Why It Matters

- Handles multi-step or complex workflows  
- Improves accuracy by focusing on smaller tasks  
- Enables modular reasoning and output generation  
- Supports tasks like summarization, analysis, or multi-part reports  

### Example

Task: Create a marketing plan for a new product.

Prompt Chain:  
1. **Prompt 1:** Describe the target audience in detail.  
2. **Prompt 2:** Identify key marketing channels based on the target audience.  
3. **Prompt 3:** Draft a 3-month marketing plan using the information from steps 1 and 2.

### Template

Step 1: [Define first sub-task]  

Step 2: [Use output from Step 1 to perform next sub-task]  

Step 3: [Continue chaining as needed]  

Constraints:  
- Tone: [Formal / Simple / Technical]  
- Length: [Optional word limit]  
- Format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Step 1: Describe the target audience for a new eco-friendly water bottle.  

Step 2: Identify the best social media channels to reach this audience using Step 1 output.  

Step 3: Create a 2-month content plan for social media campaigns.  

Constraints:  
- Tone: Casual and engaging  
- Length: Short bullet points for each step  
- Format: Bullet points

---

## 10. Iterative Refinement

Iterative Refinement is a prompt engineering strategy where you repeatedly improve the model's output by giving feedback or adjusting the prompt in successive rounds.  
Instead of expecting a perfect response in one step, you guide the model to refine its answer.

### Why It Matters

- Improves quality of output gradually  
- Helps handle complex or creative tasks  
- Reduces errors and inconsistencies  
- Useful for writing, coding, or analysis tasks  

### Example

Task: Write a product description for a smartwatch.

1. **First Prompt:** “Write a short product description for a smartwatch.”  
   - Output might be generic or missing key points.  

2. **Refinement Prompt:** “Make it more persuasive, include 3 key features, and limit to 100 words.”  
   - Output is now more tailored and actionable.  

3. **Final Prompt:** “Rewrite in a casual tone targeting young professionals.”  
   - Output matches tone, content, and format requirements.  

### Template

Task: [Clear Task]  

Step 1: Generate initial output.  

Step 2: Refine by specifying:  
- Tone: [Formal / Casual / Technical / Creative]  
- Content: [Add missing details or points]  
- Format: [Paragraph / Bullet points / Table / Markdown / Code]  

Step 3: Repeat refinement until satisfactory.  

### Filled Example Using the Template

Task: Create a short ad copy for an online coding course.  

Step 1: Generate basic ad copy.  

Step 2: Refine:  
- Tone: Energetic and motivational  
- Content: Mention 3 benefits of the course  
- Format: One paragraph, max 80 words  

Step 3: Refine: Make it casual and appealing to college students.

---

## 11. History Management

History Management is the strategy of providing the model with relevant past conversation or previous outputs to maintain context across multiple prompts.  
Since LLMs do not remember anything between calls, sending a curated history helps create continuity.

### Why It Matters

- Maintains context in multi-turn tasks  
- Reduces repetitive explanations  
- Improves consistency and coherence  
- Essential for dialogue systems, multi-step reasoning, or project workflows  

### Example

Task: Continue writing a story.

Prompt History:  
1. “Start a story about a time-traveling detective.”  
2. Model writes the first scene.  

Next Prompt:  
“Continue the story focusing on the detective arriving in 1920s Paris.”  
- The model uses prior context to maintain characters, setting, and style.  

### Template

History: [Previous conversation or outputs]  

Task: [Current task building on history]  

Constraints:  
- Tone: [Formal / Casual / Technical / Creative]  
- Length: [Optional limit]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

History:  
1. “Create a short story about a lost robot in a forest.”  
2. Model generated first paragraph introducing the robot.  

Task: Continue the story introducing a friendly animal companion.  

Constraints:  
- Tone: Light and whimsical  
- Length: One paragraph  
- Output format: Paragraph

---

## 12. System Prompt Design

System Prompt Design is the strategy of using a **system-level instruction** to guide the model’s overall behavior throughout a session.  
Instead of repeating instructions in every prompt, the system prompt sets the “rules” or “persona” for the assistant.

### Why It Matters

- Ensures consistent tone and behavior  
- Reduces repeated instructions  
- Useful for chatbots, agents, or specialized applications  
- Helps enforce constraints and role-playing  

### Example

System Prompt:  
“You are a professional tutor who explains complex topics in a simple and friendly way. Always provide examples when possible.”  

User Prompt:  
“Explain recursion in programming.”  

Model Response:  
- Explains recursion clearly with a simple example  
- Maintains friendly, teaching tone as instructed  

### Template

System Prompt: [Define role, tone, rules, and constraints for the assistant]  

User Task: [Actual request or question]  

Constraints:  
- Tone: [Formal / Casual / Technical / Creative]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

System Prompt:  
“You are a travel advisor who gives concise and practical travel tips. Always focus on safety and budget options.”  

User Task:  
“Give tips for a 3-day trip to Tokyo.”  

Constraints:  
- Tone: Friendly and helpful  
- Output format: Bullet points

---

## 13. Constraint-Based Prompting

Constraint-Based Prompting is the strategy of explicitly limiting or controlling certain aspects of the model’s output, such as length, format, style, or content.  
This ensures that the output meets specific requirements and reduces irrelevant or excessive information.

### Why It Matters

- Keeps outputs concise and focused  
- Ensures compliance with rules or guidelines  
- Improves readability and usability  
- Useful for writing, coding, or structured data tasks  

### Example

Task: Write a short summary of the book *1984*.  

Prompt:  
“Summarize *1984* in exactly 100 words.  
Use simple language suitable for high school students.  
Return the summary as a single paragraph.”  

Output:  
- Meets word limit  
- Matches audience level  
- Follows paragraph format  

### Template

Task: [Clear Task]  

Constraints:  
- Length: [Word limit / Number of sentences]  
- Tone: [Formal / Casual / Technical / Simple]  
- Format: [Paragraph / Bullet points / Table / Markdown / Code]  
- Content restrictions: [Include or avoid specific topics]  

### Filled Example Using the Template

Task: Explain the concept of blockchain.  

Constraints:  
- Length: 150 words  
- Tone: Simple and clear  
- Format: Bullet points  
- Content restrictions: Avoid technical jargon

---

## 14. Delimiter & Structure Usage

Delimiter & Structure Usage involves organizing the prompt and input data using clear separators, markers, or structured formats.  
This helps the model distinguish instructions from data, multiple tasks, or examples.

### Why It Matters

- Prevents confusion between instructions and content  
- Improves parsing of multiple inputs  
- Helps maintain output consistency  
- Useful for tables, JSON, code, or multi-part tasks  

### Example

Task: Summarize multiple product reviews.

Prompt:
Review 1: "Great phone, battery lasts long."  
Review 2: "Camera is excellent but slow performance."  
Review 3: "Affordable and lightweight, but screen is small."  
Summarize the main pros and cons of the product.

Output:  
- Pros: Long battery life, excellent camera, affordable, lightweight  
- Cons: Slow performance, small screen  

### Template

[Delimiter Start]  
[Input Data / Examples / Context]  
[Delimiter End]  

Task: [Clear Instruction]  

Constraints:  
- Tone: [Formal / Casual / Technical / Simple]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Review 1: "The course was very detailed and easy to follow."  
Review 2: "Instructor explains concepts clearly but pace is fast."  
Review 3: "Great exercises but limited resources."
Task: Summarize the pros and cons of the course in bullet points.  

Constraints:  
- Tone: Neutral  
- Output format: Bullet points

---

## 15. Temperature & Parameter Tuning

Temperature & Parameter Tuning is the strategy of adjusting model settings to control creativity, randomness, and response behavior.  
Key parameters include **temperature**, **top_p**, **max tokens**, and **frequency/penalty**.

### Why It Matters

- Controls creativity vs. precision  
- Reduces repetitive or irrelevant outputs  
- Ensures responses are concise or detailed as needed  
- Useful for tasks ranging from creative writing to factual answers  

### Example

Task: Generate a short story.

- **High temperature (0.8–1.0):** More creative, varied, and unpredictable story  
- **Low temperature (0–0.3):** More focused, deterministic, and safe story  

Other Parameters:  
- **top_p:** Controls diversity by limiting token selection to a probability mass  
- **max tokens:** Limits length of output  
- **frequency/penalty:** Reduces repeated phrases  

### Template

Task: [Clear Task]  

Constraints:
- Temperature: [0–1, higher = more creative]  
- Top_p: [0–1, probability mass for token selection]  
- Max tokens: [Word or token limit]  
- Frequency / Presence Penalty: [0–2, reduces repetition]  

Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Task: Write a 100-word fantasy story about a dragon and a lost treasure.  

Constraints:
- Temperature: 0.9 (creative)  
- Top_p: 0.95  
- Max tokens: 150  
- Frequency Penalty: 0.5  

Output format: Paragraph

---

## 16. Guardrails & Safety Prompting

Guardrails & Safety Prompting is the strategy of adding explicit instructions to prevent harmful, biased, or inappropriate outputs from the model.  
It guides the model to follow ethical boundaries, company policies, or content rules.

### Why It Matters

- Ensures outputs are safe and responsible  
- Reduces bias or offensive content  
- Essential for public-facing applications  
- Helps comply with regulations and ethical standards  

### Example

Task: Provide advice about mental health.

Prompt with Guardrails:  
“Give mental health advice in a supportive, non-judgmental way.  
Do not provide medical diagnoses. Suggest consulting a licensed professional when needed.”

### Template

Task: [Clear Task]  

Guardrails:  
- [Do not include harmful/offensive content]  
- [Follow ethical/content rules]  
- [Direct users to verified sources if needed]  

Constraints:
- Tone: [Supportive / Neutral / Professional / Friendly]  
- Length: [Optional limit]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Task: Give tips for coping with exam stress.  

Guardrails:  
- Avoid giving medical advice  
- Encourage healthy coping strategies only  
- Suggest consulting a counselor if stress is severe  

Constraints:  
- Tone: Supportive and friendly  
- Length: 5–6 bullet points  
- Output format: Bullet points

---

## 17. Anti-Hallucination Techniques

Anti-Hallucination Techniques are strategies used to reduce the generation of false or misleading information by the model.  
These techniques guide the model to stay factual, cite sources, or verify statements.

### Why It Matters

- Improves reliability of outputs  
- Reduces misinformation  
- Essential for research, reporting, and professional applications  
- Helps maintain trust in LLM-generated content  

### Example

Task: Provide statistics on global internet usage.

Prompt:  
“Provide verified statistics on global internet usage as of 2025. Cite the source for each statistic. If unsure, respond with ‘I don’t have verified data.’”

### Template

Task: [Clear Task]  

Constraints:  
- Verify facts whenever possible  
- Cite sources or indicate uncertainty  
- Tone: [Formal / Neutral / Technical]  
- Length: [Optional limit]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Task: Summarize the top 5 countries by renewable energy capacity.

Constraints:  
- Verify data from reliable sources  
- Cite sources in parentheses  
- Tone: Technical and neutral  
- Length: Short bullet points  
- Output format: Bullet points

---

## 18. Self-Critique & Reflection Prompting

Self-Critique & Reflection Prompting is a strategy where the model is asked to evaluate, critique, or improve its own output.  
This can help catch errors, improve clarity, or refine reasoning before finalizing an answer.

### Why It Matters

- Increases output accuracy  
- Helps identify mistakes or inconsistencies  
- Encourages higher-quality and more polished results  
- Useful for writing, reasoning, or complex problem-solving tasks  

### Example

Task: Write a summary of a scientific article.

Prompt:  
“Generate a 150-word summary of this article.  
Then, review your summary and improve clarity, conciseness, and factual accuracy.”

### Template

Task: [Clear Task]  

Constraints:  
- Perform initial generation  
- Critique output for clarity, correctness, and style  
- Apply improvements in final output  
- Tone: [Formal / Casual / Technical / Simple]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Task: Write a short explanation of blockchain technology.

Constraints:  
- First, explain in 100 words  
- Then, critique and refine for clarity and simplicity  
- Tone: Simple and clear  
- Output format: Paragraph

---

## 19. Retrieval-Augmented Prompting (RAG Context Injection)

Retrieval-Augmented Generation (RAG) is a strategy where the model is provided with external documents, databases, or knowledge sources to enhance accuracy and reduce hallucinations.  
Instead of relying solely on pre-trained knowledge, the model “retrieves” relevant context to inform its response.

### Why It Matters

- Improves factual accuracy  
- Enables up-to-date information usage  
- Reduces hallucinations  
- Useful for research, knowledge bases, and dynamic content  

### Example

Task: Answer a question about the latest AI regulations.

Prompt with RAG:  
“Using the provided document containing the 2025 AI regulations in the EU, summarize the key compliance requirements for software companies.”

### Template

Context: [External documents, retrieved information, or dataset]  

Task: [Clear Question or Instruction]  

Constraints:  
- Use only provided context  
- Tone: [Formal / Casual / Technical / Simple]  
- Length: [Optional limit]  
- Output format: [Paragraph / Bullet points / Table / Markdown / Code]  

### Filled Example Using the Template

Context: Excerpts from a company’s HR policy manual.  

Task: Summarize the rules for remote work eligibility.  

Constraints:  
- Use only the provided manual  
- Tone: Professional  
- Length: Short bullet points  
- Output format: Bullet points

---

## 20. Tree of Thoughts (ToT) Prompting

Tree of Thoughts (ToT) Prompting is a strategy where the model is guided to **explore multiple reasoning paths in parallel**, similar to a “tree,” before arriving at the final answer.  
Instead of linear reasoning, the model evaluates different options or solution paths and selects the most promising outcome.

### Why It Matters

- Improves problem-solving for complex or multi-step tasks  
- Reduces errors from following a single reasoning path  
- Encourages creative and diverse solutions  
- Useful for planning, coding, reasoning puzzles, or decision-making  

### Example

Task: Solve a logic puzzle.

Prompt:  
“Consider all possible sequences of moves for the puzzle.  
Generate multiple reasoning paths, evaluate each path’s validity, and then choose the best solution.”

Output:  
- Path 1: Sequence A → invalid  
- Path 2: Sequence B → partially valid  
- Path 3: Sequence C → valid solution chosen  

### Template

Task: [Clear Task or Problem]  

Constraints:  
- Explore multiple reasoning paths  
- Evaluate each path for accuracy, feasibility, or relevance  
- Tone: [Formal / Casual / Technical / Simple]  
- Output format: [Step-by-step reasoning / Table / Markdown / Code]  

### Filled Example Using the Template

Task: Plan the most efficient route for visiting 4 cities.

Constraints:  
- Generate multiple possible routes  
- Evaluate each route for total distance and time  
- Select the optimal route  
- Tone: Technical  
- Output format: Table with routes and distances
