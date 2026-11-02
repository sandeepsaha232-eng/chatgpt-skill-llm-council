# LLM Council for ChatGPT

Turn one question into five advisor opinions, an anonymous peer review, and a final verdict, inside ChatGPT.

This is a ChatGPT port of the Claude skill [aiwithremy/claude-skills-llm-council](https://github.com/aiwithremy/claude-skills-llm-council) (built by Ole Lehmann, based on Andrej Karpathy's [LLM Council](https://github.com/karpathy/llm-council)). The five advisors, the peer-review step and the verdict structure are the same. Only the packaging changed, because ChatGPT has no "skills" folder.

## The five advisors

| Advisor | Job |
|---|---|
| Contrarian | Hunts for the fatal flaw |
| First Principles Thinker | Asks what you are actually trying to solve |
| Expansionist | Finds the upside everyone else missed |
| Outsider | Zero context, catches the curse of knowledge |
| Executor | Fastest path, what to do Monday morning |

Then: anonymized peer review (strongest, biggest blind spot, what all missed) and a Chairman's verdict (agree, clash, blind spots, recommendation, one thing to do first).

## Install (pick one)

### Option A: Custom GPT (recommended, reusable)
Needs a ChatGPT plan that can create GPTs.
1. ChatGPT sidebar > **Explore GPTs** > **Create**.
2. Open the **Configure** tab.
3. Name: `LLM Council`. Description: `Pressure-test any decision with 5 advisors, peer review, and a verdict.`
4. Open [`custom-gpt-instructions.md`](custom-gpt-instructions.md), copy everything, paste into **Instructions** (it fits the 8,000 character limit).
5. Add conversation starters, for example: `Council this: ...`, `Pressure-test my plan`, `I'm torn between two options`.
6. Turn off Web Search and Image Generation if you want pure reasoning. Save.

Use it by opening the GPT and typing `council this: <your decision>`.

### Option B: One-shot prompt (works on any plan)
Copy [`one-shot-prompt.md`](one-shot-prompt.md) into any chat and paste your decision at the bottom.

### Option C: Projects
Create a ChatGPT Project and paste `custom-gpt-instructions.md` into the project's instructions. Every chat in that project then behaves as the council.

## Trigger phrases
`council this`, `run the council on ...`, `pressure-test this`, `stress-test this`, `war room this`, `debate this`

## Good and bad questions
Good: "Should I build a $97 workshop or a $497 course?", "I'm thinking of pivoting from X to Y. Am I crazy?", "Which of these 3 angles is strongest?"
Bad: "Capital of France?", "Write a tweet", "Summarize this". Those are answered normally.

## Differences from the Claude version
- **No real sub-agents.** Claude spawns 5 separate advisors in parallel, then 5 separate reviewers, then a chairman. ChatGPT does all stages in one reply, so the advisors are less independent. The instructions tell it to write each advisor in isolation and shuffle the review labels, which helps but does not fully replicate separate agents.
- **No workspace scan.** The Claude skill reads CLAUDE.md and memory files. In ChatGPT, give context in your message or attach files.
- **One combined peer review** instead of five.
- **No transcript files.** Everything stays in chat.

For more independence, run the stages as separate messages: ask for the five advisors only, then say "now do the anonymous peer review", then "now the chairman's verdict".

## Credit
Original skill by [Ole Lehmann](https://x.com/itsolelehmann). Methodology from Andrej Karpathy's LLM Council. This repo is an unofficial adaptation for ChatGPT.
