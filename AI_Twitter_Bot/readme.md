✅ *Workflow Overview: X AI Agent

**This agent:
	•	Posts tweets automatically at scheduled hours (AM/PM).
	•	Uses Telegram to approve, reject, or regenerate tweets.
	•	Selects the best LLM dynamically to reduce cost + boost speed.
	•	Sends tweets with or without image previews.
	•	Logs and tracks content over time.

⸻

🧠 **Key Modules & Logic

1. Triggers
	•	Schedule Trigger
	•	Runs at 11 AM (relatable/short) and 5 PM (tactical/long).
	•	Telegram Trigger
	•	Allows manual tweet input or reacts to approval buttons: ✅ 🔄 ❌

⸻

2. Initial Routing Logic
	•	Code Node
	•	Distinguishes between:
	•	Scheduled flow (uses hour to choose AM/PM content)
	•	Telegram message (extracts caption + file_id)
	•	Outputs: format, tone, context, prompt, image_attached

⸻

3. Dynamic Model Selection
	•	Model Selector Agent
	•	Chooses the cheapest + best-fit model:
	•	gemini-2.0-flash-001 (fast/lightweight)
	•	gpt-4.1-mini, claude-3.7-sonnet, openai/o1 depending on input

⸻

4. Tweet Generation
	•	X Bot Agent
	•	Uses:
	•	Dynamic LLM from above
	•	Prompt + Context
	•	Style Guide: tactical, raw, 21yo founder tone
	•	Rules: line limits, no emojis/hashtags, high punch

⸻

5. Tweet Preview
	•	Switch Node
	•	If image_attached = true, uses:
	•	Download Image → Preview Photo
	•	Else:
	•	Preview Chat (text-only tweet)

⸻

6. Inline Approval
	•	Node: Inline Approval
	•	Sends buttons via Telegram:
	•	✅ Approve
	•	🔄 Regenerate
	•	❌ Stop

⸻

7. Approval Decision Tree
	•	Check Approve → Posts tweet (X) → Sends confirmation
	•	Check Regenerate → Loops back to Code
	•	Check Stop → Sends cancel confirmation

⸻

8. Tweet Posting
	•	X Node (Twitter)
	•	Posts final tweet after approval
	•	Confirmation Response
	•	Sends “✅ Tweet Posted ✅” to Telegram

⸻

9. Memory Management
	•	Tweet Memory + Chat Memory Manager
	•	Logs tweet format, model, context for traceability

⸻
