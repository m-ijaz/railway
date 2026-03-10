
1SOURCE COMPONENTS
AI Sales Agent System
Full Process Document, Workflow Maps & Capability Specifications


Version 2.0  |  March 2026  |  Confidential
Prepared for internal use only — 1Source Components, Cary, NC
1. Executive Summary
1Source Components is deploying a fully integrated AI Agent system to automate the end-to-end sales process — from initial lead discovery through to closed orders, post-sale nurturing, and long-term re-engagement. This document describes each agent, its responsibilities, capabilities, workflow integrations, and how all agents connect together as one unified system.

The system consists of 9 specialized AI Agents working in sequence and in parallel, all connected to the EncuentraTI CRM (HighLevel platform) and communicating through a shared pipeline. Together they replace repetitive manual tasks performed by sales reps, allowing the 1Source team to focus on high-value relationships, negotiations, and closing deals.



2. System Architecture & Technology Stack
2.1 Infrastructure


2.2 CRM Pipeline Stages




Continuously searches for new potential customers — electronics manufacturers, EMS providers, OEMs, and procurement teams. Builds a pipeline of qualified leads before any human contact is made.
Capabilities
LinkedIn, Google, trade show lists, industry directories
Finds decision maker contact info (name, email, phone, LinkedIn)
Scores leads 1-10 by estimated volume and fit
Deduplicates against existing CRM contacts
Auto-creates contact + opportunity in CRM
Tags by industry: aerospace, medical, automotive, consumer electronics
Flags USA contacts with phone numbers for SMS/call campaigns
CRM Actions
Creates Contact + Opportunity at stage: New Lead (RFQ Submitted)
Assigns to sales rep (round-robin or by territory)
Triggers Agent 2 (Outreach) automatically



Handles all initial and follow-up communications with new leads. Crafts personalized messages, manages multi-touch sequences, and qualifies interest before handing off to a human sales rep. Operates bilingually in English and Spanish.
Outreach Sequence
Day 0 — Personalized intro email (EN or ES based on contact location)
Day 3 — Follow-up email with value proposition
Day 7 — LinkedIn connection request + message
Day 10 — AI voice call (USA numbers)
Day 14 — Final email with open-ended question
Day 21 — Move to long-term nurture
Capabilities
Personalized emails referencing company, industry, and pain points
Bilingual — EN for USA/Canada, ES for Latin America
Detects response and stops sequence — notifies sales rep immediately
AI voice call capability for USA numbers
SMS follow-up for USA mobile numbers
A/B tests subject lines and message formats automatically





Overview
The BOM Analyzer & Quoting Agent is the core revenue-generating agent. When a customer sends a Bill of Materials request via email, this agent automatically parses the parts list, sources pricing from multiple distributors, builds a professional quote with markup, and manages the complete internal review and customer communication workflow.
Step-by-Step Process







Overview
After a quote is sent, the Post-Quote Follow-Up Sequence takes over from the BOM Agent. It runs a timed multi-channel sequence — email, SMS, and AI voice calls — over 14 days. If the customer responds at any point, the sequence stops and the Response Interpreter Agent takes over to classify and route the reply. If there is no response after 14 days, the lead is escalated to the sales rep and enrolled in a 6-month nurture sequence.

Follow-Up Timeline


Message Templates — Day 1
Email (English)


Email (Spanish)


SMS (English — USA only)


Message Templates — Day 3
Email (English)


Email (Spanish)


Message Templates — Day 7
Email (English)


AI Voice Call Script (English — USA only)


Message Templates — Day 14 (Final)
Email (English)


Email (Spanish)






Overview
The Response Interpreter Agent is the intelligence layer between customer communication and CRM action. Every time a customer replies to any message — email, SMS, or AI call transcript — HighLevel fires a webhook to our backend. The agent reads the message, checks if the contact is in an active quote stage, classifies the intent using Claude AI, and automatically takes the right action. No human needed for routine responses.

How the Filter Works
The agent does NOT process every reply in the HighLevel account. It only activates for contacts whose opportunity is currently in one of these stages:



Intent Classification — 7 Categories


Technical Setup in HighLevel
To activate the Response Interpreter, set up this webhook in HighLevel:





Specializes in locating obsolete, end-of-life, allocated, and long lead-time components not available through standard channels — a core differentiator for 1Source.
Trigger
BOM Agent flags a part as Hard-to-Find or Not Found
Sales rep manually escalates a specific MPN
Extended Sources
ICS Source, BrokerForum, PartsBase, ILS — login-required portals
Sales Assistant (SA) — internal pricing history
Direct supplier outreach — automated emails to known suppliers
Manufacturer last-time-buy inquiries for EOL parts
Capabilities
Cross-references alternate MPNs and compatible substitutes
Verifies authenticity risk level for secondary market parts
Tracks vendor response times and reliability scores
Moves opportunity to Pending Vendor Response while awaiting replies



Handles all post-quote customer interactions — order confirmations, tracking updates, invoice questions, delivery issues. Operates 24/7 bilingually. Detects new BOM requests in replies and routes to Agent 3 automatically.
Capabilities
Reads full CRM conversation history before responding
Answers order status, tracking, and delivery questions
Detects frustrated language and immediately escalates to human rep
Detects new BOM requests and routes to BOM Agent automatically
Processes simple change requests — quantities, delivery address
Auto-detects customer language (EN/ES) from their message



Proactively manages existing customer relationships. Monitors buying patterns, identifies upsell opportunities, sends relationship touchpoints, and ensures customers return before they think to shop elsewhere.
Capabilities
Analyzes purchase history to predict next likely order
Sends proactive availability alerts for components in customer's product line
Generates personalized re-order reminders based on reorder intervals
Identifies customers who have gone quiet and triggers re-engagement
Flags VIP accounts for priority human attention
Cross-sells complementary components based on industry patterns



Monitors the entire pipeline, generates reports, identifies bottlenecks, and provides actionable insights to management. Runs on schedule and can be queried in plain English.
Automated Reports
Daily Pipeline Summary — new leads, quotes sent, deals closed, revenue
Weekly Performance Report — rep performance, conversion rates, average quote value
Monthly Revenue Report — closed won, lost, pipeline value, forecast
Quote Conversion Analysis — which parts, industries, or rep behaviors close deals
Real-Time Alerts
Large opportunity created (>$10,000) → Immediate manager notification
Deal stale 7+ days with no activity → Rep task created
Quote expiring in 3 days → Auto follow-up triggered
Multiple lost deals to same competitor → Manager alert

10. Master Process Flow — End-to-End
Complete customer journey from first contact through closed order and long-term nurture, showing which agent handles each step.



11. Implementation Roadmap




