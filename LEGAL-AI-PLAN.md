# LEGAL-AI-PLAN.md - Indian Legal AI Assistant

*Plan to build AI assistant trained on Indian laws for lawyers.*

---

## Project Overview

**Problem:** Lawyers spend 30-50% of their time on legal research, document drafting, and compliance checks. They pay ~₹5,000/day but waste hours on repetitive tasks.

**Solution:** AI assistant trained on Indian law that can:
- Instantly look up relevant statutes and case law
- Draft documents and contracts
- Analyze legal compliance issues
- Answer routine legal questions
- Reduce research time from hours to minutes

**Target Market:** Indian lawyers, law firms, legal departments

**Revenue Model:** B2B SaaS
- Free tier: Basic queries (limits apply)
- Pro tier: Unlimited queries + document generation + ₹2,000-5,000/month
- Enterprise: Custom training + dedicated API access

**Price Points:**
- Lawyers already pay ₹5,000/day = ~₹1,00,000/month
- Saving 2 hours/day = ₹60,000/month saved
- AI subscription at ₹3,000/month = tiny fraction of their revenue
- **Clear ROI** for them

---

## Technical Architecture

### Option 1: RAG with Vector Database (Recommended for MVP)

**Stack:**
- Vector database: Pinecone, Weaviate, or Qdrant
- Embeddings: OpenAI text-embedding-3-small or HuggingFace models
- LLM API: OpenAI GPT-4 or Anthropic Claude (for quality)
- Frontend: Node.js/Next.js + AI assistant UI

**How It Works:**
1. Upload legal documents (Bare Act, IPC, Constitution, etc.) to vector DB
2. When lawyer queries, search relevant documents
3. Send query + retrieved docs to LLM
4. Return answer with legal citations

**Pros:**
- ✅ No training required (use pre-trained models)
- ✅ Easy to update (just upload new documents)
- ✅ Fast to build (can launch in 2-4 weeks)
- ✅ Lower cost (no GPU, pay per query)

**Cons:**
- ❌ Ongoing API costs (pay per query)
- ❌ Limited by model capabilities
- ❌ No model ownership

**Timeline:** 2-4 weeks to MVP

### Option 2: Fine-Tuned Open Source Model

**Stack:**
- Model: Llama 3.1 8B or Mistral 7B (open source)
- Training: LoRA fine-tuning on legal corpus
- Inference: vLLM, Ollama, or API service
- Frontend: Node.js/Next.js + AI assistant UI

**How It Works:**
1. Collect Indian legal texts (acts, codes, case law)
2. Fine-tune LLM on legal data (1-3 days on GPU)
3. Deploy model for inference (can self-host or use API)
4. Lawyers query the fine-tuned model
5. Answers are based on Indian law specifically

