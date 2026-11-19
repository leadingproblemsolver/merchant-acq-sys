INTENT.md

Upgrade the existing RealX Conversation Engine V3 in place. Do not rebuild it.

Use these existing artifacts:
- RealX JSON Conversation Adapter
- ICP Lead Intelligence Engine
- RealX Conversation Engine V3
- MarketOS evidence ledger

Build ONE application with ONLY THREE SCREENS:

1. LEADS
Import the exact uploaded Qatar restaurant JSON array.
Preserve original Google Place IDs.
Filter by area, restaurant category, price band, rating and available contact route.
Choose five merchants.
Do not claim ICP relevance implies buying intent.

2. CONVERSATION
For the selected merchant, show source facts and one student-acquisition value hypothesis.
Generate one opening question using the existing deterministic Conversation Mapper.
Allow human entry of the actual contact attempt and exact merchant reply.
Generate the next question based on the reply.
Keep simulated replies in a separate DEMO namespace; never count simulations as real outreach.

3. HANDOFF
Record a mutually agreed meeting, named RealX AE and supporting reference.
Do not mark the meeting VERIFIED without confirmation evidence.
Generate an AE handoff brief.
Track attempts, meaningful replies, confirmed meetings and AE-accepted handoffs.

ARCHITECTURE:
Reuse existing domain logic and tests.
One source schema adapter, one account/event store, one conversation mapper.
Offline/local-first is acceptable for this pilot.
No authentication, browser agent, live sending, scraping, CRM replacement or payment system yet.

ACCEPTANCE TEST:
Import the provided JSON → filter five merchants → choose one → generate opening → record real reply → produce next question → record confirmed meeting → generate AE handoff → export JSON.

Preserve provenance, distinguish observed evidence from hypotheses, prevent false meeting states, and add regression tests.

Return changed files, test results and remaining external blockers.




# **REF MarketOS → RealX: One unified acquisition pipeline**

**Everything we've built should become one execution loop, not six separate applications.**

The system takes a raw Qatar business JSON export, identifies relevant merchants, prepares a context-specific conversation, records what actually happens, and advances qualified merchants to a RealX account executive.

**1. LEAD INTAKE**

Your restaurant JSON / future compatible exports

**2. ICP FILTER + RANK**

Area, category, price band, public business signals, exclusions

**3. ACCOUNT INTELLIGENCE**

Source facts → value hypotheses → decision-maker route

**4. CONVERSATIONAL MAPPER**

Opening → real reply → next question → qualification

**5. OUTREACH + FOLLOW-UP**

Authorized channel → actual messages → response receipts

**6. QUALIFIED MEETING + AE HANDOFF**

Buyer agreement → confirmed meeting → RealX accepts

**7. SETTLEMENT + LEARNING**

Conversion metrics → objections → improved targeting

The key distinction is that **stages 1–4 prepare the opportunity, stages 5–6 produce external commercial evidence, and stage 7 improves the next cycle.**

## **Minimum viable integration: 4 blocks, 1 application**

**Do not merge every feature. Connect only the parts needed to produce one qualified RealX merchant meeting.**

1

**JSON Import + ICP Filter**

Reuse: Existing JSON Conversation Adapter

Output: Select 5 relevant merchants

2

**Conversation Mapper**

Reuse: Existing V3 + Student First Client logic

Output: One opening question and response-based follow-up

3

**Contact + Meeting Ledger**

Reuse: Existing RealX Meeting Engine

Output: Record actual attempt, reply and agreed meeting

4

**AE Handoff + KPI**

Reuse: Existing MarketOS event ledger

Output: Evidence-backed handoff and conversion report

### **Only 3 screens**

| Screen           | Required functionality                                                       |
| ---------------- | ---------------------------------------------------------------------------- |
| **Leads**        | Import exact JSON, filter, rank, choose merchant                             |
| **Conversation** | View merchant facts, draft opening, enter real reply, generate next question |
| **Handoff**      | Record agreed meeting, AE owner, receipt and KPI status                      |

### **One canonical record**

```
{
  "merchant_id": "original Google Place ID",
  "source": {},
  "icp_score": 0,
  "qualification": "UNVERIFIED",
  "value_hypothesis": "STUDENT_ACQUISITION",
  "decision_maker": null,
  "conversation_events": [],
  "next_action": null,
  "meeting": null,
  "ae_handoff": null
}
```

Use the original JSON ID for deduplication. Keep the raw source data intact, and store conversation events separately so imports don't overwrite real work.

Use this with the existing source package in Google AI Studio Build or Replit.

&#x20;Copy minimal integration prompt

**Strict stop condition:** Once the three screens work and the JSON-to-handoff test passes, stop building.

The next job is **five real merchant approaches**, not another technical iteration. Success is one independently confirmed meeting accepted by a named RealX AE.