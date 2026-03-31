# 🇩🇿 WaraqDz — AI Administrative Voice Assistant
 
WaraqDz is an AI-powered automation workflow built using n8n that transforms user requests about Algerian administrative procedures into:
* 🧠 AI-generated explanations (powered by RAG)
* 🎙️ Natural voice audio (MP3)
* ☁️ Cloud storage (Google Drive)
* 📧 Optional email delivery
 
## 🚀 Core Idea
 
User sends a simple request:
```
"Demande passeport biométrique"
```
 
System automatically:
1. **Retrieves relevant context** using RAG from your administrative knowledge base
2. **Understands the request** using AI with enriched context
3. **Generates structured explanation** based on retrieved documents
4. **Converts text into natural voice** using ElevenLabs
5. **Uploads audio to Google Drive** for easy access
 
---
 
## 🔍 How RAG Works in WaraqDz
 
### Retrieval-Augmented Generation (RAG)
RAG enhances your AI responses by combining:
 
- **Knowledge Base**: Documents containing Algerian administrative procedures, requirements, and forms
- **Vector Embeddings**: Converts documents into searchable vectors for semantic matching
- **Smart Retrieval**: When a user requests information, RAG retrieves the most relevant documents
- **Context-Aware Responses**: Claude uses retrieved context to generate accurate, grounded explanations
 
### RAG Workflow
```
User Request
    ↓
Vector Search (Find Relevant Documents)
    ↓
Retrieve Top Matching Documents
    ↓
Pass Context to Claude AI
    ↓
Generate Accurate Response
    ↓
Convert to Voice (ElevenLabs)
    ↓
Store in Google Drive
```
 
### Benefits of RAG
✅ **Accuracy**: Responses grounded in your actual administrative documents  
✅ **Consistency**: Always refers to current, up-to-date procedures  
✅ **Relevance**: Returns only relevant information for each request  
✅ **Transparency**: Users know responses come from verified sources  
 
---
 
## 🛠️ Tech Stack
 
| Component | Technology |
|-----------|-----------|
| Workflow Orchestration | n8n |
| AI & RAG | Anthropic Claude API |
| Vector Search | Pinecone / Weaviate / LangChain |
| Voice Synthesis | ElevenLabs API |
| Cloud Storage | Google Drive API |
| Knowledge Base | PDF/Document Management |
 
---
 
## 📋 Setup Requirements
 
### 1. n8n Instance
- Self-hosted or n8n Cloud
- Nodes configured for: HTTP, AI, Google Drive, ElevenLabs
 
### 2. Knowledge Base Setup (RAG)
- Collect Algerian administrative procedure documents
- Convert to vector embeddings using Anthropic's embeddings API
- Store in vector database (Pinecone, Weaviate, or Chroma)
 
### 3. API Keys
```
ANTHROPIC_API_KEY=your_key_here
ELEVENLABS_API_KEY=your_key_here
GOOGLE_DRIVE_API_KEY=your_key_here
VECTOR_DB_API_KEY=your_vector_db_key
```
 
### 4. Vector Database Configuration
Choose and configure one of:
- **Pinecone**: Cloud-hosted, managed indexes
- **Weaviate**: Self-hosted or cloud
- **Chroma**: Lightweight, local or server mode
- **Milvus**: Open-source vector database
 
---
 
## 📦 n8n Workflow Steps
 
1. **Trigger**: User submits request (Webhook/Form)
2. **RAG Retrieval**: Query vector database for relevant documents
3. **Prompt Engineering**: Build context-aware prompt with retrieved documents
4. **Claude AI**: Generate structured explanation with context
5. **Text Processing**: Clean and format response
6. **Voice Synthesis**: ElevenLabs converts text to MP3
7. **Google Drive Upload**: Store audio with metadata
8. **Email Notification**: Optional - send link to user
 
---
 
## 💡 Example Workflow
 
**User Request:**
```
"كيفية طلب جواز سفر بيومتري؟"
(How to apply for a biometric passport?)
```
 
**RAG Process:**
1. Vector search retrieves relevant documents about passport procedures
2. Returns top 3 matching documents with step-by-step requirements
 
**AI Generation:**
```
Claude generates:
- Required documents
- Step-by-step procedure
- Office locations & hours
- Cost & processing time
- Contact information
```
 
**Output:**
- MP3 audio file
- Uploaded to Google Drive
