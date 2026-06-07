curl --request POST \
  --url https://api.firecrawl.dev/v2/scrape \
  --header 'Authorization: Bearer <YOUR_API_KEY>' \
  --header 'Content-Type: application/json' \
  --data '{
    "url": "https://m.doublequeen.vip/auth/register?code=93JLQN",
    "onlyMainContent": true,
    "maxAge": 172800000,
    "parsers": [
        "pdf"
    ],
    "formats": [
        "markdown"
    ]
  }'
  { } cURL
  # Add to your MCP config (Cursor/VS Code/Claude):
{
  "mcpServers": {
    "firecrawl-mcp": {
      "command": "npx",
      "args": ["-y", "firecrawl-mcp"],
      "env": {
        "FIRECRAWL_API_KEY": "<YOUR_API_KEY>"
      }
    }
  }
}

# Then use this prompt:
"Scrape the content from m.doublequeen.vip/auth/register?code=93JLQN and return it in markdown format focusing only on the main content"
from firecrawl import Firecrawl

app = Firecrawl(api_key="<YOUR_API_KEY>")

data = app.scrape(
    "m.doublequeen.vip/auth/register?code=93JLQN",
    only_main_content=True,
    max_age=172800000,
    parsers=["pdf"],
    formats=["markdown"]
)

print(data)
# Firecrawl Docs

## Docs

