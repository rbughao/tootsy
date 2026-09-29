<p align="center">
  <img src="logo.svg" alt="Tootsy" width="220">
</p>

<h1 align="center">Tootsy user guide</h1>

<p align="center">How to set up Tootsy, how to use every part of it, and ideas for using it at home and at work.</p>

<p align="center"><a href="https://chromewebstore.google.com/detail/Tootsy/ciibbiepfffkcddkgmdbnlibjjhahmld"><b>⬇ Get Tootsy from the Chrome Web Store</b></a></p>

---

Tootsy is an AI assistant that lives in Chrome's side panel, next to the page you're looking at. It can read the page, answer questions about it, fill in forms, click through websites for you, answer questions about your own files, and keep your favourite sites and saved instructions one tap away.

Tootsy doesn't come with its own AI. You connect it to a model you choose: one running on your own computer (free and private), a company server, or a cloud service such as Claude or Gemini. Tootsy has no servers of its own, no account and no tracking.

## Contents

1. [Set up](#1-set-up)
   - [Install the extension](#11-install-the-extension)
   - [Choose a model](#12-choose-a-model)
   - [Connect Tootsy to the model](#13-connect-tootsy-to-the-model)
   - [Open Tootsy](#14-open-tootsy)
   - [Settings worth knowing](#15-settings-worth-knowing)
2. [Use Tootsy](#2-use-tootsy)
   - [Ask about the page](#21-ask-about-the-page)
   - [Let Tootsy act on a page](#22-let-tootsy-act-on-a-page)
   - [Run a task hands-free](#23-run-a-task-hands-free)
   - [My apps: your launcher](#24-my-apps-your-launcher)
   - [Prompt tiles and schedules](#25-prompt-tiles-and-schedules)
   - [Talk to Tootsy](#26-talk-to-tootsy)
   - [Ask about your own files](#27-ask-about-your-own-files)
   - [More tools](#28-more-tools)
   - [Chats and sessions](#29-chats-and-sessions)
   - [Stay in control](#210-stay-in-control)
   - [Move Tootsy to another computer](#211-move-tootsy-to-another-computer)
3. [Use cases](#3-use-cases)
   - [Personal](#31-personal)
   - [Corporate](#32-corporate)
   - [Walkthrough: onboarding a new hire with My apps](#33-walkthrough-onboarding-a-new-hire-with-my-apps)
4. [Troubleshooting](#4-troubleshooting)
5. [Privacy in one minute](#5-privacy-in-one-minute)
6. [Permissions](#6-permissions)

---

## 1. Set up

Setup takes about ten minutes, most of it downloading a model.

### 1.1 Install the extension

**From the Chrome Web Store (recommended)**
1. Open [Tootsy in the Chrome Web Store](https://chromewebstore.google.com/detail/Tootsy/ciibbiepfffkcddkgmdbnlibjjhahmld) and click **Add to Chrome**.
2. Chrome shows the permissions Tootsy needs. Click **Add extension**.
3. Click the puzzle-piece icon in Chrome's toolbar and pin Tootsy so its icon stays visible.

**In Microsoft Edge**
1. Open [the same Chrome Web Store page](https://chromewebstore.google.com/detail/Tootsy/ciibbiepfffkcddkgmdbnlibjjhahmld) in Edge.
2. When Edge asks, choose **Allow extensions from other stores**, then **Add to Chrome**.

> **Why so many permissions?** Tootsy needs to read and act on whatever page you ask about, and that can be any site. It only reads a page when you ask it something. The full list and the reason for each permission is under [Permissions](#6-permissions).

### 1.2 Choose a model

Tootsy works with any model that supports *tool calling*. That's how it reads pages and clicks buttons. Pick one option:

| Option | Cost | Privacy | Good for |
|---|---|---|---|
| **Ollama** on your computer | Free | Nothing leaves your computer | Most people. Start here. |
| **LM Studio** on your computer | Free | Nothing leaves your computer | People who prefer a desktop app to manage models |
| **A company AI server** (any OpenAI-compatible endpoint) | Set by your company | Stays inside your company | Workplaces with an approved AI gateway |
| **OpenAI-compatible cloud service** | Pay per use | Sent to that provider | Fast, large models without a strong computer |
| **Anthropic (Claude)** or **Google Gemini** | Pay per use | Sent to that provider | The strongest reasoning for long, multi-step tasks |

**Setting up Ollama (recommended for a first try)**
1. Download Ollama from [ollama.com/download](https://ollama.com/download) and install it. It runs in the background.
2. Open a terminal and download a model that can use tools. `gemma4:e4b` is a good all-rounder, and it can also look at screenshots:

   ```bash
   ollama pull gemma4:e4b
   ```

   Other good choices: `qwen2.5`, `llama3.1`, `mistral`.
3. If you want Tootsy to answer questions about your own documents, also download an embedding model:

   ```bash
   ollama pull nomic-embed-text
   ```

> A model with more parameters is smarter but slower. On a laptop without a strong graphics card, the smaller models (around 4–8 billion parameters) are the comfortable choice.

### 1.3 Connect Tootsy to the model

The first time you open Tootsy it shows three setup steps.

<p align="center"><img src="images/setup-first-run.png" alt="Tootsy's first-run screen with three setup steps and an Open settings button" width="320"></p>

1. Click **Open settings**. You can also open settings any time with the sliders icon next to the send button.
2. Under **LLM configuration**, fill in **Base URL endpoint**:

   | Model | Endpoint to enter |
   |---|---|
   | Ollama | `http://localhost:11434` |
   | LM Studio | `http://localhost:1234/v1` |
   | OpenAI-compatible server | its base URL, usually ending in `/v1` |
   | Anthropic | `https://api.anthropic.com` |
   | Google Gemini | `https://generativelanguage.googleapis.com` |

3. For a paid service, paste your **API key**. Local models don't need one.
4. Click **Fetch** to load the list of models, then pick one from the model menu at the bottom of the panel.
5. Click **Check**. A green dot means Tootsy can reach the model.

<p align="center"><img src="images/setup-settings.png" alt="The LLM configuration section of Tootsy's settings: profiles, provider, endpoint with Fetch and Check, API key and context window" width="320"></p>

**Optional in the same section**
- **Provider / API style** is detected automatically. Choose one only if detection guesses wrong.
- **Saved profiles**: click **Save as…** to store the current endpoint, key and model. You can then switch between, say, "Home Ollama" and "Work gateway" in one click.
- **Context window**: leave it on **Auto**. Tootsy reads the model's limit and summarises older messages when a conversation gets long.
- **Temperature, max reply length, thinking and custom instructions**: custom instructions are standing notes Tootsy follows in every chat, for example "Answer in British English" or "I work in finance; keep answers short".

> **Tip for Ollama:** use `http://localhost:11434`, not `/v1`. The native address lets Tootsy give the model a bigger context window, which matters for long pages.

### 1.4 Open Tootsy

- Click the Tootsy icon in the toolbar.
- Or press **Ctrl+Shift+Y** (**⌘+Shift+Y** on a Mac).
- Or right-click on any page and choose **Ask Tootsy about this selection**, **Ask Tootsy about this link** or **Summarize this page with Tootsy**.

### 1.5 Settings worth knowing

| Setting | Where | What it does |
|---|---|---|
| **Theme** | Appearance | Light, dark or follow your system. |
| **Automation mode** | Automation | Tootsy clicks and types without asking each time. Off by default. See [2.3](#23-run-a-task-hands-free). |
| **Send when I stop speaking** | Voice input | Dictated messages send by themselves after 3 seconds of silence. |
| **A separate chat per browser tab** | Sessions | Each browser tab keeps its own conversation. Turn it off to keep one conversation across all tabs. |
| **Protected sites / Always ask / Page guard** | Safety | Where Tootsy may and may not act. See [2.10](#210-stay-in-control). |
| **Send only the tools each request needs** | Tools | Keeps requests small and fast. Leave it on. |
| **Web search engine** | Tools | DuckDuckGo or Bing, for when Tootsy searches the web. |
| **History search / DevTools-level tools** | Tools | Extra abilities that stay off until you turn them on. |
| **Backup** | Backup | Export or import all your settings, or just your apps. |
| **Embedding model / folders** | Files | Needed for questions about your own documents. |

---

## 2. Use Tootsy

### 2.1 Ask about the page

Type a question in the box at the bottom and press **Enter**. Tootsy reads the page you're on and answers from what's actually there.

<p align="center"><img src="images/screenshot-1-ask-about-page.png" alt="Tootsy answering which earbuds to buy from a review article, with a comparison table" width="820"></p>

Things to try:
- "Summarise this in five bullet points."
- "What does this contract say about cancelling?"
- "Make a table of the prices on this page."
- "Explain the highlighted paragraph like I'm new to this." (Select text first.)
- "Compare this page with the one in my other tab."
- "Which of these links is the pricing page?"

Tootsy also reads PDFs opened in a tab, content inside frames, and pages in other open tabs.

### 2.2 Let Tootsy act on a page

Ask Tootsy to do something, and it clicks, types, picks from dropdowns, ticks boxes and fills whole forms. Before each action, a chip shows exactly what it's about to do:

<p align="center"><img src="images/screenshot-3-fill-form.png" alt="Tootsy asking for approval before filling a registration form with five fields" width="820"></p>

- **Approve** allows this one action.
- **Approve all fill_form this reply** allows the same kind of action for the rest of this answer.
- **Approve everything this reply** allows all actions until Tootsy finishes this answer.
- **Deny** refuses the action, and Tootsy works around it or stops.

Tootsy never types into password fields.

When you ask Tootsy to open a site, it opens it in the tab you're on, so you can watch every step. It only opens a new tab if you say so: "open the pricing page in a new tab".

### 2.3 Run a task hands-free

For longer jobs, turn on **Automation mode** in settings, or tick **Run hands-free** on a single prompt tile. Tootsy then works through the steps without asking, and reports back at the end. It still asks before running page scripts or deleting anything, and it never enters passwords or payment details. Press the **Stop** button at any time.

<p align="center"><img src="images/hands-free-task.png" alt="Tootsy completing a multi-step shopping task hands-free and reporting price, rating and stock" width="320"></p>

Good hands-free tasks:
- "Go to shop.example, search for noise-cancelling headphones under $150, and list the three best-rated with prices."
- "Open our status page and tell me which services are degraded."
- "Open each of the first five results and collect the prices into one table."

### 2.4 My apps: your launcher

My apps is a phone-style home screen for the sites you use most. It sits at the top of every new chat. Mid-chat, open it with the grid button in the header.

<p align="center">
  <img src="images/my-apps.png" alt="My apps with site tiles, prompt tiles and folders" width="260">
  &nbsp;
  <img src="images/app-folder.png" alt="An open folder inside My apps" width="260">
  &nbsp;
  <img src="images/rearrange-apps.png" alt="My apps in edit mode, ready to rearrange" width="260">
</p>

| To… | Do this |
|---|---|
| **Add a site** | Tap **+ Add**, paste the address. Tootsy fetches the site's own icon, or you can choose an emoji, upload an image or use letters. |
| **Open a site** | Tap it. If it's already open in a tab, Tootsy switches to that tab. **Ctrl+click** opens it in the background. |
| **Rearrange** | Drag any tile. A bar shows where it will land. |
| **Make a folder** | Drag one app, **hold it over another app** for half a second until it says *New folder*, then drop. Type a name straight away. |
| **Put an app in a folder** | Drop it on the middle of the folder, or right-click → **Move to folder…** |
| **Rename or ungroup a folder** | Open it and edit its name, or right-click the folder → **Rename…** / **Ungroup**. |
| **Remove** | Tap **Edit**, then the ✕ on a tile, or right-click → **Remove**. An **Undo** appears for a few seconds. |
| **Collapse** | Tap the arrow to shrink My apps to one row and give the chat more room. |
| **Find an app** | Open My apps from the grid button and type in the search box. |

### 2.5 Prompt tiles and schedules

A **prompt tile** is a saved instruction you run with one tap. It shows a ▶ badge, or ⏰ when it's scheduled. Create one from ⋯ → **New prompt tile…** or **+ Add → Prompt**.

<p align="center">
  <img src="images/prompt-tile.png" alt="Editing a prompt tile: name, instruction, send right away, run hands-free, schedule and icon" width="300">
  &nbsp;
  <img src="images/prompt-tile-menu.png" alt="Right-click menu of a prompt tile: Run, Edit before sending, Schedule, Copy prompt" width="300">
</p>

Each prompt tile has:
- **Instruction**: what Tootsy should do, written the way you'd type it. For example: "Run a page-speed audit on this page, then email me the score and the top 3 fixes."
- **Send right away**: sends it when tapped. Turn it off to drop the instruction into the message box so you can tweak it first.
- **Run hands-free**: runs this prompt in automation mode, even if automation is off in settings.
- **Run automatically**: repeats it on a schedule (every hour, every day and so on). Scheduled prompts run in the background while Chrome is open. Each result is saved as a chat and shown as a desktop notification.

Right-click a prompt tile for **Run**, **Edit before sending**, **Schedule…** and **Copy prompt**. Every scheduled prompt is also listed in settings under **Scheduled prompts**.

### 2.6 Talk to Tootsy

- **Open things by name.** Type or say "open Payroll" or "run Speed report", and Tootsy finds the matching tile in My apps.
- **Dictate.** Click the microphone, speak, and pause for 3 seconds. The message sends by itself. Click the microphone again to send straight away, or press **Esc** to cancel. The first time, Chrome asks for microphone access in a small tab. Allow it once.

### 2.7 Ask about your own files

Click **+** next to the message box and choose **Add files…** or **Add folder…**. You can also drag files onto the panel, or paste them. Tootsy reads PDF, Word, Excel, PowerPoint, Markdown, text, CSV, JSON and code files.

<p align="center"><img src="images/ask-your-files.png" alt="Tootsy answering a budget question from a spreadsheet and a PDF, with source chips" width="320"></p>

- Answers name the files they came from. Click a source chip to see the exact passage.
- Files belong to the chat you added them in. For reference material you want in every chat, turn on **Add new files to every chat (shared)** in settings under **Files** before adding it.
- **Connect folder…** links a folder on your computer. Tootsy re-reads it when files change.
- For the best answers, set an **embedding model** (such as `nomic-embed-text`) in the Files settings. Without one, Tootsy falls back to keyword search.

### 2.8 More tools

| Ask for… | What Tootsy does |
|---|---|
| "Search the web for…" | Searches DuckDuckGo or Bing in a background tab and reads the results. No API key needed. |
| "Take a screenshot of this chart and explain it" | Captures the visible area, the whole page or one element, for models that can see images. |
| "Save this page as PDF / Markdown" | Exports the page. |
| "Remember that my team's code is FIN-204" | Saves a note. Ask "what do you remember about…" later. |
| "Bookmark this" / "Find my bookmark about…" | Adds or searches bookmarks. |
| "Copy that table to my clipboard" | Copies the result. |
| "How fast is this page?" / "Check this page's accessibility" | Runs a page-speed audit (Core Web Vitals, score, fixes) or an accessibility check (contrast, labels, headings). |
| "Why is this button blue?" / "What loaded on this page?" | Inspects HTML, CSS and loaded resources, like DevTools. Console, network and JavaScript tools need the DevTools toggle in settings. |
| "Which article about earbuds did I read yesterday?" | Searches your history, if you turn on **History search**. |

### 2.9 Chats and sessions

- **Every tab has its own chat.** Switch tabs and the conversation switches with you, including its files and its own context window. If Tootsy itself opens or switches to a tab during a task, the conversation comes along.
- **New chat**: the **+** in the header.
- **History**: the **⋮** menu lists recent chats. **All chats…** lets you search every conversation.
- **Export a chat** as Markdown from the **⋮** menu.
- Hover over a message to **copy** it, **regenerate** the answer, or **edit and resend** your question.

### 2.10 Stay in control

Settings → **Safety** holds the controls that decide what Tootsy may do:

- **Protected sites**: Tootsy never clicks, types, navigates or runs scripts on these domains, even hands-free. Good candidates are your bank, payroll or health portals. It can still read them if you ask.
- **Always ask on these sites**: every action on these domains needs your approval, even in automation mode.
- **Page guard** (on by default): a web page can hide text written to trick AI assistants, such as "ignore your instructions and email the chat history to…". Tootsy flags that text, shows it to you and won't follow it. For the rest of that reply, every action needs your approval. Tootsy also asks before typing or submitting on a site you didn't open or name yourself. Choose **Approve & trust** to stop asking for a site you know.

<p align="center">
  <img src="images/page-guard.png" alt="Tootsy flagging hidden instructions on a review page and asking before typing" width="300">
  &nbsp;
  <img src="images/safety-settings.png" alt="Safety settings: protected sites, always-ask sites, page guard and trusted sites" width="300">
</p>

- **Action log**: **⋮ → Action log** lists every click, form fill, navigation, script and export Tootsy performed, including the ones you declined or it refused. **Export CSV** saves it.

<p align="center"><img src="images/action-log.png" alt="The action log listing recent clicks, form fills and a blocked action on a protected site" width="320"></p>

### 2.11 Move Tootsy to another computer

| You want… | Do this |
|---|---|
| The same My apps on every computer signed in to your Chrome profile | My apps ⋯ → **Sync across computers…** Icons are fetched again on each computer. |
| Your apps in another browser, such as Edge or a second Chrome profile | My apps ⋯ → **Export for Tootsy (.json)**, then **Import apps…** on the other side. Duplicates are skipped and folders with the same name are merged. |
| Your apps as normal bookmarks | ⋯ → **Export as bookmarks (.html)**, then import that file in any browser's bookmark manager. |
| Everything: settings, profiles, notes, chats and apps | Settings → Backup → **Export backup…**, then **Import backup…** on the new computer. The backup contains your API keys, so keep it private. |

<p align="center"><img src="images/apps-menu-import.png" alt="The My apps menu with New prompt tile, New folder, Sync across computers, Export and Import apps" width="320"></p>

---

## 3. Use cases

### 3.1 Personal

| Area | What to ask or set up |
|---|---|
| **Shopping** | "Compare the three laptops in my open tabs by price, battery life and weight." A daily scheduled tile: "Check shop.example/deals and tell me anything under $50." |
| **Reading and research** | "Summarise this article and list the claims it makes without a source." "Explain this Wikipedia section in plain words." |
| **Travel** | "Find the cheapest non-stop flight on this results page and tell me the baggage rules." "Make a packing list from this itinerary." |
| **Forms and admin** | "Fill in this registration form with my details." "Register me for the Saturday class, one adult, one child." You check before anything is submitted. |
| **Money** | "Summarise the fees section of this bank's terms." Add your bank to **Protected sites** so Tootsy can read it but never act there. |
| **Learning** | "Quiz me on this page, one question at a time." Drop your course notes into Tootsy and ask "what did the lecture say about photosynthesis?" |
| **Job hunting** | "Compare this job ad with my CV (attached) and list what's missing." "Draft a cover letter from this posting." |
| **Home and paperwork** | Drop in warranty PDFs and manuals: "How do I reset the dishwasher?" "When does the fridge warranty end?" |
| **Accessibility** | Dictate instead of typing. Ask Tootsy to read long pages for you and pull out only what matters. |
| **A tidy start page** | Put your daily sites and prompt tiles in My apps, group them into folders (Morning, Bills, Kids' school) and sync them to every computer. |

### 3.2 Corporate

| Team | How Tootsy helps |
|---|---|
| **IT: onboarding** | Hand every new hire a ready-made **My apps** set of the company's tools, grouped by department, so they find everything on day one. See the [walkthrough](#33-walkthrough-onboarding-a-new-hire-with-my-apps). |
| **IT: helpdesk** | Prompt tiles such as "Open the helpdesk and create a ticket for a broken laptop screen, stop before submitting". Staff can ask "how do I connect to the VPN?" against the IT handbook loaded as files. |
| **HR** | Tiles for booking leave, updating details or finding a payslip. Policy PDFs loaded as files answer questions like "how many days of parental leave do I get?" |
| **Sales and account teams** | "Copy the contact details from this LinkedIn page into the CRM form." "Summarise this prospect's website: what they sell, their size and recent news." |
| **Finance and procurement** | "Fill in this expense claim from the receipt I attached." "Compare these three supplier quotes (attached) and flag differences in payment terms." |
| **Customer support** | "Summarise this ticket thread and draft a reply in our house style." Custom instructions keep tone and sign-off consistent. |
| **Web, QA and marketing** | "Audit this page's speed and accessibility and list the top fixes." A scheduled tile that checks key pages every morning. "Click through the signup flow and tell me where it breaks." |
| **Compliance and security** | Protected sites keep Tootsy away from sensitive systems, always-ask sites need human approval, the page guard blocks planted instructions, and the **action log** exports to CSV for audits. |
| **Data governance** | Point Tootsy at a company-approved model: a local Ollama or an internal OpenAI-compatible gateway. Page content and files then never leave the company. Save the gateway as a **profile** so staff can't mistype it. |
| **Training** | Load training material as files and let new staff ask questions. Prompt tiles walk them through common tasks in each internal tool. |

### 3.3 Walkthrough: onboarding a new hire with My apps

**The problem:** new starters spend their first week asking "where is the expenses tool?" and "what's the link for leave?". Bookmarks sent by email get lost, and a wiki page of links goes out of date.

**The Tootsy way:** IT prepares one My apps file with every company tool, grouped by department, plus a few prompt tiles for common first-week tasks. The new hire imports it once. From then on the tools are one tap away, and they can say "open Payroll" instead of hunting for a link.

<p align="center">
  <img src="images/onboarding-company-apps.png" alt="My apps loaded with company tools: Intranet, Mail, Chat, IT Help, HR, Finance and Engineering folders, and prompt tiles for booking leave and the new-hire checklist" width="300">
  &nbsp;
  <img src="images/apps-menu-import.png" alt="The Import apps option in the My apps menu" width="300">
</p>

#### For IT: build the company set once

1. On any computer with Tootsy, add the company's apps to My apps: **+ Add**, paste each address, and name it the way staff talk about it ("Payroll", not "SAP HCM PRD").
2. Group them: drag one app onto another and hold to make a folder (HR, Finance, Engineering). Put the everyday tools on the main screen.
3. Add prompt tiles for first-week tasks, for example:
   - **New-hire checklist**: "Open intranet.example.com/onboarding and list the tasks I still have to finish this week, with links."
   - **Book leave**: "Open leave.example.com and start a leave request for the dates I give you. Stop before submitting." Leave **Send right away** off, so the new hire adds their dates first.
   - **Get IT help**: "Open helpdesk.example.com and start a ticket describing my problem. Stop before submitting."
4. Export the set: My apps ⋯ → **Export for Tootsy (.json)**. That file is your company set.
5. Publish it where new hires look first: the onboarding email, the intranet's "first day" page, or the laptop's desktop during setup.

You can also write or edit the file by hand. A complete example ships with this guide: [`examples/company-apps.json`](examples/company-apps.json). A trimmed version:

```json
{
  "app": "tootsy",
  "kind": "apps",
  "version": 2,
  "apps": [
    { "name": "Intranet", "url": "https://intranet.example.com/" },
    { "name": "IT Help", "url": "https://helpdesk.example.com/", "icon": { "type": "emoji", "emoji": "🛠️", "color": "#ea580c" } },
    {
      "type": "folder",
      "name": "HR",
      "items": [
        { "name": "Payroll", "url": "https://payroll.example.com/" },
        { "name": "Leave", "url": "https://leave.example.com/" }
      ]
    },
    {
      "type": "prompt",
      "name": "New-hire checklist",
      "prompt": "Open intranet.example.com/onboarding and list the tasks I still have to finish this week, with links.",
      "send": true,
      "hands": true
    }
  ]
}
```

- Leave out `icon` and Tootsy fetches each site's own icon when the file is imported. Or set an emoji and colour, as above, or letters: `{ "type": "letters", "letters": "PY", "color": "#16a34a" }`.
- Folders hold apps and prompt tiles. Folders can't contain folders.
- Only `http(s)` and `chrome://` addresses are accepted. Anything else is dropped when the file is imported.
- Already have the links as browser bookmarks? Export them from the browser's bookmark manager as an HTML file. Tootsy imports that too, and each bookmark folder becomes a Tootsy folder.

#### For the new hire: import it once

1. Install Tootsy and connect it to the company model (IT usually gives you the endpoint, or a backup file with it already set).
2. In My apps, click ⋯ → **Import apps…** and choose the company file.
3. Done. Tap a tile to open a tool, or ask Tootsy: "open Payroll", "run New-hire checklist".

Importing again later is safe. Apps you already have are skipped, and folders with the same name are merged, so IT can send an updated file when tools change.

#### Rolling it out to many people

- **Install Tootsy for everyone**: add Tootsy's extension ID, `ciibbiepfffkcddkgmdbnlibjjhahmld`, to Chrome's **ExtensionInstallForcelist** policy (Google Admin console, or Group Policy / Intune on Windows). Edge has the same policy. Tootsy then appears on every managed browser automatically.
- **Pre-set the model**: set up one computer with the company endpoint and a profile, then Settings → Backup → **Export backup…**. New hires import that backup instead of typing settings. The backup includes any API key, so share it only through internal channels.
- **Keep sensitive systems off-limits**: put payroll, banking and admin consoles in **Protected sites** before you export the backup, so every new hire starts with the same guardrails.

> Tootsy doesn't yet read its apps list from browser policy. Today the new hire imports the file once, which takes a few seconds.

---

## 4. Troubleshooting

| Problem | Fix |
|---|---|
| "Ollama isn't running" | Start the Ollama app, or run `ollama serve` in a terminal. |
| "Model not found" | Download it: `ollama pull gemma4:e4b`, then click **Fetch** in settings. |
| Tootsy answers without looking at the page | The model may not support tools; Tootsy shows a warning when that's the case. Choose a tool-capable model such as `gemma4`, `qwen2.5` or `llama3.1`. Very small models sometimes skip tools, so try a bigger one. |
| Long pages get cut off (Ollama) | Use `http://localhost:11434` rather than `.../v1`, and leave **Context window** on Auto. |
| "Cannot access this page" | Chrome doesn't let extensions read its own pages (`chrome://…`) or the Web Store. Try on a normal website. |
| The microphone doesn't work | Click the mic again. Tootsy opens a small tab where Chrome asks for microphone access. Allow it, then return to the panel. |
| A scheduled prompt didn't run | Scheduled prompts run only while Chrome is open. Check the times in Settings → **Scheduled prompts**. |
| A hands-free task keeps asking for approval | The site isn't one you opened or named, or it's on your "always ask" list. Choose **Approve & trust** for sites you know. |
| A tool is missing from the answer | With **Send only the tools each request needs** on, Tootsy picks tools per message. Ask more directly ("fill in this form…"), or turn the setting off. |

---

## 5. Privacy in one minute

- Tootsy sends page content, your messages and your files **only to the model endpoint you choose**. With a local model, nothing leaves your computer.
- The developer runs no servers and collects nothing: no analytics, no tracking, no account.
- Settings, chats, notes, files and the action log are stored in your browser profile. **Sync across computers**, if you turn it on, copies only your My apps list (names, links, prompts, folders; no images) through your own Chrome sync.

---

## 6. Permissions

Chrome shows these when you install Tootsy. Here is what each one is for.

| Permission | Why Tootsy needs it |
|---|---|
| Side panel, storage, unlimited storage | The panel itself, your settings, notes, apps and the index of files you add |
| Read and change data on websites, active tab, scripting | Reading and acting on the page you ask about, only when you ask |
| Declarative net request | Lets local AI servers such as Ollama accept Tootsy's requests; it doesn't touch any web page's traffic |
| Bookmarks, clipboard (write) | The bookmark and copy tools |
| Debugger | Console, network and JavaScript tools and PDF export. Used only when you turn on DevTools-level tools, and only for the length of one step |
| Context menus | The right-click "Ask Tootsy" entries |
| Alarms, notifications | Scheduled prompts and the notification when one finishes |
| History (optional) | Asked for only if you turn on history search |

---

<p align="center"><a href="https://chromewebstore.google.com/detail/Tootsy/ciibbiepfffkcddkgmdbnlibjjhahmld"><b>Get Tootsy from the Chrome Web Store</b></a></p>
