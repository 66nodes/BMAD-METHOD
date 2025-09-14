# A Beginner's Guide to the BMAD-METHOD™

Welcome! This guide is for anyone new to the BMAD-METHOD™. We'll explain how it works and walk you through using it, all from a user's perspective. Our goal is to get you up and running quickly.

For more advanced details, you can always consult the full [User Guide](user-guide.md).

## How BMAD Works: A Simple Explanation

At its heart, the BMAD-METHOD™ is about **thinking before doing**. It solves the biggest problem with most AI code generation today: AI agents often start writing code without fully understanding the requirements, leading to messy, incorrect, or incomplete results.

BMAD fixes this by splitting the process into two distinct phases:

**Phase 1: The Planning Session (Thinking)**

*   Instead of one AI trying to do everything, you assemble a team of specialized AI "agents" (like a Project Manager, an Architect, and an Analyst).
*   You work *with* this team to define your project. They will ask you questions and, based on your answers, create professional documents like a **Product Requirements Document (PRD)** and an **Architecture Plan**.
*   This phase is all about strategy and design. By the end, you have a crystal-clear plan that everyone (including the AI agents) agrees on.

**Phase 2: The Development Cycle (Doing)**

*   Once the plan is set, you switch to your code editor.
*   A "Scrum Master" agent takes the big plan and breaks it down into small, manageable coding tasks called "stories".
*   Crucially, each story contains all the context from the planning phase.
*   A "Developer" agent then picks up a story and, because it has all the necessary information, can write high-quality, accurate code to implement the feature.

This **"plan first, code later"** approach, combined with specialized agents who have full context, is what makes BMAD so effective. It turns AI from a simple code-completion tool into a structured, reliable development partner.

## Quick Start: Your First Planning Session (Web UI)

The fastest way to start with BMAD is by using a powerful web-based AI, like Claude or the Gemini web UI. This is perfect for the "Planning Phase" where you define what your project is all about.

**Goal:** To create a Project Brief, a PRD, and an Architecture document for a simple project idea.

**Step 1: Get Your AI Team**

1.  Find the "team file" that defines your AI agents. The best one to start with is the full-stack team.
2.  You can find it here in the repository: [`dist/teams/team-fullstack.txt`](../dist/teams/team-fullstack.txt).
3.  Open this file and copy its entire content.

**Step 2: Set Up Your Web AI**

1.  Go to your favorite web AI platform (e.g., Gemini, Claude, or a Custom GPT in ChatGPT).
2.  Create a new chat or a new "Gem".
3.  In the instruction or configuration panel, paste the content you copied from `team-fullstack.txt`. Add this line above or below the pasted text:
    > "Your critical operating instructions are attached, do not break character as directed."

**Step 3: Start Planning!**

Now you can start chatting with your AI team. The lead agent is the **BMAD-Orchestrator**.

*   **To see all commands**, type:
    ```
    *help
    ```
*   **To start planning**, a good first step is to talk to the Analyst to create a project brief. Try this:
    ```
    *analyst
    ```
    The analyst will then guide you through a process to create a `brief`.

*   **To create the PRD**, once you have a brief, you can ask the Project Manager:
    ```
    *pm create a prd from the brief
    ```

*   **To create the Architecture**, you can then ask the Architect:
    ```
    *architect create the architecture from the prd
    ```

By the end of this process, you will have high-quality planning documents. The next section will explain how to take these documents and start building the actual software in your code editor.

## Full Workflow: From Idea to Code (IDE)

Once you have your planning documents (PRD and Architecture) from the web UI session, it's time to move to your local code editor and start building.

**Goal:** To set up your project locally and implement your first feature using the BMAD agents in your IDE.

**Step 1: Prerequisites**

*   Make sure you have [Node.js](https://nodejs.org) (version 20 or higher) installed on your computer. You can check by opening a terminal and running `node -v`.
*   You'll also need `git` installed.

**Step 2: The One-Command Install**

1.  Open a terminal or command prompt.
2.  Navigate to the root directory of your project (or an empty folder where you want to start your new project).
3.  Run the following command:
    ```bash
    npx bmad-method install
    ```
    This command will ask you a few questions to set up BMAD correctly for your project and your preferred tools. It's smart enough to handle new installs and also updates if you run it again later.

**Step 3: Bring in Your Plans**

1.  From your web UI session, copy the content of the PRD and Architecture documents.
2.  In your project, create the following files and paste the content into them:
    *   `docs/prd.md`
    *   `docs/architecture.md`
    (If the `docs` folder doesn't exist, create it.)

**Step 4: The Development Loop**

Now you're ready to code. The basic loop looks like this:

1.  **Break Down the Plan:** First, you need to "shard" your big planning documents into smaller pieces. The Product Owner (`*po`) agent does this. (The installer can also do this for you).

2.  **Create a Story:** Ask the Scrum Master (`*sm`) to prepare the next coding task. The SM will look at the epics and architecture and create a detailed "story" file for the developer.
    *   Example command (in a compatible IDE): `@sm draft next story`

3.  **Implement the Story:** Now, the Developer (`*dev`) agent takes over. It will read the story file, which contains all the context it needs.
    *   Example command: `@dev implement the story`

4.  **Review and Test:** After the `*dev` agent is done, you should review the code. The QA agent (`*qa`) can also be used to run tests and check for issues.
    *   Example command: `@qa *review the story`

5.  **Repeat:** Once the story is complete and the code is committed, you can ask the `@sm` to draft the next story, and the loop continues!

This workflow ensures that every piece of code you write is directly tied to the master plan you created, leading to a more organized and robust final product.

## Meet Your AI Team

You don't just have one AI assistant; you have a whole team of them! Here are the key players and their roles:

| Agent Role | Name / Alias | What They Do |
| :--- | :--- | :--- |
| **Orchestrator** | `*bmad-orchestrator` | The team leader in the web UI. It directs your requests to the right agent. |
| **Analyst** | `*analyst` | Your research expert. Helps with brainstorming, market research, and creating a Project Brief. |
| **Project Manager** | `*pm` | The planner. Takes the Project Brief and turns it into a detailed Product Requirements Document (PRD). |
| **Architect** | `*architect` | The designer. Creates the technical architecture and system design based on the PRD. |
| **Product Owner** | `*po` | The gatekeeper. Ensures the plans are solid and breaks them down for the development team. |
| **Scrum Master** | `*sm` | The task master. Takes the high-level plans and writes detailed, context-rich stories for the developer to work on. |
| **Developer** | `*dev` | The builder. Takes a story and writes the code, including tests. |
| **QA Agent** | `*qa` / "Quinn" | The quality expert. A "Test Architect" who can assess risk, design test plans, and review code for quality. |
| **Master Agent** | `*bmad-master` | A versatile agent that can perform most of the other agents' tasks. Useful if you don't want to switch roles often. |

Using the right agent for the right task is key to getting the best results from the BMAD-METHOD™.

## What's Next?

Congratulations! You now understand the basics of the BMAD-METHOD™. You know how to start a project in a web UI and how to transition to your IDE to build it.

When you're ready to go deeper, here are some resources to explore:

*   **The Full [User Guide](user-guide.md):** For a detailed breakdown of every feature, command, and agent.
*   **The [Core Architecture](core-architecture.md):** For a technical deep-dive into how BMAD works under the hood.
*   **[Expansion Packs](expansion-packs.md):** Learn how to use BMAD for more than just software, like game development or creative writing, or even create your own agents.
*   **Join the Community:** The best way to learn is to connect with others. Join the **[Discord Community](https://discord.gg/gk8jAdXWmj)** to ask questions, share your projects, and get help from other users.

Happy building!
