# Prompt Evaluation: `quick_prompt.md`

## Overall Score

| Parameter | Score |
|---|---:|
| Prompt Clarity | 33 / 100 |
| Output Quality | 18 / 100 |
| Efficiency | 14 / 50 |
| **Total** | **65 / 250** |

## Executive Summary

The evaluated file is a polished, highly structured canteen strategy document, but it is not a model-facing prompt: it presents a completed plan without telling a model what to do. As supplied, it therefore provides little control over a future model's role, task, response format, assumptions, or factual checks. Its strongest prompt-adjacent qualities are clear sectioning and concrete operational details. The main improvements are to turn it into an instruction with explicit inputs and output requirements, and to require arithmetic and budget reconciliation before presenting financial conclusions.

**Evaluation scope:** The target is assessed as supplied, not as an inferred original request. The optimized rewrite below reconstructs a likely intended task from the document's subject and contents; it is not a claim about the missing original prompt.

## Evaluated Prompt Analysis

- **Source:** [`quick_prompt.md`](quick_prompt.md), evaluated in full.
- **Opening text:** “# CAMPUS FLAVOR PULSE / ## A Dynamic Demand-Driven College Canteen Strategy”
- **Estimated size:** 8,919 characters and 1,398 whitespace-delimited word-like units; approximately **2,230 tokens**, estimated as characters divided by four. This is a rough estimate, not a tokenizer measurement.
- **Structure:** Eleven numbered sections, several Markdown tables, operational bullets, two contingency scenarios, and a closing tagline. The document reads as a finished proposal, not a prompt template: there is no explicit task directive, model role, input block, output contract, or variable placeholder.

## Detailed Parameter Breakdown

### 1. Prompt Clarity: 33 / 100

| Criterion | Score | Evidence and rationale |
|---|---:|---|
| Role & Persona Definition | 0 / 20 | No model role or expertise is assigned. “Campus Flavor Pulse” names the strategy, not the assistant. |
| Task Specificity & Negative Constraints | 3 / 25 | The document describes actions, such as “Predict → Batch → Serve → Track → Adapt,” but never instructs a model to produce, analyze, or revise anything. No out-of-scope constraints are specified. |
| Instruction Structure & Delimiters | 12 / 20 | The eleven numbered sections and tables are easy to scan, but they organize a finished deliverable rather than separating instructions, inputs, and expected output. |
| Tone, Style & Target Audience | 8 / 15 | The operational subject and campus context imply a canteen manager audience, but the intended reader and desired response tone are not stated as instructions. |
| Unambiguous Language | 10 / 20 | Many quantities and procedures are concrete, but key terms and calculations are not fully defined. For example, the basis for “Break-Even Quantity: ~404 units” is absent. |
| **Subtotal** | **33 / 100** | |

### 2. Output Quality & Schema Guidance: 18 / 100

| Criterion | Score | Evidence and rationale |
|---|---:|---|
| Output Format & Schema Enforcement | 8 / 30 | The file itself uses tables and headings, but it does not require a future response to follow a schema, headings, length, or output-only rule. |
| Few-Shot Examples & Demonstrations | 0 / 25 | No input/output examples demonstrate how a model should respond. The menu is content, not a prompt demonstration. |
| Edge Cases & Fallback Instructions | 7 / 25 | “Demand Suddenly Surges (+40% unexpected crowd)” and “Demand Plummets (-50% due to rain/festivals)” are useful operational contingencies. They do not explain how a model should handle missing, ambiguous, or conflicting inputs. |
| Factuality & Hallucination Prevention | 3 / 20 | The note that figures are “ESTIMATES” is a useful qualification, but there are no source requirements or verification rules. The figures also contain apparent reconciliation problems: the item-level sales prices imply Monday revenue of ₹6,000 (48×₹30 + 63×₹60 + 39×₹20), versus ₹4,980 in the daily financial table. Across all days, item-level revenue calculates to ₹41,245, versus the stated ₹33,490. The opening claim of waste “below **2%**” conflicts with the reported 3.2%. |
| **Subtotal** | **18 / 100** | |

### 3. Efficiency & Token Economy: 14 / 50

| Criterion | Score | Evidence and rationale |
|---|---:|---|
| Conciseness & Fluff Elimination | 5 / 15 | The sectioning helps navigation, but the financial summary and KPIs repeat figures, and the closing promotional tagline does not add operating instructions. |
| Token Economy & Context Footprint | 5 / 15 | At roughly 2,230 estimated tokens, the document carries substantial detail without telling a model how to use it. Some of that detail could be generated from compact inputs and a defined output contract. |
| Dynamic Parameterization | 0 / 10 | Campus size, capture rate, budget, reserve, waste target, and currency are hard-coded or embedded in prose; none is a clearly delimited variable. |
| Signal-to-Noise Ratio | 4 / 10 | The central operating idea is easy to identify, but promotional claims and repeated KPIs compete with the assumptions and calculation rules needed to make the plan reliable. |
| **Subtotal** | **14 / 50** | |