**Pros:**
- ✅ Model ownership (can't be shut down)
- ✅ No ongoing API costs
- ✅ Can improve model over time
- ✅ Legal domain expertise
- ✅ One-time training cost

**Cons:**
- ❌ Requires GPU/Cloud (expensive for training)
- ❌ Complex setup (MLOps, deployment)
- ❌ Longer time to first version (4-8 weeks)
- ❌ Model may hallucinate more than GPT/Claude

**Timeline:** 4-8 weeks to first version

---

## Data Collection Strategy

### Where to Get Indian Legal Data

**Option 1: Government Sources (Free/Public)**
1. **India Code** - Primary source of Indian law
   - URL: https://indiacode.nic.in/
   - Contains: IPC, CrPC, Evidence Act, Contract Act, Property laws
   - Format: Text/PDF, free to access
   - Coverage: Most major areas of law

2. **National Legal Services Authority** - Land records, court procedures
   - URL: https://nalsa.gov.in/
   - Land laws, registration procedures

3. **Ministry of Law & Justice** - Acts, bills, notifications
   - URL: https://legislative.gov.in/
   - Recent amendments, new legislation

4. **Supreme Court & High Courts** - Case law database
   - URL: https://main.sci.gov.in/
   - Judgments, orders, cause lists

**Option 2: Legal Databases (Paid)**
1. **Manupatra** - Comprehensive Indian case law database
   - Paid subscription (~₹25,000/month)
   - Huge database of judgments
   - High quality, well-structured

2. **Westlaw India / SCC Online** - Premium legal research
   - Paid subscription (expensive but comprehensive)

3. **LexisNexis India** - Corporate legal database
   - Paid subscription (focus on corporate/commercial law)

**Option 3: Scraping (For Specific Acts)**
- Web scraping of India Code, Bare Act
- PDF extraction and parsing
- Convert to training data format
- **Legal gray area** - check terms of use

---

## Data Sources Priority (MVP)

### Phase 1: Start with One Legal Domain (Weeks 1-2)
**Recommended:** **Property Law / Land Revenue Law**
**Why:**
- Directly relevant to property valuation app (complementary)
- Smaller corpus than general law
- Your lawyer friends may specialize here
- Clear ROI for property lawyers

**Data to Collect:**
1. **Maharashtra Land Revenue Code** - EASR, ceiling rates
   - Already scraping EASR (government land rates)
   - Add: Land Revenue Act, ceiling calculations, exemptions
2. **Registration Act** - Property registration procedures
3. **Transfer of Property Act** - Title transfer laws
4. **Rent Control Act** - Rental regulations

**Estimated Data Size:** ~500-1000 legal documents

### Phase 2: Expand to Civil/Criminal Law (Weeks 3-6)
**Domains:**
1. **Indian Penal Code (IPC)** - Criminal offenses
2. **Code of Civil Procedure (CPC)** - Court procedures
3. **Indian Evidence Act** - Evidence rules
4. **Limitation Act** - Time limits for filing cases

**Estimated Data Size:** ~2000-5000 documents

### Phase 3: Specialized Laws (Weeks 7-12)
**Domains:**
1. **Contract Act** - Business contracts
2. **Companies Act** - Corporate law
3. **Labor Laws** - Employment issues
4. **Intellectual Property** - Patents, trademarks, copyrights

---

## Implementation Plan

### Option 1: RAG MVP (Recommended - Fast to Market)

#### Week 1-2: Setup & Data Collection
**Tasks:**
1. [ ] Choose vector database (Pinecone vs Qdrant vs local)
2. [ ] Set up OpenAI/Anthropic API account
3. [ ] Download/extract India Code sections (start with property law)
4. [ ] Parse and clean legal text
5. [ ] Create embeddings for documents
6. [ ] Store in vector database with metadata (act, section, keywords)
7. [ ] Build simple UI for uploading docs and querying

**Deliverable:** Working RAG system on property law

#### Week 3-4: MVP Development
**Tasks:**
1. [ ] Build retrieval system (search vector DB)
2. [ ] Integrate LLM API (GPT-4 or Claude)
3. [ ] Create prompt templates for legal queries
4. [ ] Build web interface (lawyer can type question → get answer)
5. [ ] Test with your lawyer friends (get feedback)
6. [ ] Add citation system (reference specific sections)
7. [ ] Implement rate limiting and user authentication

**Deliverable:** Web app lawyers can use for legal research

#### Week 5-6: Testing & Launch
**Tasks:**
1. [ ] Beta test with 5-10 lawyers
2. [ ] Collect feedback and iterate
3. [ ] Create pricing page (Free/Pro/Enterprise)
4. [ ] Create user authentication system
5. [ ] Set up Stripe/Razorpay for payments
6. [ ] Write documentation (user guide, API docs)
7. [ ] Launch to public

**Deliverable:** Live SaaS product

### Option 2: Fine-Tuned Model (Longer, More Complex)

#### Week 1-4: Data Collection & Preparation
**Tasks:**
1. [ ] Scrape India Code for target legal domain
2. [ ] Collect supplementary legal documents
3. [ ] Clean and format text for training
4. [ ] Create training dataset (query-answer pairs)
5. [ ] Choose base model (Llama 3.1 vs Mistral 7B)
6. [ ] Set up GPU access (Google Colab, AWS, or local GPU)
7. [ ] Prepare training scripts (using QLoRA or Axolotl)

#### Week 5-6: Fine-Tuning
**Tasks:**
1. [ ] Train model on legal corpus (24-72 hours depending on data)
2. [ ] Evaluate model performance (accuracy, hallucination rate)
3. [ ] Optimize model (quantization, distillation)
4. [ ] Convert to inference format
5. [ ] Test on legal queries

#### Week 7-8: Deployment & App
**Tasks:**
1. [ ] Set up inference server (Ollama or API)
2. [ ] Build AI assistant interface
3. [ ] Implement RAG (search + generate)
4. [ ] Add document upload for custom cases
5. [ ] Create user system (accounts, billing)
6. [ ] Performance testing and optimization
7. [ ] Deploy to production

**Deliverable:** Full legal AI product

---

## Where We'll Get Stuck (Potential Blockers)

### Data Collection Issues
**Problem:** India Code and other legal sources may have:
- Paywalls for advanced features
- No bulk download API
- Copyright restrictions on redistribution
- Complex legal text formatting (Marathi + English)

**Workarounds:**
- Manual data entry for key documents
- Use unofficial aggregators (if available)
- Start with government sources (no copyright issues)

### Training Challenges
**Problem:** Fine-tuning requires significant compute
- GPU access needed (we don't have dedicated GPU)
- Training Llama 3.1 on 50K+ documents requires ~$100-500 cloud credits
- Ongoing cost for inference (need GPU or pay API)

**Solutions:**
1. **Use RAG approach first** (Option 1) - No training needed
2. **Rent GPU** - AWS p3.2xlarge, Lambda Labs, or other cloud GPU
3. **Use free GPU** - Google Colab, Hugging Face Spaces (limited)
4. **Use inference API** - Replicate, Fireworks, or Together AI (pay per call)
5. **Local inference** - Run Ollama on CPU (slow but free)

### Model Selection
**Options:**
1. **Llama 3.1 8B** - Latest, strong open source
2. **Mistral 7B** - Excellent performance, good for legal text
3. **GPT-4/Claude** - Best quality, pay per API
4. **Sanskrit-based models** - Some Indian legal AI experiments

**Recommendation:**
- Start with GPT-4/Claude + RAG (Option 1)
- Fine-tune once validated (Option 2)

---

## Infrastructure Requirements

### For Option 1: RAG MVP

| Component | Choice | Monthly Cost |
|-----------|---------|---------------|
| Vector DB | Pinecone (recommended) | $70 (0-5M vectors) |
| | Qdrant (self-hosted) | Free + server cost (~$20/mo) |
| | Weaviate Cloud | $110 |
| LLM API | OpenAI GPT-4 | $20-200 (based on usage) |
| | Anthropic Claude | $20-150 (based on usage) |
| Frontend | Vercel (Next.js) | Free (pro plan $20) |
| Auth | Clerk or Supabase Auth | Free |
| Database | Supabase Postgres | Free (pro plan $25) |
| Payments | Stripe | 2.9% of revenue |

**Est. Monthly Cost:** $150-600/month for early stage

### For Option 2: Fine-Tuned Model

| Component | Choice | Cost |
|-----------|---------|--------|
| GPU Training | Google Colab (free, limited) | $0 (but slow) |
| | AWS p3.2xlarge | $400/24hr for 3 days = $3,600 |
| | Lambda Labs | Custom pricing |
| Inference | Ollama on CPU (free) | $0 (but slow) |
| | Fireworks API | $0.30/mo per 1M tokens |
| | Replicate | $0.25/mo per 1M tokens |
| Frontend | Vercel | Free or $20 |
| Vector DB | Qdrant self-hosted | $20 (server) |

**Est. Monthly Cost:** $0-3,600/month (depends on training method)

---

## Technical Requirements

### What We Have
- ✅ Node.js v24.13.0
- ✅ Bun v1.3.8
- ✅ Playwright installed (for web scraping)
- ✅ Sudo access (can install packages)
- ✅ Workspace data storage
- ✅ Basic web development capability

### What We Need
1. **Vector Database Access** - Pinecone account or self-host Qdrant
2. **LLM API Access** - OpenAI or Anthropic API key
3. **GPU Access** - For fine-tuning (or use cloud services)
4. **Legal Text Corpus** - Downloaded from India Code
5. **Web Hosting** - Vercel, Netlify, or similar
6. **Payment Gateway** - Stripe or Razorpay (for Indian market)

---

## Success Metrics

### MVP Launch (Option 1)
- [ ] 100+ legal documents in vector database
- [ ] 10 beta testers (lawyers) using system
- [ ] 80%+ queries answered correctly
- [ ] Average response time < 10 seconds
- [ ] 50+ paying customers (Free + Pro tiers)

### First Revenue Milestone
- [ ] ₹1,00,000/month ($1,200/mo)
- **Path:** 50 lawyers on Pro tier (₹2,000 each) + free tier users

### Full Product (Option 2)
- [ ] Fine-tuned model on Indian law
- [ ] 200+ legal domains covered
- [ ] 500+ paying customers
- [ ] ₹5,00,000/month ($6,000/mo)

---

## Immediate Next Steps

### For Rocky (Week 1)

**Data Collection:**
1. Visit India Code (https://indiacode.nic.in/)
2. Download Maharashtra Land Revenue Code PDFs
3. Download Registration Act, Property Transfer Act
4. Save to `/home/nisheeth/.openclaw/workspace/data/legal/`
5. Tell me what's accessible (PDF download? Scraping needed?)

**Decision Required:**
1. Which option: RAG MVP (fast) or Fine-Tuned Model (better but slower)?
2. Budget for infrastructure ($0-600/month acceptable?)
3. Target launch date (2 weeks from now? 4 weeks?)
4. Priority property law or broader legal corpus?

### For Lisa (Ready to Start)

**Week 1 Tasks:**
1. [ ] Create data pipeline for legal text extraction
2. [ ] Set up vector database (Pinecone or Qdrant)
3. [ ] Build RAG retrieval system
4. [ ] Create AI assistant UI (Next.js + shadcn/ui)
5. [ ] Integrate OpenAI/Anthropic API
6. [ ] Create prompt templates for legal queries
7. [ ] Test system with sample legal queries
8. [ ] Document system for deployment

---

## Competitive Analysis

### Existing Solutions
- **Harvey.ai** - US law focused, subscription expensive
- **Casetext** - Indian case law, but limited features
- **Manupatra** - Database but no AI assistant
- **LawRato** - Early stage, limited to criminal law

### Our Advantage
- **India-first** - Focused on Indian law (English + Marathi)
- **Property law expertise** - Leverages property valuation app
- **Multiple access points** - Web app + API + potential mobile
- **Bilingual support** - Can handle English and Marathi legal text
- **Competitive pricing** - Indian market pricing (lower than US products)
- **Local validation** - Your lawyer friends can test and validate

---

## Questions for Rocky

1. **Data Access:** Can you access India Code and download legal PDFs? Or should we plan to scrape?
2. **Infrastructure Budget:** What's acceptable monthly cost for MVP ($0-600/mo)?
3. **Launch Timeline:** When do you want this launched (2-4 weeks for MVP)?
4. **Legal Domain:** Start with property law only or broader corpus?
5. **Beta Testers:** Are your lawyer friends willing to test early?

---

## Status

**Created:** 2026-02-01 06:30 UTC
**Status:** Planning complete, ready for execution
**Next:** User decision on approach, then start development
**Estimated Time to MVP:** 2-4 weeks after decision

---

*This is a high-value B2B SaaS opportunity with clear ROI for lawyers.*
*Your lawyer friends pay ~₹1,00,000/month - saving them 20+ hours per month is worth ₹5,000+/mo subscription.*
