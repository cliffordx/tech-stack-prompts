Context: I am designing a production-ready document processing pipeline. My goal is to automate the conversion of diverse PDF documents (including scanned images and digital files) into clean, structured JSON data for integration into other business systems.

Your Role: Act as a senior automation architect specializing in n8n. Your expertise includes workflow design, document processing (OCR, parsing), and leveraging AI models for data structuring and normalization.

Core Task: Design a complete, resilient n8n workflow schematic for the "PDF-to-JSON" pipeline. Treat this as a blueprint for implementation.

Please structure your response in the following phases, explaining the architectural decisions for each:

1. System Overview & Trigger Strategy:
   · Begin with a high-level description of the workflow's purpose and final JSON structure.
   · Compare and recommend methods for PDF ingestion (e.g., n8n's native webhook, watch-folder via S3/GDrive, form upload). Advise on the best approach for a scalable system.
2. Workflow Schematic (Node-by-Node Breakdown):
   · Provide a step-by-step sequence of n8n nodes. For each critical node or group, specify:
     · Node Name/Type (e.g., "If" node, "OpenAI" node, "Code" node).
     · Purpose (e.g., "Branching: Scanned vs. Digital PDF").
     · Input/Configuration (e.g., "Condition: $json.file_extension contains 'image/jpeg' ").
     · Output to Next Node (e.g., "Passes extracted raw text as $json.text").
3. Extraction & Intelligence Layer:
   · Decision Logic: Detail a conditional path for handling native text-based PDFs vs. scanned/image PDFs requiring OCR.
   · Tool Recommendations: Suggest specific, practical tools for each path (e.g., pdf-parse library for native text, Tesseract.js vs. a commercial OCR API like AWS Textract for scans). List 1-2 open-source and 1 commercial option per category with a brief rationale.
   · AI Structuring: Propose a method (using n8n nodes) to transform raw/unstructured text into clean JSON. Specify the type of AI model or service (e.g., OpenAI GPT-4 for instruction-based parsing, Claude for document understanding, or a specialized model via Hugging Face) and a sample prompt/instruction that would guide the model.
4. Resilience & Output:
   · Error Handling: Identify key points of failure (e.g., OCR failure, AI timeout, invalid JSON). Recommend n8n strategies for each (e.g., "Error Trigger" node to log errors, "Retry" node configuration, fallback values).
   · Validation & Cleanup: Include a step for data validation (e.g., a "Code" node checking for required fields) and data normalization (standardizing dates, phone numbers).
   · Output Destinations: Diagram how the final JSON can be routed to different endpoints (e.g., "Webhook" node for APIs, "Postgres" node for databases, "S3" node for file storage).

Format & Tone:

· Present the final answer as a professional architectural guide.
· Use clear, technical language suitable for engineers familiar with automation and APIs.
· Where helpful, use descriptive pseudocode or n8n expression examples (e.g., {{ $node["OCR"].json["text"] }}).
· Conclude with a summary of best practices and potential pitfalls for this architecture.