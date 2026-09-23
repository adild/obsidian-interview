Phase 1: Python fundaments and web apis (2-3 weeks)
	Python - type hints, databases, async/await, context managers
	FastAPI - rest points, pydantic models, dependency injection, middleware, lifespan event
	Unicorn - ASGI server, running and configuring
Goal - build CRUD api with project layering

Phase 2- Databases & Caching (1-2 weeks)
	MongoDB + PyMongo document modeling, CRUD, aggregation pipelines
	SQL databases (OracleDB/PostgreSQL) - basic relational queries via oracledb or SQLAlchemy
	Redis - caching patterns, TTLs, async access with redis-py

Phase 3- Background Jobs & Scheduling (1 week)
	APScheduler-interval/cron jobs, scheduler lifecycle management
	Asyncio patterns - event loops, background tasks in FastAPI, asyncio.create_task
"Goal: Add a scheduler that polls an external source periodically."

Phase 4-LLMs & Al Foundations (2-3 weeks)
	OpenAI API-chat completions, function calling, prompt engineering
	LangChain-chains, tools, output parsers, chat models
	LangChain-OpenAI- ChatOpenAI, structured output, tool binding
	Tiktoken-token counting, context window management
"Goal: Build a standalone LLM-powered classifier that categorizes documents by type"

Phase 5-Agentic Workflows (3-4 weeks)Core
	LangGraph-state graphs, nodes, edges, conditional routing, checkpointing, thread management
	CrewAl-agents, tasks, crews, delegation, multi-agent orchestration
	Agent design patterns - tool-calling agents, ReAct, plan-and-execute, human-in-the-loop
	State management-passing context between nodes, error handling, retry logic
"Goal: Build a multi-step workflow that ingests → classifies → extracts → outputs, using LangGraph."

Phase 6-Document Processing & IDP (2 weeks)
	PDF extraction pdfplumber, reportlab for PDF generation
	OCR-integrating OCR services for scanned documents
	Data extraction patterns - annotation processing, attribute mapping, structured output from unstructured docs
	Excel handling- openpyxl for reading/writing spreadsheets
"Goal: Extract structured fields from PDF/email attachments using LLM + PDF tools."

Phase 7-Integrations & Channels (2 weeks)
	Email processing-parsing.eml /MIME, extracting body + attachments
	JIRA API-REST client, OAuth authentication, issue/comment management
	WebSockets-real-time progress updates (ws/connection_manager)
	HTTP clients- httpx/requests, MTLS with.p12 certificates (requests-pkcs12).
	Kerberos auth - enterprise authentication (winkerberos/kerberos)
"Goal: Ingest documents from email and JIRA, push progress via WebSocket"