# Ava — AI voice agent

**An AI phone agent that answers a locksmith company's calls and books jobs straight into the CRM.**

*Showcase page. The code and prompts are private because they run a live business; a walkthrough is available on request.*

---

## What she does

- Answers calls in a natural voice, works out what the caller needs, collects the details, and **books the job** into [Ava Connects](https://github.com/alon005/ava-connects) through tool calls.
- Looks up existing jobs, reschedules, passes messages to the technician, adds notes for the office, and escalates to a person when needed.
- Knows the company's rules: what we do and don't do, when to quote a price and when not to, and how to handle prices, complaints and after-hours calls.

She was first built on top of the master dashboard and Workiz, then moved onto Ava Connects.

## Numbers

Since 10 Aug 2026 she has answered **639 calls** and **booked 306 jobs on her own**.

## What's built around her

- **Tool layer:** about a dozen tools into the CRM (book, edit, look up, message the technician, escalate and more), each one validating what she sends and telling her plainly what happened.
- **Callback judge:** when a call drops before booking, an AI judge (Gemini) reads the call twice and decides whether she should call back. She only calls when both reads are at least 90% sure.
- **Callbacks with memory:** every callback carries the whole earlier call, so she picks up where it stopped instead of starting over. If the caller went to get something (an address, a gate code), the office is told to call first, and she calls only if nobody has. She checks the phone system live first.
- **Guards:** a claim guard posts an escalation if she says she flagged something but didn't; a wrong-state guard stops a job being sent to the wrong market.
- **Testing by replay:** every change is replayed against real past calls before it goes live, and every prompt is published only after a review.

**Stack:** Retell · Gemini · Cloudflare Workers · TypeScript · Postgres

— Alon Schneidman · [GitHub](https://github.com/alon005) · [LinkedIn](https://www.linkedin.com/in/alonschneidman)
