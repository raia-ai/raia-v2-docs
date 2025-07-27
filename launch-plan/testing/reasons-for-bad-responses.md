# Reasons for Bad Responses

When testing AI Agents they can provide bad, incomplete or vague answers to questions during testing. The following outlines the various reasons the AI Agent may not be answering correctly (or meet your requirements/expectations).&#x20;

***

#### 1. **Wrong Model Selection**

Choosing the incorrect model can significantly affect performance. Different models have different capabilities in terms of reasoning, knowledge, and cost.

**Issues:**

* **Incompatible model** (e.g., using `gpt-3.5-turbo` when `gpt-4` is required for complex reasoning).
* **No tool support** (e.g., needing code execution or search features but using a base model without those tools).
* **Outdated context** due to a model with an older knowledge cutoff.

**Solutions:**

* Ensure you select the model that matches the complexity of the tasks.
* Use `gpt-4o` for most advanced multimodal and multilingual needs.
* Enable tools like Code Interpreter or Retrieval if applicable.

***

#### 2. **Poorly Formatted Training Documents**

How data is ingested via the file search or knowledge retrieval system affects understanding.

**Issues:**

* Long unstructured blocks of text.
* Lack of headings, metadata, or semantically clear sections.
* Content embedded in images or non-searchable formats (e.g., scanned PDFs).

**Solutions:**

* Use well-structured documents with headings, bullet points, and tables.
* Convert image-based content to text using OCR.
* Index documents using clear semantic sections (e.g., FAQ style, topic tags).

***

#### 3. **Missing Information in Training Documents**

Even perfectly formatted documents are useless if the key content isn't there.

**Issues:**

* Core facts, edge cases, or updated procedures not represented.
* Only partial knowledge captured (e.g., one department’s workflow but not another’s).
* Outdated documents with obsolete information.

**Solutions:**

* Keep document corpus current and complete.
* Ingest a wide variety of content (e.g., emails, SOPs, chat transcripts, dashboards).
* Establish regular update cycles for high-value documents.

***

#### 4. **Weak or Misleading Instructional Prompt**

System instructions or user messages guide behavior, so poorly written ones reduce accuracy.

**Issues:**

* Vague or overly broad system instructions (e.g., “Act like a helpful assistant”).
* Conflicting instructions (“Be brief” vs “Include detail”).
* No role definition, persona, or tone guidance.

**Solutions:**

* Use rich system prompts (e.g., “You are a compliance advisor specializing in HIPAA…”).
* Be clear about tone, scope, and priorities.
* Use user messages with specific context when possible (“Summarize this for a C-level exec”).

***

#### 5. **Poorly Designed Tools or Retrieval Config**

When using `retrieval` with the Assistants API, the chunking and embedding setup heavily influences success.

**Issues:**

* Chunk size too large or too small.
* No semantic overlap between chunks.
* Weak embeddings leading to irrelevant results.

**Solutions:**

* Tune chunk sizes (typically 300–800 tokens).
* Use semantic chunking instead of just token counts (e.g., by section or heading).
* Choose high-quality embedding models (like `text-embedding-3-large`).

***

#### 6. **Insufficient Message History or Context**

The Assistant may miss key context if the conversation is short or key facts are not repeated.

**Issues:**

* Relying too much on memory that isn't preserved across calls.
* Missing in-conversation context (e.g., follow-up questions with no reference).

**Solutions:**

* Pass relevant prior messages into the thread when needed.
* Use persistent threads and retrieve previous context explicitly.

***

#### 7. **Inaccurate or Non-Representative User Inputs**

Sometimes the Assistant isn’t at fault—users can give misleading or poorly phrased prompts.

**Issues:**

* Ambiguous questions ("What’s the status?" without topic).
* Typos or incorrect terminology.
* Overloaded prompts with too many asks.

**Solutions:**

* Design interfaces that guide user input (e.g., dropdowns, autocomplete).
* Preprocess user prompts to clarify intent if possible.
* Add follow-up questions for disambiguation.

***

#### 8. **Latency or Incomplete API Responses**

In edge cases, latency or timeouts may truncate responses or fail to return relevant completions.

**Issues:**

* Token limits exceeded silently.
* Timeout on a long query, especially with large file retrieval.

**Solutions:**

* Monitor logs for errors or truncation.
* Use streaming responses or pagination where needed.

***

#### 9. **Security/Privacy Filtering**

If sensitive content is blocked, the Assistant may omit useful info or produce vague answers.

**Issues:**

* Guardrails may filter outputs for safety or compliance.
* Some content may be inaccessible for safety reasons.

**Solutions:**

* Review content filtering thresholds in enterprise settings.
* Use system prompts to clarify when restricted content is expected.

***

#### 10. **Limitations in Reasoning or Creativity**

Even the best models have reasoning limitations, especially under ambiguity or when data requires synthesis.

**Issues:**

* Fails to connect multi-hop logic steps.
* Lacks domain-specific nuance unless explicitly trained.

**Solutions:**

* Use tool-assisted models (e.g., function calling or code interpreter).
* Provide few-shot examples in instructions or user message.&#x20;
