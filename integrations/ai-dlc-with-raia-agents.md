# AI DLC with raia Agents

## AI-DLC: AI-Powered IDE vs. AI Agent Trained on Key Data

### Core distinction

* **AI-powered IDE** = best for **building**
* **AI agent trained on key data** = best for **deciding, grounding, and orchestrating**

The AI-powered IDE is strongest when the task is local to the codebase and editor workflow: writing code, refactoring, generating tests, fixing bugs, explaining code, and making multi-file edits.

The AI agent trained on key data is strongest when the task depends on business context outside the code itself: requirements, customer commitments, architecture constraints, policies, prior incidents, product behavior, support history, integration docs, and operating procedures.

### Comparison matrix

<table><thead><tr><th width="175.45037841796875">AI-DLC area</th><th>AI-powered IDE is better at</th><th>AI agent trained on key data is better at</th></tr></thead><tbody><tr><td>Requirements</td><td>Turning a spec into stories, code tasks, schemas, and API shapes</td><td>Clarifying what the customer actually needs, pulling prior decisions, surfacing edge cases from docs, tickets, and calls</td></tr><tr><td>Design</td><td>Suggesting patterns, scaffolds, interface shapes, and starter architectures</td><td>Recommending designs that fit the company’s real stack, integration constraints, security rules, and client commitments</td></tr><tr><td>Coding</td><td>Generating functions, classes, endpoints, boilerplate, refactors, and migrations</td><td>Explaining which implementation is correct for a specific client, workflow, policy, or business rule</td></tr><tr><td>Testing</td><td>Creating unit and integration tests, mocks, assertions, and edge-case coverage</td><td>Identifying what truly matters to test based on production failures, SLAs, support history, and customer-specific workflows</td></tr><tr><td>Documentation</td><td>Auto-writing docstrings, README updates, code comments, and release notes from diffs</td><td>Producing accurate business and process documentation grounded in internal knowledge, not just code changes</td></tr><tr><td>Code review</td><td>Catching syntax issues, style problems, likely bugs, missing tests, and refactor opportunities</td><td>Checking whether a change violates business logic, client-specific rules, operational policies, or contractual expectations</td></tr><tr><td>Debugging</td><td>Explaining stack traces, tracing code paths, and suggesting likely fixes</td><td>Connecting a bug to a known client issue, data dependency, prior incident, integration quirk, or rollout context</td></tr><tr><td>Security / compliance</td><td>Flagging insecure patterns in code and dependencies</td><td>Applying company-specific rules like PII handling, approval flows, regulated workflows, or tenant-specific restrictions</td></tr><tr><td>Deployment</td><td>Generating scripts, CI/CD snippets, rollback steps, and infrastructure changes</td><td>Deciding whether deployment is safe given customer timing, release commitments, open incidents, and operational readiness</td></tr><tr><td>Operations</td><td>Helping inspect logs, queries, code paths, and runbooks</td><td>Acting like an informed operator that knows escalation history, client environments, SOPs, and ownership boundaries</td></tr><tr><td>Knowledge access</td><td>Searching code and editor context well</td><td>Synthesizing across docs, tickets, emails, chats, SOPs, and product knowledge</td></tr><tr><td>Best human role</td><td>Direct the implementation</td><td>Direct the judgment and decision-making</td></tr></tbody></table>

### Quick decision guide

| Question                                         | Better tool                                          |
| ------------------------------------------------ | ---------------------------------------------------- |
| How do I write this?                             | AI-powered IDE                                       |
| What should we build?                            | AI agent trained on key data                         |
| Why is this breaking for this client?            | AI agent trained on key data, often with IDE support |
| Can you generate the implementation and tests?   | AI-powered IDE                                       |
| What constraints do we have to respect?          | AI agent trained on key data                         |
| Does this match how our business actually works? | AI agent trained on key data                         |

### Recommended operating model

* **AI IDE = execution copilot**
* **Data-trained AI agent = context copilot**
* **Human = accountability layer**

### Best-practice workflow in an AI-DLC

1. The **agent trained on key data** defines the right problem, constraints, and acceptance criteria.
2. The **AI-powered IDE** turns that into code, tests, and edits quickly.
3. The **agent** validates the output against business and process context.
4. The **human** approves the final decision.

### Stage-by-stage view

<table><thead><tr><th width="155.19805908203125">Stage</th><th>AI IDE contribution</th><th>Data-trained AI agent contribution</th></tr></thead><tbody><tr><td>Plan</td><td>Converts ideas into technical tasks</td><td>Grounds scope in customer, product, and operational reality</td></tr><tr><td>Build</td><td>Generates and edits code quickly</td><td>Guides implementation choices with domain knowledge</td></tr><tr><td>Test</td><td>Produces tests and code-level validation</td><td>Prioritizes what matters most based on business risk and production history</td></tr><tr><td>Deploy</td><td>Assists with release mechanics</td><td>Advises on readiness, dependencies, and blast radius</td></tr><tr><td>Operate</td><td>Helps diagnose code and infrastructure issues</td><td>Helps diagnose workflow, customer, and knowledge-process issues</td></tr><tr><td>Govern</td><td>Enforces code conventions and patterns</td><td>Enforces policy, business rules, approvals, and traceability</td></tr></tbody></table>

### Key takeaway

The trap is using the AI-powered IDE for something that really needs business memory. That is when teams get fast code that is technically plausible but operationally wrong.

For a company like raia, this usually means:

* The **IDE AI** should help engineers build workflows, transforms, integrations, prompts, and tests faster.
* The **data-trained agent** should know client requirements, implementation notes, escalation history, integration rules, SOPs, and deployment constraints.

That combination is much stronger than either one alone.