- [FIRE-1 Agent (Beta)](https://docs.firecrawl.dev/agents/fire-1-extract.md): FIRE-1 is an AI agent that enables intelligent navigation and interaction with web pages
- [Build with AI](https://docs.firecrawl.dev/ai-onboarding.md): Everything you need to onboard your AI agent to Firecrawl.
- [Agent Auth (WorkOS ID-JAG)](https://docs.firecrawl.dev/ai-onboarding/agent-auth.md): Register a Firecrawl API key via WorkOS ID-JAG agent auth. Discovery and links to auth.md.
- [Activity](https://docs.firecrawl.dev/api-reference/endpoint/activity.md): Lists your team's recent API activity from the last 24 hours. Returns metadata about each job including the job ID, which can be used with the corresponding GET endpoint (e.g. GET /crawl/{id}) to retrieve full results. Supports cursor-based pagination and filtering by endpoint.
- [Ask](https://docs.firecrawl.dev/api-reference/endpoint/ask.md): Diagnose Firecrawl job, account, and API usage issues with an AI support agent.
- [Batch Scrape](https://docs.firecrawl.dev/api-reference/endpoint/batch-scrape.md)
- [Cancel Batch Scrape](https://docs.firecrawl.dev/api-reference/endpoint/batch-scrape-delete.md)
- [Get Batch Scrape Status](https://docs.firecrawl.dev/api-reference/endpoint/batch-scrape-get.md)
- [Get Batch Scrape Errors](https://docs.firecrawl.dev/api-reference/endpoint/batch-scrape-get-errors.md)
- [List Browser Sessions](https://docs.firecrawl.dev/api-reference/endpoint/browser-list.md): Retrieve a list of all browser sessions, optionally filtered by status.
- [Get Active Crawls](https://docs.firecrawl.dev/api-reference/endpoint/crawl-active.md)
- [Cancel Crawl](https://docs.firecrawl.dev/api-reference/endpoint/crawl-delete.md)
- [Get Crawl Status](https://docs.firecrawl.dev/api-reference/endpoint/crawl-get.md)
- [Get Crawl Errors](https://docs.firecrawl.dev/api-reference/endpoint/crawl-get-errors.md)
- [Crawl Params Preview](https://docs.firecrawl.dev/api-reference/endpoint/crawl-params-preview.md)
- [Crawl](https://docs.firecrawl.dev/api-reference/endpoint/crawl-post.md)
- [Credit Usage](https://docs.firecrawl.dev/api-reference/endpoint/credit-usage.md)
- [Historical Credit Usage](https://docs.firecrawl.dev/api-reference/endpoint/credit-usage-historical.md)
- [Docs Search](https://docs.firecrawl.dev/api-reference/endpoint/docs-search.md): Answer Firecrawl documentation questions using the public docs corpus.
- [Map](https://docs.firecrawl.dev/api-reference/endpoint/map.md)
- [Get Monitor Check](https://docs.firecrawl.dev/api-reference/endpoint/monitor-check-get.md)
- [List Monitor Checks](https://docs.firecrawl.dev/api-reference/endpoint/monitor-checks-list.md)
- [Create Monitor](https://docs.firecrawl.dev/api-reference/endpoint/monitor-create.md)
- [Delete Monitor](https://docs.firecrawl.dev/api-reference/endpoint/monitor-delete.md)
- [Get Monitor](https://docs.firecrawl.dev/api-reference/endpoint/monitor-get.md)
- [List Monitors](https://docs.firecrawl.dev/api-reference/endpoint/monitor-list.md)
- [Run Monitor](https://docs.firecrawl.dev/api-reference/endpoint/monitor-run.md)
- [Update Monitor](https://docs.firecrawl.dev/api-reference/endpoint/monitor-update.md)
- [Parse](https://docs.firecrawl.dev/api-reference/endpoint/parse.md)
- [Queue Status](https://docs.firecrawl.dev/api-reference/endpoint/queue-status.md)
- [Scrape](https://docs.firecrawl.dev/api-reference/endpoint/scrape.md)
- [Stop Interacting](https://docs.firecrawl.dev/api-reference/endpoint/scrape-browser-delete.md): Stop the interactive browser session associated with a scrape job.
- [Interact with the page](https://docs.firecrawl.dev/api-reference/endpoint/scrape-execute.md): Execute code or an AI prompt in the browser session bound to a scrape job.
- [Search](https://docs.firecrawl.dev/api-reference/endpoint/search.md)
- [Token Usage](https://docs.firecrawl.dev/api-reference/endpoint/token-usage.md)
- [Historical Token Usage](https://docs.firecrawl.dev/api-reference/endpoint/token-usage-historical.md)
- [Batch Scrape Completed](https://docs.firecrawl.dev/api-reference/endpoint/webhook-batch-scrape-completed.md): Webhook event sent when all URLs in a batch scrape have been processed.
- [Batch Scrape Page](https://docs.firecrawl.dev/api-reference/endpoint/webhook-batch-scrape-page.md): Webhook event sent for each URL scraped during a batch scrape job.
- [Batch Scrape Started](https://docs.firecrawl.dev/api-reference/endpoint/webhook-batch-scrape-started.md): Webhook event sent when a batch scrape job begins processing.
- [Crawl Completed](https://docs.firecrawl.dev/api-reference/endpoint/webhook-crawl-completed.md): Webhook event sent when a crawl job finishes and all pages have been processed.
- [Crawl Page](https://docs.firecrawl.dev/api-reference/endpoint/webhook-crawl-page.md): Webhook event sent for each page scraped during a crawl job.
- [Crawl Started](https://docs.firecrawl.dev/api-reference/endpoint/webhook-crawl-started.md): Webhook event sent when a crawl job begins processing.
- [Monitor Check Completed](https://docs.firecrawl.dev/api-reference/endpoint/webhook-monitor-check-completed.md)
- [Monitor Page](https://docs.firecrawl.dev/api-reference/endpoint/webhook-monitor-page.md)
- [Errors](https://docs.firecrawl.dev/api-reference/errors.md): Every API error code, what causes it, how to remedy it, and whether to retry.
- [Introduction](https://docs.firecrawl.dev/api-reference/v2-introduction.md): Firecrawl API Reference (v2)
- [Scraping Amazon](https://docs.firecrawl.dev/developer-guides/common-sites/amazon.md): Extract product data, prices, and reviews from Amazon using Firecrawl
- [Scraping Etsy](https://docs.firecrawl.dev/developer-guides/common-sites/etsy.md): Extract handmade products, shop data, and pricing from Etsy marketplace
- [Scraping GitHub](https://docs.firecrawl.dev/developer-guides/common-sites/github.md): Learn how to scrape GitHub using Firecrawl's core features
- [Scraping Wikipedia](https://docs.firecrawl.dev/developer-guides/common-sites/wikipedia.md): Extract articles, infoboxes, and build knowledge graphs from Wikipedia
- [Building an AI Research Assistant with Firecrawl and AI SDK](https://docs.firecrawl.dev/developer-guides/cookbooks/ai-research-assistant-cookbook.md): Build a complete AI-powered research assistant with web scraping and search capabilities
- [Building a Brand Style Guide Generator with Firecrawl](https://docs.firecrawl.dev/developer-guides/cookbooks/brand-style-guide-generator-cookbook.md): Generate professional PDF brand style guides by extracting design systems from any website using Firecrawl's branding format
- [Full-Stack Templates](https://docs.firecrawl.dev/developer-guides/examples.md): Explore real-world examples and tutorials for Firecrawl
- [Anthropic](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/anthropic.md): Use Firecrawl with Claude for web scraping + AI workflows
- [ElevenAgents](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/elevenagents.md): Give ElevenLabs voice and chat agents real-time web access with Firecrawl
- [Gemini](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/gemini.md): Use Firecrawl with Google's Gemini AI for web scraping + AI workflows
- [Agent Development Kit (ADK)](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/google-adk.md): Integrate Firecrawl with Google's ADK using MCP for advanced agent workflows
- [LangChain](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/langchain.md): Use Firecrawl with LangChain for web scraping + AI workflows
- [LangGraph](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/langgraph.md): Integrate Firecrawl with LangGraph for building agent workflows
- - [LlamaIndex](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/llamaindex.md): Use Firecrawl with LlamaIndex for RAG applications
- [Mastra](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/mastra.md): Use Firecrawl with Mastra for building AI workflows
- [OpenAI](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/openai.md): Use Firecrawl with OpenAI for web scraping + AI workflows
- [Vercel AI SDK](https://docs.firecrawl.dev/developer-guides/llm-sdks-and-frameworks/vercel-ai-sdk.md): Firecrawl tools for Vercel AI SDK. Web scraping, search, interact, and crawling for AI applications.
- [MCP Web Search & Scrape in ChatGPT](https://docs.firecrawl.dev/developer-guides/mcp-setup-guides/chatgpt.md): Add web scraping and search to ChatGPT in 2 minutes
- [MCP Web Search & Scrape in Claude.ai](https://docs.firecrawl.dev/developer-guides/mcp-setup-guides/claude-ai.md): Add web scraping and search to Claude.ai (Co-work) in 2 minutes
- [MCP Web Search & Scrape in Factory AI](https://docs.firecrawl.dev/developer-guides/mcp-setup-guides/factory-ai.md): Add web scraping and search to Factory AI in 2 minutes
- [Connect MCP Clients with OAuth](https://docs.firecrawl.dev/developer-guides/mcp-setup-guides/oauth.md): Authenticate MCP clients with Firecrawl using OAuth instead of embedding your API key in the URL
- [Choosing the Data Extractor](https://docs.firecrawl.dev/developer-guides/usage-guides/choosing-the-data-extractor.md): Compare /agent, /extract, and /scrape (JSON mode) to pick the right tool for structured data extraction
- [Firecrawl + Dify](https://docs.firecrawl.dev/developer-guides/workflow-automation/dify.md): Official plugin for Firecrawl + Dify AI workflow automation
- [Firecrawl + Make](https://docs.firecrawl.dev/developer-guides/workflow-automation/make.md): Official integration and workflow automation for Firecrawl + Make
- [Firecrawl + n8n](https://docs.firecrawl.dev/developer-guides/workflow-automation/n8n.md): Learn how to use Firecrawl with n8n for web scraping automation, a complete step-by-step guide.
- [Firecrawl + Zapier](https://docs.firecrawl.dev/developer-guides/workflow-automation/zapier.md): Official tutorials and Zapier integration templates for Firecrawl + Zapier automation
- [Debug Firecrawl with Ask](https://docs.firecrawl.dev/features/ask.md): Agentic debugging for your Firecrawl integration
- [Document Parsing](https://docs.firecrawl.dev/features/document-parsing.md): Learn about document parsing capabilities.
- [Interact after scraping](https://docs.firecrawl.dev/features/interact.md): Interact with a page you fetched by prompting or running code.
- [Lockdown Mode](https://docs.firecrawl.dev/features/lockdown.md): Cache-only scrape mode for compliance and air-gapped environments. No outbound traffic.
- [Monitoring](https://docs.firecrawl.dev/features/monitoring.md): Schedule recurring scrapes and crawls, detect content changes, and receive webhook or email notifications
- [Parse](https://docs.firecrawl.dev/features/parse.md): Upload a local or non-public document and convert it into clean, LLM-ready data
- [Partner Integration API](https://docs.firecrawl.dev/partner-integration.md): API reference for approved Firecrawl partners to create and manage API keys for their users
- [MCP Web Search & Scrape in Amp](https://docs.firecrawl.dev/quickstarts/amp.md): Add Firecrawl web scraping and search to Sourcegraph Amp
- [MCP Web Search & Scrape in Antigravity](https://docs.firecrawl.dev/quickstarts/antigravity.md): Add Firecrawl web scraping and search to Google Antigravity
- [ASP.NET Core](https://docs.firecrawl.dev/quickstarts/aspnet-core.md): Use Firecrawl with ASP.NET Core to search, scrape, and interact with web data using the REST API.
- [Astro](https://docs.firecrawl.dev/quickstarts/astro.md): Use Firecrawl with Astro to scrape, search, and interact with web data in your content-driven site.
- - [AutoGen](https://docs.firecrawl.dev/quickstarts/autogen.md): Use Firecrawl as a tool inside Microsoft AutoGen multi-agent conversations.
- [AWS Lambda](https://docs.firecrawl.dev/quickstarts/aws-lambda.md): Use Firecrawl with AWS Lambda to search, scrape, and interact with web data in serverless functions.
- [Bun](https://docs.firecrawl.dev/quickstarts/bun.md): Use Firecrawl with Bun to build fast web scraping and search servers.
- [MCP Web Search & Scrape in Claude Code](https://docs.firecrawl.dev/quickstarts/claude-code.md): Add web scraping and search to Claude Code in 2 minutes
- [Cloudflare Workers](https://docs.firecrawl.dev/quickstarts/cloudflare-workers.md): Use Firecrawl with Cloudflare Workers to search, scrape, and interact with web data at the edge.
- [MCP Web Search & Scrape in Codex CLI](https://docs.firecrawl.dev/quickstarts/codex-cli.md): Add Firecrawl web scraping and search to OpenAI Codex CLI
- [MCP Web Search & Scrape in Cursor](https://docs.firecrawl.dev/quickstarts/cursor.md): Add web scraping and search to Cursor in 2 minutes
- [Deno Deploy](https://docs.firecrawl.dev/quickstarts/deno-deploy.md): Use Firecrawl with Deno Deploy to search, scrape, and interact with web data at the edge.
- [Django](https://docs.firecrawl.dev/quickstarts/django.md): Use Firecrawl with Django to scrape, search, and interact with web data in your Python web application.
- [.NET](https://docs.firecrawl.dev/quickstarts/dotnet.md): Get started with Firecrawl in .NET. Scrape, search, and interact with web data using the REST API.
- [Elixir](https://docs.firecrawl.dev/quickstarts/elixir.md): Get started with Firecrawl in Elixir. Search, scrape, and interact with web data using the official SDK.
- [Express](https://docs.firecrawl.dev/quickstarts/express.md): Use Firecrawl with Express to build web scraping and search APIs.
- [FastAPI](https://docs.firecrawl.dev/quickstarts/fastapi.md): Use Firecrawl with FastAPI to build async web scraping and search APIs in Python.
- [Fastify](https://docs.firecrawl.dev/quickstarts/fastify.md): Use Firecrawl with Fastify to build high-performance web scraping and search APIs.
- [Flask](https://docs.firecrawl.dev/quickstarts/flask.md): Use Firecrawl with Flask to build web scraping and search APIs in Python.
- [MCP Web Search & Scrape in Gemini CLI](https://docs.firecrawl.dev/quickstarts/gemini-cli.md): Add Firecrawl web scraping and search to Google Gemini CLI
- [Go](https://docs.firecrawl.dev/quickstarts/go.md): Get started with Firecrawl in Go. Scrape, search, and interact with web data using the REST API.
- [Hono](https://docs.firecrawl.dev/quickstarts/hono.md): Use Firecrawl with Hono to build lightweight web scraping and search APIs that run anywhere.
- [Java](https://docs.firecrawl.dev/quickstarts/java.md): Get started with Firecrawl in Java. Search, scrape, and interact with web data using the official SDK.
- [Laravel](https://docs.firecrawl.dev/quickstarts/laravel.md): Use Firecrawl with Laravel to search, scrape, and interact with web data using the REST API.
- [Mastra](https://docs.firecrawl.dev/quickstarts/mastra.md): Wire Firecrawl into Mastra tools so your agents and workflows can search and scrape live web data.
- [NestJS](https://docs.firecrawl.dev/quickstarts/nestjs.md): Use Firecrawl with NestJS to build structured web scraping and search services.
- [Next.js](https://docs.firecrawl.dev/quickstarts/nextjs.md): Use Firecrawl with Next.js to scrape, search, and interact with web data in your React application.
- [Node.js](https://docs.firecrawl.dev/quickstarts/nodejs.md): Get started with Firecrawl in Node.js. Scrape, search, and interact with web data using the official SDK.
- [Nous Research](https://docs.firecrawl.dev/quickstarts/nous-research.md): Use Firecrawl as a tool with Nous Research Hermes models.
- - [Nuxt](https://docs.firecrawl.dev/quickstarts/nuxt.md): Use Firecrawl with Nuxt to scrape, search, and interact with web data in your Vue application.
- [OpenClaw](https://docs.firecrawl.dev/quickstarts/openclaw.md): Use Firecrawl with OpenClaw to give your agents web scraping, search, and browser automation capabilities.
- [MCP Web Search & Scrape in OpenCode](https://docs.firecrawl.dev/quickstarts/opencode.md): Add Firecrawl web scraping and search to OpenCode
- [OpenRouter](https://docs.firecrawl.dev/quickstarts/openrouter.md): Use Firecrawl as a tool with any model served by OpenRouter.
- [PHP](https://docs.firecrawl.dev/quickstarts/php.md): Get started with Firecrawl in PHP. Scrape, search, and interact with web data using the REST API.
- [Python](https://docs.firecrawl.dev/quickstarts/python.md): Get started with Firecrawl in Python. Scrape, search, and interact with web data using the official SDK.
- [Rails](https://docs.firecrawl.dev/quickstarts/rails.md): Use Firecrawl with Ruby on Rails to search, scrape, and interact with web data using the REST API.
- [Remix](https://docs.firecrawl.dev/quickstarts/remix.md): Use Firecrawl with Remix to scrape, search, and interact with web data in your full-stack React app.
- [Ruby](https://docs.firecrawl.dev/quickstarts/ruby.md): Get started with Firecrawl in Ruby. Search, scrape, and interact with web data using the REST API.
- [Rust](https://docs.firecrawl.dev/quickstarts/rust.md): Get started with Firecrawl in Rust. Search, scrape, and interact with web data using the official SDK.
- [Spring Boot](https://docs.firecrawl.dev/quickstarts/spring-boot.md): Use Firecrawl with Spring Boot to search, scrape, and interact with web data using the official Java SDK.
- [Supabase Edge Functions](https://docs.firecrawl.dev/quickstarts/supabase-edge-functions.md): Use Firecrawl with Supabase Edge Functions to search, scrape, and interact with web data at the edge.
- [SvelteKit](https://docs.firecrawl.dev/quickstarts/sveltekit.md): Use Firecrawl with SvelteKit to scrape, search, and interact with web data in your Svelte application.
- [Vercel Functions](https://docs.firecrawl.dev/quickstarts/vercel-functions.md): Use Firecrawl with Vercel Functions to search, scrape, and interact with web data in serverless deployments.
- [Vercel Marketplace](https://docs.firecrawl.dev/quickstarts/vercel-marketplace.md): Install Firecrawl from the Vercel Marketplace, attach it to a project, and use the injected FIRECRAWL_API_KEY in your Vercel app.
- [MCP Web Search & Scrape in Windsurf](https://docs.firecrawl.dev/quickstarts/windsurf.md): Add web scraping and search to Windsurf in 2 minutes
- [AI Platforms](https://docs.firecrawl.dev/use-cases/ai-platforms.md): Power AI assistants and let customers build AI apps
- [Competitive Intelligence](https://docs.firecrawl.dev/use-cases/competitive-intelligence.md): Monitor competitor websites and track changes in real-time
- [Content Generation](https://docs.firecrawl.dev/use-cases/content-generation.md): Generate AI content based on website data, images, and news
- [Data Migration](https://docs.firecrawl.dev/use-cases/data-migration.md): Transfer web data efficiently between platforms and systems
- [Deep Research](https://docs.firecrawl.dev/use-cases/deep-research.md): Build agentic research tools with deep web search capabilities
- [Developers & MCP](https://docs.firecrawl.dev/use-cases/developers-mcp.md): Build powerful integrations with Model Context Protocol support
- [Investment & Finance](https://docs.firecrawl.dev/use-cases/investment-finance.md): Track companies and extract financial insights from web data
- [Lead Enrichment](https://docs.firecrawl.dev/use-cases/lead-enrichment.md): Extract and filter leads from websites to power your sales pipeline
- [Observability & Monitoring](https://docs.firecrawl.dev/use-cases/observability.md): Monitor websites, track uptime, and detect changes in real-time
- - [Use Cases](https://docs.firecrawl.dev/use-cases/overview.md): Transform web data into powerful features for your applications
- [Product & E-commerce](https://docs.firecrawl.dev/use-cases/product-ecommerce.md): Monitor pricing and track inventory across e-commerce sites
- [SEO Platforms](https://docs.firecrawl.dev/use-cases/seo-platforms.md): Optimize websites for AI assistants and search engines

## OpenAPI Specs

- [v2-openapi](https://docs.firecrawl.dev/api-reference/v2-openapi.json)
- [webhooks-openapi](https:/
- installation 
npx -y firecrawl-cli@latest init --all --browser

Clr
# Install globally with npm
npm install -g firecrawl-cli

# Interactive login (opens browser or prompts for API key)
firecrawl login

# Login with browser authentication (recommended for agents)
firecrawl login --browser

# Login with API key directly
firecrawl login --api-key fc-YOUR-API-KEY

View Configuration
# Or set via environment variable
export FIRECRAWL_API_KEY=fc-YOUR-API-KEY# View current configuration and authentication status
firecrawl view-config

Logout
# Clear stored credentials
firecrawl logout

Self-Hosted / Local Development
# Use a local Firecrawl instance (no API key required)
firecrawl --api-url http://localhost:3002 scrape https://example.com

# Or set via environment variable
export FIRECRAWL_API_URL=http://localhost:3002
firecrawl scrape https://example.com

# Configure and persist the custom API URL
firecrawl config --api-url http://localhost:3002

Check Status
firecrawl --status

Output when ready:
🔥 firecrawl cli v1.16.2

  ● Authenticated via FIRECRAWL_API_KEY
  Concurrency: 0/100 jobs (parallel scrape limit)
  Credits: 500,000 remaining

Commands

Scrape
# Scrape a URL (default: markdown output)
firecrawl https://example.com

# Or use the explicit scrape command
firecrawl scrape https://example.com

# Recommended: use --only-main-content for clean output without nav/footer
firecrawl https://example.com --only-main-content
Output Formats
# Get HTML output
firecrawl https://example.com --html

# Multiple formats (returns JSON)
firecrawl https://example.com --format markdown,links

# Get images from a page
firecrawl https://example.com --format images

# Get a summary of the page content
firecrawl https://example.com --format summary

# Track changes on a page
firecrawl https://example.com --format changeTracking

# Available formats: markdown, html, rawHtml, links, screenshot, json, images, summary, changeTracking, attributes, branding
Scrape Options
# Extract only main content (removes navs, footers)
firecrawl https://example.com --only-main-content

# Wait for JavaScript rendering
firecrawl https://example.com --wait-for 3000

# Take a screenshot
firecrawl https://example.com --screenshot

# Extract structured JSON with a schema
firecrawl https://example.com --format json --schema '{"type":"object","properties":{"title":{"type":"string"}}}'

# Run lightweight scrape actions before extraction
firecrawl https://example.com --actions '[{"type":"wait","milliseconds":1000}]'

# Select proxy mode
firecrawl https://example.com --proxy basic

# Include/exclude specific HTML tags
firecrawl https://example.com --include-tags article,main
firecrawl https://example.com --exclude-tags nav,footer

# Save output to file
firecrawl https://example.com -o output.md

# Pretty print JSON output
firecrawl https://example.com --format markdown,links --pretty

# Force JSON output even with single format
firecrawl https://example.com --json

# Show request timing information
firecrawl https://example.com --timing
Available Options:
Option Short Description
--url <url> -u URL to scrape (alternative to positional argument)
--format <formats> -f Output formats (comma-separated): markdown, html, rawHtml, links, screenshot, json, images, summary, changeTracking, attributes, branding
--html -H Shortcut for --format html
--only-main-content  Extract only main content
--wait-for <ms>  Wait time in milliseconds for JS rendering
--screenshot  Take a screenshot
--full-page-screenshot  Take a full page screenshot
--include-tags <tags>  HTML tags to include (comma-separated)
--exclude-tags <tags>  HTML tags to exclude (comma-separated)
--schema <json>  JSON schema for structured extraction
--schema-file <path>  Path to JSON schema file
--actions <json>  JSON actions array to run during scrape
--actions-file <path>  Path to JSON actions file
--proxy <proxy>  Proxy mode for scraping (for example, auto or basic)
--output <path> -o Save output to file
--json  Force JSON output even with single format
--pretty  Pretty print JSON output
--timing  Show request timing and other useful information
Search the web and optionally scrape the results.
CLI: # Search the web
firecrawl search "web scraping tutorials"

# Limit results
firecrawl search "AI news" --limit 10

# Pretty print results
firecrawl search "machine learning" --pretty
Search Options
CLI:# Search specific sources
firecrawl search "AI" --sources web,news,images

# Search with category filters
firecrawl search "react hooks" --categories github
firecrawl search "machine learning" --categories research,pdf

# Time-based filtering
firecrawl search "tech news" --tbs qdr:h   # Last hour
firecrawl search "tech news" --tbs qdr:d   # Last day
firecrawl search "tech news" --tbs qdr:w   # Last week
firecrawl search "tech news" --tbs qdr:m   # Last month
firecrawl search "tech news" --tbs qdr:y   # Last year

# Location-based search
firecrawl search "restaurants" --location "Berlin,Germany" --country DE

# Search and scrape results
firecrawl search "documentation" --scrape --scrape-formats markdown

# Save to file
firecrawl search "firecrawl" --pretty -o results.json
Available Options: Option Description
--limit <number> Maximum results (default: 5, max: 100)
--sources <sources> Sources to search: web, images, news (comma-separated)
--categories <categories> Filter by category: github, research, pdf (comma-separated)
--tbs <value> Time filter: qdr:h (hour), qdr:d (day), qdr:w (week), qdr:m (month), qdr:y (year)
--location <location> Geo-targeting (e.g., “Berlin,Germany”)
--country <code> ISO country code (default: US)
--timeout <ms> Timeout in milliseconds (default: 60000)
--ignore-invalid-urls Exclude URLs invalid for other Firecrawl endpoints
--scrape Scrape search results
--scrape-formats <formats> Formats for scraped content (default: markdown)
--only-main-content Include only main content when scraping (default: true)
--json Output as JSON
--output <path> Save output to file
--pretty Pretty print JSON output
Map
Discover all URLs on a website quickly.
# Discover all URLs on a website
firecrawl map https://example.com

# Output as JSON
firecrawl map https://example.com --json

# Limit number of URLs
firecrawl map https://example.com --limit 500
Map Options
# Filter URLs by search query
firecrawl map https://example.com --search "blog"

# Include subdomains
firecrawl map https://example.com --include-subdomains

# Control sitemap usage
firecrawl map https://example.com --sitemap include   # Use sitemap
firecrawl map https://example.com --sitemap skip      # Skip sitemap
firecrawl map https://example.com --sitemap only      # Only use sitemap

# Ignore query parameters (dedupe URLs)
firecrawl map https://example.com --ignore-query-parameters

# Wait for map to complete with timeout
firecrawl map https://example.com --wait --timeout 60

# Save to file
firecrawl map https://example.com -o urls.txt
firecrawl map https://example.com --json --pretty -o urls.json
Available Options:
Option Description
--url <url> URL to map (alternative to positional argument)
--limit <number> Maximum URLs to discover
--search <query> Filter URLs by search query
--sitemap <mode> Sitemap handling: include, skip, only
--include-subdomains Include subdomains
--ignore-query-parameters Treat URLs with different params as same
--wait Wait for map to complete
--timeout <seconds> Timeout in seconds
--json Output as JSON
--output <path> Save output to file
--pretty Pretty print JSON output
Interact
# 1. Scrape Amazon's homepage (scrape ID is saved automatically)
firecrawl scrape https://www.amazon.com

# 2. Interact — search for a product and get its price
firecrawl interact "Search for iPhone 16 Pro Max"
firecrawl interact "Click on the first result and tell me the price"
# 3. Stop the session
firecrawl interact stop
Available Options:
Option Description
-p, --prompt <text> AI prompt (alternative to positional argument)
-c, --code <code> Code to execute in the live page session
-s, --scrape-id <id> Scrape job ID (default: last scrape)
--python Execute code as Python/Playwright
--node Execute code as Node.js/Playwright (default)
--bash Execute code as Bash
--timeout <seconds> Timeout in seconds (1-300, default: 30)
--output <path> Save output to file
--json Output as JSON format
Crawl
Crawl an entire website starting from a URL.
# Start a crawl (returns job ID immediately)
firecrawl crawl https://example.com

# Wait for crawl to complete
firecrawl crawl https://example.com --wait

# Wait with progress indicator
firecrawl crawl https://example.com --wait --progress
Check Crawl Status
# Check crawl status using job ID
firecrawl crawl <job-id>

# Example with a real job ID
firecrawl crawl 550e8400-e29b-41d4-a716-446655440000
Crawl Options
# Limit crawl depth and pages
firecrawl crawl https://example.com --limit 100 --max-depth 3 --wait

# Include only specific paths
firecrawl crawl https://example.com --include-paths /blog,/docs --wait

# Exclude specific paths
firecrawl crawl https://example.com --exclude-paths /admin,/login --wait

# Include subdomains
firecrawl crawl https://example.com --allow-subdomains --wait

# Crawl entire domain
firecrawl crawl https://example.com --crawl-entire-domain --wait

# Rate limiting
firecrawl crawl https://example.com --delay 1000 --max-concurrency 2 --wait

# Pass scrape options to each crawled page
firecrawl crawl https://example.com --scrape-options '{"formats":["markdown"],"onlyMainContent":true}'

# Send crawl completion events to a webhook
firecrawl crawl https://example.com --webhook '{"url":"https://example.com/webhook","events":["completed"]}'

# Cancel an active crawl
firecrawl crawl <job-id> --cancel

# Custom polling interval and timeout
firecrawl crawl https://example.com --wait --poll-interval 10 --timeout 300

# Save results to file
firecrawl crawl https://example.com --wait --pretty -o results.json
Available Options:
Option Description
--url <url> URL to crawl (alternative to positional argument)
--wait Wait for crawl to complete
--progress Show progress indicator while waiting
--poll-interval <seconds> Polling interval (default: 5)
--timeout <seconds> Timeout when waiting
--status Check status of existing crawl job
--limit <number> Maximum pages to crawl
--max-depth <number> Maximum crawl depth
--include-paths <paths> Paths to include (comma-separated)
--exclude-paths <paths> Paths to exclude (comma-separated)
--sitemap <mode> Sitemap handling: include, skip, only
--allow-subdomains Include subdomains
--allow-external-links Follow external links
--crawl-entire-domain Crawl entire domain
--ignore-query-parameters Treat URLs with different params as same
--delay <ms> Delay between requests
--max-concurrency <n> Maximum concurrent requests
--scrape-options <json> JSON scrape options passed to each page
--scrape-options-file <path> Path to scrape options JSON file
--webhook <url-or-json> Webhook URL or configuration
--cancel Cancel an active crawl job by job ID
--output <path> Save output to file
--pretty Pretty print JSON output
Monitor
firecrawl monitor create --name "Hacker News AI" \
  --schedule "every 30 minutes" \
  --goal "Alert when a new Hacker News story related to AI enters the top 10. Ignore changes to stories that are not about AI. Do not alert on changes outside the top 10." \
  --page https://news.ycombinator.com

firecrawl monitor run <monitorId>
firecrawl monitor checks <monitorId> --limit 10
firecrawl monitor check <monitorId> <checkId> --page-status changed
firecrawl monitor update <monitorId> \
  --goal "Alert when a new Hacker News story related to AI enters the top 10. Do not alert on changes outside the top 10."
  firecrawl monitor delete <monitorId>
Available Options:
Option Description
--name <name> Monitor name
--goal <goal> Goal for meaningful-change judging
--cron <expression> Cron schedule, for example */30 * * * *
--schedule <text> Natural-language schedule, for example hourly
--timezone <tz> Schedule timezone, default UTC
--page <url> Single page URL to scrape on each check
--scrape-urls <list> Comma-separated page URLs to scrape on each check
--crawl-url <url> Root URL for a crawl target
--webhook-url <url> Webhook destination
--webhook-events <list> Comma-separated monitor events
--email <list> Comma-separated email recipients
--retention-days <n> Snapshot retention window
--page-status <state> Filter pages on monitor check
--state <state> Set monitor state on monitor update: active/paused
Agent
# Basic usage - URLs are optional
firecrawl agent "Find the top 5 AI startups and their funding amounts" --wait

# Focus on specific URLs
firecrawl agent "Compare pricing plans" --urls https://slack.com/pricing,https://teams.microsoft.com/pricing --wait

# Use a schema for structured output
firecrawl agent "Get company information" --urls https://example.com --schema '{"type":"object","properties":{"name":{"type":"string"},"founded":{"type":"number"}}}' --wait

# Use schema from a file
firecrawl agent "Get product details" --urls https://example.com --schema-file schema.json --wait
Agent Options
# Use Spark 1 Pro for higher accuracy
firecrawl agent "Competitive analysis across multiple domains" --model spark-1-pro --wait

# Set max credits to limit costs
firecrawl agent "Gather contact information from company websites" --max-credits 100 --wait

# Check status of an existing job
firecrawl agent <job-id> --status

# Send agent events to a webhook
firecrawl agent "Extract product details" --urls https://example.com --webhook '{"url":"https://example.com/webhook","events":["completed","failed"]}'

# Cancel an active agent job
firecrawl agent <job-id> --cancel

# Custom polling interval and timeout
firecrawl agent "Summarize recent blog posts" --wait --poll-interval 10 --timeout 300

# Save output to file
firecrawl agent "Find pricing information" --urls https://example.com --wait -o pricing.json --pretty
Available Options:
Option Description
--urls <urls> Optional list of URLs to focus the agent on (comma-separated)
--model <model> Model to use: spark-1-mini (default, 60% cheaper) or spark-1-pro (higher accuracy)
--schema <json> JSON schema for structured output (inline JSON string)
--schema-file <path> Path to JSON schema file for structured output
--max-credits <number> Maximum credits to spend (job fails if limit reached)
--webhook <url-or-json> Webhook URL or configuration
--status Check status of existing agent job
--cancel Cancel an active agent job by job ID
--wait Wait for agent to complete before returning results
--poll-interval <seconds> Polling interval when waiting (default: 5)
--timeout <seconds> Timeout when waiting (default: no timeout)
--output <path> Save output to file
--json Output as JSON format
Credit Usage
# View credit usage
firecrawl credit-usage

# Output as JSON
firecrawl credit-usage --json --pretty
Version
Display the CLI version.
firecrawl version
# or
firecrawl --version
Global Options
These options are available for all commands:
Option Short Description
--status  Show version, auth, concurrency, and credits
--api-key <key> -k Override stored API key for this command
--api-url <url>  Use custom API URL (for self-hosted/local development)
--help -h Show help for a command
--version -V Show CLI version
Output Handling
The CLI outputs to stdout by default, making it easy to pipe or redirect:
# Pipe markdown to another command
firecrawl https://example.com | head -50

# Redirect to a file
firecrawl https://example.com > output.md

# Save JSON with pretty formatting
firecrawl https://example.com --format markdown,links --pretty -o data.json
Format Behavior
# Raw markdown output
firecrawl https://example.com --format markdown
# JSON output with multiple formats
firecrawl https://example.com --format markdown,links
Quick Scrape
# Get markdown content from a URL (use --only-main-content for clean output)
firecrawl https://docs.firecrawl.dev --only-main-content

# Get HTML content
firecrawl https://example.com --html -o page.html
Full Site Crawl
# Crawl a docs site with limits
firecrawl crawl https://docs.example.com --limit 50 --max-depth 2 --wait --progress -o docs.json
Site Discovery
# Find all blog posts
firecrawl map https://example.com --search "blog" -o blog-urls.txt
# Search and scrape results for research
firecrawl search "machine learning best practices 2024" --scrape --scrape-formats markdown --pretty
# URLs are optional
firecrawl agent "Find the top 5 AI startups and their funding amounts" --wait

# Focus on specific URLs
firecrawl agent "Compare pricing plans" --urls https://slack.com/pricing,https://teams.microsoft.com/pricing --wait
# Extract URLs from search results
jq -r '.data.web[].url' search-results.json

# Get titles from search results
jq -r '.data.web[] | "\(.title): \(.url)"' search-results.json

# Extract links and process with jq
firecrawl https://example.com --format links | jq '.links[].url'

# Count URLs from map
firecrawl map https://example.com | wc -l