## Actionable Recommendations

1. Replace the finished-report opening with an explicit task, such as creating a seven-day canteen menu and operating plan from supplied constraints.
2. Define the model's role, audience, currency, campus assumptions, budget, reserve, meal periods, and target waste rate as delimited inputs.
3. Specify required output sections and tables, including the formulas and denominator for revenue, material cost, gross profit, waste rate, and break-even quantity.
4. Require arithmetic reconciliation across the menu, daily financial table, weekly totals, inventory plan, and KPI summary; label estimates and expose any unknowns.
5. Define a fallback for missing or contradictory inputs: ask focused questions when a required input blocks the plan; otherwise state assumptions and flag unresolved figures instead of inventing certainty.
6. Remove claims that cannot be supported by the calculations, including “below 2%” unless the resulting waste calculation meets that target.

## Optimized Prompt Rewrite (Production-Ready)

The source is a completed strategy, so this rewrite infers the likely task: generate a financially reconciled, practical seven-day college canteen plan. Replace the sample input values with the intended values before use.

```text
<role>
You are an operations and financial-planning assistant for a small college canteen. Produce practical plans and show assumptions; do not present estimates as verified facts.
</role>

<task>
Create a seven-day menu, demand-based preparation plan, and cash-aware operating budget for a college canteen using the inputs below. Optimize for student affordability, freshness, low food waste, and positive gross profit without exceeding the available budget.
</task>

<inputs>
  <campus_size>{200 students}</campus_size>
  <expected_daily_capture_rate>{60%}</expected_daily_capture_rate>
  <planning_period>{7 days}</planning_period>
  <currency>{INR (₹)}</currency>
  <total_starting_budget>{₹10,000}</total_starting_budget>
  <protected_emergency_reserve>{₹1,500}</protected_emergency_reserve>
  <meal_periods>{breakfast, lunch, evening snacks}</meal_periods>
  <maximum_target_waste_rate>{2%}</maximum_target_waste_rate>
  <dietary_and_equipment_constraints>{provide constraints or write "none provided"}</dietary_and_equipment_constraints>
  <local_prices_or_costs>{provide known prices/costs or write "not provided"}</local_prices_or_costs>
</inputs>

<method>
1. Treat supplied inputs as constraints. Label all unsupplied demand, price, and cost figures as estimates; do not imply they were researched or verified.
2. If a missing or contradictory input prevents a defensible plan, ask up to five concise clarifying questions before drafting. Otherwise, proceed with clearly stated assumptions.
3. For each menu item, show planned quantity, expected units sold, selling price per unit, estimated cost per produced unit, and expected unsold quantity. Ensure expected sales plus expected unsold quantity does not exceed planned quantity.
4. Calculate expected revenue as expected units sold × selling price. Calculate material cost on planned production, including unsold portions, as planned quantity × cost per produced unit. Calculate gross profit as revenue minus material cost. State that this is gross profit before labor, utilities, rent, taxes, and other unprovided costs.
5. Calculate waste rate as expected unsold quantity ÷ planned quantity. State the denominator. Do not claim the target is met unless the calculated result meets it; if not, revise the plan or report the shortfall.
6. Reconcile every daily subtotal with its item rows and every weekly total with the daily subtotals. Verify budget feasibility with a day-by-day cash flow: do not rely on future sales to fund purchases made before those sales are received. Keep the protected reserve separate unless the input explicitly authorizes using it.
7. Define any demand-adjustment rule and batch-release trigger precisely. Ensure triggers fit the listed serving times and production quantities.
8. Calculate break-even units only if the required fixed costs and contribution margin are supplied or can be stated as explicit assumptions. Otherwise report that break-even cannot be determined from the inputs.
</method>

<output>
Return concise Markdown with these sections:
1. Assumptions and unresolved inputs.
2. Seven-day menu table with the item-level fields defined above.
3. Daily and weekly financial table: units sold, revenue, production material cost, gross profit, unsold units, and waste rate.
4. Initial purchasing and protected-reserve allocation, followed by day-by-day cash flow and budget checks.
5. Demand forecast and batch-release rules.
6. Contingency actions for higher and lower demand, including their cash impact.
7. Student feedback and service actions, with costs labeled or marked unknown.
8. KPI summary and a reconciliation check listing any target that is not met.
</output>

<constraints>
- Use the supplied currency consistently and format monetary values clearly.
- Do not invent supplier quotes, local market facts, fixed costs, or guaranteed outcomes.
- Do not count the same cost twice or mix units sold with units produced.
- If an arithmetic check fails, correct the tables before responding; if inputs are insufficient to resolve it, flag the discrepancy.
- Keep recommendations operational and distinguish facts, calculations, and assumptions.
</constraints>
```
