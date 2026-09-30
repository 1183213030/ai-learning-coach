<div align="center">

# AI Learning Coach (Personal Tech Mentor)

### A Personal Learning Operating System that Helps Anyone Truly Master Coding and Technology

Say goodbye to "reading a tutorial and thinking you got it, then staring blankly at an empty screen." Like having an expert private tutor by your side, guiding you from absolute zero to independent real-world mastery.

[![Protocol Version](https://img.shields.io/badge/Protocol-v3.0.0-007ACC?style=flat-square)](#)
[![Zero Command](https://img.shields.io/badge/Interaction-Zero--Command%20Natural%20Language-4EBA6F?style=flat-square)](#)
[![Complete Pedagogy](https://img.shields.io/badge/Pedagogy-Controlled%20Variation%20%7C%20Counterexamples-orange?style=flat-square)](#)
[![License](https://img.shields.io/badge/License-MIT-lightgrey?style=flat-square)](#)

[简体中文](README.md) • [English](README_en.md)

</div>

---

## Why Do You Need This Tool?

When learning to code, almost everyone encounters three painful frustrations:

1. **"The Illusion of Competence"**: You watch a video tutorial or read a blog post, nodding along thinking "this is so easy!" But when you close the tab and try to write code from scratch, your mind goes completely blank.
2. **"Standard AI is Like a Cheating Butler"**: When you get stuck, you ask ChatGPT. It dumps hundreds of lines of code and technical jargon. You copy-paste it to solve the immediate problem, but your brain never actually learned how it works.
3. **"Fragmented Learning Feels Like Scavenging Puzzle Pieces"**: You read one blog today and watch a random video tomorrow. After months of studying, you still can't connect the pieces into a cohesive architecture.

**AI Learning Coach** was designed to solve this once and for all. It doesn't spoon-feed answers. It acts as your **dedicated private mentor**: guiding you with intuitive real-world analogies, controlled contrast experiments, and closed-book assessments to ensure the skills become permanently yours.

---

## How Does It Actually Teach a Beginner?

### 1. Maps the Entire Journey First
Whether you say "I want to build websites" or "I want to master frontend development," it doesn't rush to dump random code. It quietly draws a clear **Skill Tree Roadmap**:
- What fundamentals must be built first (the solid bedrock);
- What comes second and third;
- Where the destination lies and how every concept connects.
It never pushes you to advanced chapters until your foundational mechanics are truly solid.

### 2. Controlled Variation: Change One Variable and Watch the Result Shift
Great teachers don't just state definitions; they run experiments with you.
Instead of memorizing array methods, it holds everything constant and **changes only one variable at a time**:
- `[1, 2, 3].includes(2)` -> `true` (Found, normal)
- `[1, 2, 3].includes(4)` -> `false` (Value changed)
- `['1', '2', '3'].includes(1)` -> `false` (Type changed: string vs number)
- `[[1]].includes([1])` -> `false` (Reference changed: memory pointer trap!)
By observing output shifts step-by-step, you build an unshakeable physical intuition for how the runtime operates.

### 3. Counterexample Shocks: Shattering False Assumptions
Beginners often suffer from assuming they understand when they don't.
The coach presents **"near-miss counterexamples that look correct but fail instantly"**:
- For example, checking if a string contains `"admin"`;
- It shows `"hello, admin"` (passes) vs `"hello, admmmmmin"` (FAILS!);
- Then asks: *"Every letter of 'admin' is inside 'admmmmmin'. Why did the computer reject it?"*
When you deduce for yourself that "the letters must be connected consecutively with no breaks," the concept is locked into your mind forever.

### 4. Closed-Book Verification: Saying "I Understand" Doesn't Count
Traditional courses ask "Does that make sense?" and accept a polite "yes" as proof of mastery.
This coach enforces a strict rule: **Teaching and Testing are completely separate**.
During verification, hints and solutions are hidden. You must explain the mechanism in plain words or write the code completely independently. True capability is logged only when you succeed with zero AI hints.

### 5. Respects Real Life: Your Fatigue and Time Come First
Real humans aren't machines. You can't always study for 2 hours:
- If you worked late and only have 10 minutes, say: *"Exhausted today, only have 10 mins"*. It stops new chapters immediately and gives you a 3-minute micro-review on a recent blind spot.
- If you hit a real production bug, say: *"Pause the course, my app is throwing a CORS error"*. It pauses the curriculum immediately to help you debug and extracts the lesson from your real code.

---

## How to Use It (Just Speak Naturally)

You never need to memorize slash commands. Speak naturally as if chatting on Discord or Slack:

### Scenario A: Starting a Brand New Subject
> **You**: *"I want to systematically learn frontend development, but I'm a complete beginner."*
> 
> **Coach**: Skips intimidating jargon. Asks 1-2 intuitive diagnostic questions to gauge your level, then starts step-by-step from foundational concepts.

### Scenario B: Resuming Where You Left Off
> **You**: *"Continue yesterday's study."*
> 
> **Coach**: Skips pleasantries and picks up exactly where you left off yesterday.

### Scenario C: Really Confused, Demanding an Analogy
> **You**: *"That closure explanation was way too abstract. Give me a real-life analogy."*
> 
> **Coach**: Drops the technical jargon and uses an intuitive physical model (like a hotel keycard and private safe box) to make the memory model crystal clear.

### Scenario D: Limited Time
> **You**: *"Overtime today, only have 15 minutes. Keep it quick."*
> 
> **Coach**: Blocks new lessons and delivers a 3-minute quiz on yesterday's mistake. Once done, it lets you rest immediately.

### Scenario E: Testing Yourself Honestly
> **You**: *"Quiz me on what we just learned, zero hints."*
> 
> **Coach**: Enters closed-book mode, hides previous code examples, and presents a clean problem for you to solve independently.

### Scenario F: Real Work Bug Interrupt
> **You**: *"Pause the lesson. My live page threw a cross-origin error, help me figure out why."*
> 
> **Coach**: Freezes curriculum progress, diagnoses the browser's Same-Origin Policy with you, and resumes the course only when your production bug is fixed.

---

## Step-by-Step Installation & Setup

### Method 1: In Google Antigravity (Recommended / Zero Config)
Natively configured for this workspace:
1. Open this workspace in Antigravity;
2. Type whatever you want to learn in the chat (e.g. *"I want to learn frontend development"*);
3. The coach activates automatically.

### Method 2: In Claude Code (Universal across all systems)
If you use Anthropic's Claude Code CLI:

**Global Installation (Available across all your projects):**
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent claude-code
```

**Project-Level Installation (Only active inside current directory):**
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --agent claude-code
```

### Method 3: In OpenAI Codex / Other Terminal Agents
```bash
npx skills add https://github.com/1183213030/ai-learning-coach.git --skill ai-learning-coach --global --agent codex
```

### Advanced: Ingest Your Own Books / Notes as Courseware (Local Library)
If you have great Markdown tutorials, PDF textbooks, or documentation:
1. Copy your files into `library/` (e.g. inside `library/frontend/`);
2. Tell the AI:
   > *"Teach me using my local frontend notes in the library folder."*
3. The coach prioritizes your local material as the curriculum backbone, ensuring structured and non-conflicting learning.

---

## License

This project is open-source under the [MIT License](LICENSE).
