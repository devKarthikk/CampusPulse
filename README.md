Project Name :
CampusPulse AI

Problem Statement:

Modern higher education institutions require students to navigate a web of disconnected platforms and physical service counters for course registration,
administrative grievances, hostel facilities, mental health support, and career placement, each operating in isolation. 
This fragmentation creates administrative friction, increases academic anxiety, and leaves critical student needs unmet at the moments when timely institutional support could make the greatest difference.


Explain clearly what problem your project is solving:

Students often struggle with fragmented campus services spread across multiple platforms. Academic support, career guidance, scholarship information,
campus events, hostel management, document storage, and wellness resources are typically available through separate systems,
making it difficult to access information quickly and efficiently. This lack of integration reduces productivity, causes students to miss important opportunities,
and limits access to personalized support. Additionally, many students lack instant academic assistance and proactive wellness guidance to help them balance their studies and personal well-being.

Campus Pulse AI solves this problem by bringing all essential campus services into a single intelligent platform powered by Google Gemma 4.
The platform provides personalized academic assistance, career and scholarship guidance, campus information, secure document management, 
event updates, and AI-generated wellness reports, enabling students to access everything they need through one seamless, AI-driven experience.


Project Description:

Campus Pulse AI is a mobile-first AI-powered digital companion designed exclusively for college students.
It centralizes everything a student needs — academics, hostel life, career planning, scholarships,
and campus services — into a single intelligent app, replacing the chaos of scattered portals, WhatsApp groups, and paper notices.


Describe your solution, how it works, and what makes it useful:

The app is built as a full-stack web application:

Frontend — A React + Vite progressive web app with a clean mobile-first UI (shadcn/ui + Tailwind). Students access it from any device, no installation needed.
Backend — An Express.js API server with a PostgreSQL database (Drizzle ORM) managing all student data: events, scholarships, hostel info, documents, notifications, and chat history.
AI Layer — Powered by Groq (Llama 3.3 70B), the AI assistant maintains full conversation history per session and is specialized across 8 domains: academics, programming, data engineering, career guidance, scholarships, campus services, productivity, and motivational support.
Academic Wellness Engine — Analyzes attendance, upcoming exams, assignment deadlines, CGPA, and semester progress, then generates a personalized AI wellness report with a 7-day study plan, risk factors, and recommendations.

Google AI Usage:
Campus Pulse AI uses Google Gemma 4 as its core intelligence layer. 
Gemma 4 is integrated directly into the backend and powers two major features of the application — the real-time AI Chat Assistant and the Academic Wellness Analysis engine.

The model is accessed via the Google AI SDK (@google/genai) using a GOOGLE_API_KEY stored securely as an environment secret. No AI processing happens on the frontend — all calls to Gemma 4 are made server-side through a single centralized AI service.


Tools / Models Used:

AI Model -	Google Gemma 4 
AI SDK -	@google/genai (Google AI JavaScript SDK)
API Key -	GOOGLE_API_KEY (stored as Replit Secret)
AI Features	- Multi-turn Chat, Structured Wellness Analysis

Tech Stack used:

React 18	- UI framework
Vite	- Build tool and dev server
Wouter	- Client-side routing
TanStack Query (React Query) -	Server state, caching, API calls
shadcn/ui	- Component library (Radix UI primitives)
Tailwind CSS -	Styling
Lucide React -	Icons

Node.js + Express 5	API server
TypeScript	Type safety across the full stack
Drizzle ORM	Type-safe database queries
PostgreSQL	Primary database (Replit managed)
Zod	Request/response validation
Pino	Structured logging

AI

Google Gemma 4	Language model for chat and analysis
@google/genai SDK	Client to call the Gemma 4 API
System Prompt	Defines AI identity, student context, response format


Monorepo & Tooling

Tool	Purpose
pnpm workspaces	Monorepo package management
esbuild	Fast API server bundler
OpenAPI + Orval	Auto-generated API types and React Query hooks
Replit	Hosting, secrets management, PostgreSQL database


How Google AI Was Used

AI Chat Assistant
The chat feature uses Gemma 4 in multi-turn conversational mode. Every time a student sends a message:

The backend retrieves the complete conversation history from PostgreSQL (up to 40 messages)
It prepends a detailed System Prompt that gives Gemma 4 the student's identity, profile links, specializations, and formatting rules
The full message array is sent to Gemma 4 in a single API call
Gemma 4 returns a context-aware, Markdown-formatted response
The response is saved back to the database and returned to the frontend
This means Gemma 4 remembers the entire session — it can refer back to earlier messages, build on prior answers, and never loses context within a conversation.

Gemma 4 is specialized across 8 academic domains:

 1. Academics & Exam Prep
 Programming & Computer Science
 Data Engineering & AI/ML
 Career Guidance & Interview Prep
 Scholarships & Financial Aid
 Campus Services (Hostel, Events)
 Study Planning & Productivity
 Motivational Support
 
2. Academic Wellness Analysis
   
The Wellness page collects the student's academic data (attendance per subject, upcoming exams, assignment deadlines, CGPA, semester progress) and sends it all to Gemma 4 as a richly structured one-shot prompt.

Gemma 4 analyses this data and generates a complete Academic Wellness Report containing:

Overall Wellness Score (out of 100) with rationale
Stress Level (Low / Moderate / High)
Key Risk Factors (specific subjects, deadlines)
5–7 Actionable Recommendations
Today's Priorities & Tomorrow's Deadlines
Personalised 7-Day Study Plan (day-by-day, with time blocks)
Time Management Tips
Motivational Message

<img width="1181" height="746" alt="Screenshot 2026-07-18 070140" src="https://github.com/user-attachments/assets/a80959e7-808c-4a6f-b2cd-cea0272969f2" />

