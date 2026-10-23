---
name: robomark-requirements-shredder
description: "Analyze Government RFP documents (BAA, CSO, PWS, SOW, Section C, L, M, etc.) to perform comprehensive requirements shredding and generate a Compliance and Traceability Matrix spreadsheet. Use when the user asks to \"shred an RFP\", extract proposal requirements, build a compliance matrix, or analyze government solicitation documents for formatting, cost, and technical/material requirements."
---
# RFP Requirements Shredder

Extract, categorize, and structure all explicit and implicit requirements from Government Request for Proposals (RFP) documents into a comprehensive Compliance and Traceability Matrix spreadsheet designed for proposal writers, Red Team, and Gold Team reviewers.

## When to Use

- The user provides one or more Government RFP documents (e.g., Statement of Work (SOW), Performance Work Statement (PWS), Section L Instructions, Section M Evaluation Criteria, Pricing/Section B) and asks to shred them or extract requirements.
- The user asks for a proposal compliance matrix, requirements traceability matrix, or RFP breakdown.
- The user wants to ensure their government proposal incorporates all formatting rules, cost criteria, key phrases, and evaluation triggers.

## Steps

### 1. Gather and Inventory RFP Documents
Identify all solicitation documents provided in the conversation or located in the user's workspace. If multiple documents are involved (e.g., Main Solicitation, PWS/SOW, Q&A Amendments, Pricing Attachments), inventory them so you can accurately cite which document and section each requirement originates from.

### 2. Perform Deep Requirements Shredding
Scan the documents systematically for mandatory directives ("shall", "must", "will", "is required to") as well as evaluation-critical directives ("should", "may", "evaluated on", "demonstrate"). Make sure each identified requirement matches 

Requirements should be fine-grained. For example, if there is a prescribed statement of work outline format in the RFP, there should be a single requirement for each section of the SOW outline format from the RFP - **not** a single requirement for a SOW in the proposal.

If the RFP documents contain multiple "topic areas", "focus areas", or "areas of interest" where we may bid against only one, some, or all areas, please stop and ask the user which topic or focus area(s) the user plans to bid on before continuing. Disregard instructions that are exclusively for topic or focus areas not selected by the user.

Categorize every extracted item into one of three required groups:

- **Compliance**: Administrative, formatting, and submission rules (typically found in Section L or equivalent). Include font type and size, margins, page limits per volume, file naming conventions, submission portals/deadlines, required forms/certifications (e.g., SF33, SF1449, Reps & Certs), and organizational structure.
- **Cost**: Pricing and business volume requirements (typically Section B, Section L Cost Instructions, Section M Cost Evaluation). Include contract type (FFP, T&M, Cost-Plus), labor categories, rate build-up rules, Indirect Rate caps, BOE (Basis of Estimate) requirements, and price template formatting.
- **Material**: Technical, management, past performance, and substantive scope requirements (typically Section C/PWS/SOW, Section L Technical, Section M Evaluation Factors). Include:
  - What the offeror must *demonstrate*, prove, or substantiate for a high-quality, fully responsive proposal.
  - Exact **key phrases, buzzwords, and agency terminology** from the RFP that must be mirrored in the proposal response.
  - Alignment between instructions (Section L) and evaluation criteria (Section M) to highlight high-scoring discriminators.
  - Split this section out by response volume defined in the RFP
- **Other**: Any other requirements for the proposal that do not fit elsewhere.

### 3. Build the Requirements Matrix Spreadsheet
Organize the extracted requirements grouped clearly by **Compliance**, **Cost**, and **Material** (either using a dedicated `Category` column sorted by those three groups, or structured with clear group header rows).

Include the following columns in the spreadsheet:

- **Req ID**: Unique identifier (e.g., `COMP-001`, `COST-001`, `MAT-001`).
- **Category**: `Compliance`, `Cost`, or `Material`.
- **RFP Document & Section**: Exact document name, section number, paragraph, or page reference (e.g., `Section L.4.2, p. 42` or `PWS 3.1.2`).
- **Requirement & What to Demonstrate**: Clear statement of the requirement, including specific instructions on what the proposal must demonstrate to be fully responsive and high-scoring.
- **Key Phrases / Terms to Incorporate**: Exact terminology, acronyms, or phrases from the RFP to echo in the response (if any)
- **Proposal Volume / Section Mapping**: Placeholder column for the team to map where this requirement is addressed in the response.
- **Compliance Status**: Placeholder for tracking (e.g., `Not Started / In Progress / Compliant`).
- **Red Team Comments**: Blank column dedicated to Red Team reviewers (focusing on compliance, technical depth, win themes, and scoring against Section M).
- **Gold Team Comments**: Blank column dedicated to Gold Team reviewers (focusing on final executive sign-off, pricing alignment, and strategic polish).

### 4. Validate spreadsheet against RFP data
- Revisit the RFP material and validate that the spreadsheet contains:
  - All the necessary requirements from the RFP documents
  - Each requirement listed should contain one logical task that can be identified as complete or not- multiple logically individual requirements should be listed individually.
  - Each requirement should be listed only once within the spreadsheet.
  - No requirements that do not exist in the documents (clean up hallucinations)

### 5. Deliver the Spreadsheet Output
- If creating a Google Sheet using workspace tools, format it as clean CSV data with all fields properly escaped.
- If creating a Google Sheet using workspace tools, format the document for easy reading and group rows strictly by `Compliance`, `Cost`, `Material`, and `Other`.
- If generating a downloadable file (`.xlsx` or `.csv`) or Markdown preview, ensure all columns are present and grouped strictly by `Compliance`, `Cost`,`Material`, and `Other`.
- Alongside the spreadsheet, provide a brief executive summary highlighting any "killer" compliance traps (e.g., strict page limits, unusual font rules on graphics/tables) and top evaluation discriminators discovered during the shred.

## Gotchas

- **Missing implicit Section M requirements**: Never shred only the SOW/PWS or Section L. Always cross-reference Section M (Evaluation Factors). Sometimes Section M evaluates criteria not explicitly requested in Section L; flag these under `Material` requirements so the proposal team doesn't miss points.
- **Overlooking graphic and table formatting rules**: Government RFPs frequently allow smaller font sizes for tables and graphics (e.g., 8pt or 9pt vs. 12pt Times New Roman for body text). Always extract both body and graphic/table rules separately under `Compliance`.
- **Summarizing away key terms**: Proposal evaluators look for their own language. Do not overly paraphrase technical requirements without preserving the exact RFP terminology in the `Key Phrases / Terms to Incorporate` column.
- **Vague section citations**: "Section C" is not helpful for a Red Team reviewer. Always capture the most granular reference available (e.g., `Section C.3.2.1` or `Attachment 1 PWS, Para 4.b`).
