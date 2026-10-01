# Tootsy — Privacy Policy

_Last updated: 2026-09-25_

Tootsy is a Chrome extension that connects your browser to an LLM endpoint **you choose** (a local Ollama/LM Studio server, an OpenAI-compatible server, the Anthropic API or Google Gemini). The developer of Tootsy runs no servers and receives no data from the extension.

## What Tootsy processes

- **Page content** — when you ask about a page or give a browsing task, Tootsy reads text, links, form fields and (if you ask for a screenshot) an image of the current tab, and sends what is needed to *your configured endpoint* as part of the conversation.
- **Your prompts, files and images** — text you type, files and images you add to the panel, and the text of PDFs you open are stored locally (IndexedDB / `chrome.storage`) and sent to your endpoint when relevant.
- **Settings** — endpoint URL, API key, model choices, custom instructions, site lists, notes, My apps (links, prompt tiles, folders), chat history and the action log are stored locally in your browser profile.
- **My apps sync (off by default)** — if you turn on "Sync My apps across my computers", the names, links, prompt text, folders and schedules of your My apps are stored in your own Chrome sync storage (your Google account), so Chrome can copy them to your other computers. Icon images, chats, files, notes, API keys and other settings are never synced. Turning it off stops syncing from that computer.

## Where data goes

- Only to the endpoint URL you entered in settings. If that is a hosted provider (OpenAI-compatible, Anthropic, Gemini), that provider's privacy policy applies to what you send.
- Web search uses a normal DuckDuckGo or Bing results page opened in a background tab; those sites see the query like any other visit.
- Nothing is sent to the extension developer. There is no analytics, telemetry, crash reporting or advertising.

## Optional permissions and features

- **History** search is off by default and only enabled when you opt in; results are used to answer your question and are not stored.
- **DevTools-level tools** (console logs, network capture, running JavaScript, PDF export) attach Chrome's debugger only for the duration of a single tool call and only when you turn the toggle on.
- **Scheduled prompt tiles** run in the background with the same endpoint and store their result as a chat locally.
- **Protected sites**: domains you list in settings are never acted on (clicks, typing, navigation, scripts).
- **App lists** you subscribe to, or that your organization sets, are downloaded from the address given, with your browser's normal sign-in for that site. Nothing about you is sent to it beyond what any page visit sends.
- **Organization policy**: if your organization manages Tootsy, it can set company apps, default or locked settings and which AI servers are allowed. Tootsy only reads that policy; it reports nothing back.
- **Email drafts** open in the mail service you choose (Gmail, Outlook or your mail app). The draft's recipient, subject and text travel in the link to that service, and you decide whether to send it.
- **Clipboard reading** is an optional permission, asked for only when a prompt tile uses `{{clipboard}}`, and used only to fill that blank.
- **Page guard**: pages are checked, on your computer, for text that tries to instruct the assistant. Anything found is shown to you and noted in the local action log. Sites you choose to trust for typing are kept in your local settings.

## Data retention and deletion

Everything lives in your Chrome profile (and, only if you turn on My apps sync, your My apps list in your Chrome sync storage). Delete chats, notes, tasks, files or the action log from the panel, use **Backup → Export** to take a copy, or remove the extension to delete all of it. Backups you export contain your API keys — treat them as secrets.

## Contact

Open an issue at https://github.com/rbughao/tootsy/issues.
