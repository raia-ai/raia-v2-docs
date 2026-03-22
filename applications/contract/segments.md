# Segments

Underpinning the entire document review process in RAIA Contract is the concept of **segments**. A segment is a logical division of your document, such as a paragraph, a clause, or even a single line item. When you upload a contract, the platform doesn't just store it as a single block of text; it intelligently parses it into a structured collection of these segments. This segmentation is the key to the platform's granular review and redlining capabilities.

### Why Segments are Important

The segmentation of documents serves several critical purposes:

* **Granular Analysis**: By breaking the document down, the AI Agent can analyze it piece by piece. This allows for a more focused and accurate review, as the agent can assess the context and implications of each individual clause or paragraph.
* **Precise Redlining**: Changes are suggested at the segment level. This means that when the AI suggests a revision, it is applied to a specific, identifiable part of the document, rather than making ambiguous changes to a large block of text.
* **Efficient Review**: For the user, segmentation makes the review process much more manageable. Instead of having to read through the entire document to find changes, you can navigate from one changed segment to the next, focusing your attention only where it is needed.
* **Side-by-Side Comparison**: The side-by-side review interface is built upon segments. The platform aligns the original and redlined segments, making it possible to directly compare the before and after versions of each specific part of the contract.

### How Segmentation Works

When you upload a document, RAIA Contract's document parser analyzes its structure. It identifies natural breaks in the text, such as paragraphs, headings, and list items, and converts each of these into a distinct segment. This collection of segments is then stored as a JSON object in the `user_documents` table, preserving the document's structure in a way that the platform can easily work with.

Each segment typically contains:

* The original text of that segment.
* A unique identifier.
* Metadata about its position and type.

When the AI Agent processes the document, it receives these segments, analyzes them, and returns a revised set of segments containing the tracked changes. The platform then uses this data to render the redlined view.

### The User Experience

As a user, you don't need to manually manage segments. The process is entirely automated. However, understanding that the platform operates on a segment-based model helps to clarify why the review process is so structured and precise. When you click to accept or reject a change, you are acting on a specific segment, and the platform updates that individual piece of the document accordingly.

In essence, segments are the atomic units of contract review in RAIA Contract. They transform a monolithic legal document into a structured, manageable, and editable dataset, enabling the intelligent and granular review process that defines the platform. The next article will discuss **Versions**, which builds upon this segmented structure to provide a complete history of your document's evolution.
