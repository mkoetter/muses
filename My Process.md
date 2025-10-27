---


---

<h1 id="my-ai-coding-workflow">My AI Coding Workflow</h1>
<h2 id="overview">Overview</h2>
<p>This is my full stack AI development workflow.  I’ve been using it for about 3 weeks as of October 27, and it’s been incredibly effective.  I’ve only used it for personal projects, so it’s optimized for basic public-facing web development - though I have created some very basic IOS apps as well.</p>
<p>My development skills are decades old.  I’ve been a tech executive for the past 20 years, and have barely coded in that time period.  So I think like a more like a product manager, architect or dev manager than an actual software engineer.  I think that’s why this process has been such a good match for me.</p>
<p>Claude Code works a lot like a developer.  I spend a lot of time in “planning” mode, just talking to it.  CC helps me to refine my ideas and create detailed requirements.  It helps me to conceptualize the target architecture, including the creation of subsystems or libraries that contain complexity, allowing my apps to grow without becoming unwieldy.  I use it to document coding standards, logging and optimizations (code hygiene, de-duplication, performance, security, comments, documentation) Finally, it helps me to create and implement my SDLC.</p>
<p>A huge unlock was getting CC to play different roles on the project.  A single threaded CC instance takes forever, and the context gets very muddled with different concerns.  By spinning up separate CC instances with dedicated personas, they can work together as a team of specialists.  Their context stays small &amp; on-mission for a specific goal.  In my workflow, this could be requirements planning, architectural design, feature development, code optimization or devops functions.</p>
<h2 id="tools">Tools</h2>
<p><strong>Claude Code CLI</strong><br>
I work exclusively through the Claude Code CLI.  It knows how to run all my secondary tools via MCP or CLI.    I am interested in using the web interface to do on-the go development.  As a CLI, you can run it right in your IDE.  I ran it for a while in Cursor and VSCode, but have since decided that I like to run it standalone with VSCode open for rare direct file edits.  <em>Side note: if you want to use our company’s Bedrock API key for access to Anthropic models, you need to use the CLI.</em></p>
<p><strong>MCP’s</strong><br>
There are a ton of these, and I’ve really just dipped my toe in the waters here.  The MCP I use most often is MS Playwright, which gives CC the ability to see and drive the app it’s building.  This is huge, and saves me a ton of time pasting console logs or taking screenshots.</p>
<p><strong>Github</strong><br>
All projects are stored in Github.  I’ve installed the Github CLI, which Claude Code uses very well.  There are a lot of cool Github tools out there, but CC can do everything I need without having to jump into the web or desktop UI’s.</p>
<p><strong>Vercel</strong><br>
Vercel provides a no-fuss serverless next.js hosting environment.  It also has a CLI tool that CC can run.  So I can ask CC in plain English to do things like create a project, link it to a Github repo, deploy code to a specific environment, etc.  It can even securely migrate environment variables like API keys, which makes the whole process very simple.</p>
<p><strong><a href="http://Stackedit.io">Stackedit.io</a></strong><br>
CC likes to use markdown files for documentation.  I needed a simple tool for writing markdown.  I’m writing this right now in Stackedit, and it’s great.</p>
<h2 id="process">Process</h2>
<p><strong>Scaffolds</strong><br>
I found that I was spending a lot of time setting up new projects that had the same underlying ingredients (Next.js, Typescript, Mongo).  So I made a very clean baseline &amp; published it to Github as a template.  CC can now create new projects from this template in just a few minutes.</p>
<p><strong>Specifications</strong><br>
While it is absolutely amazing that CC can create an app from almost no direction, it is better when you have a coherent idea what you want to achieve.  I have a /docs folder in my project where I store all of my documents specifying requirements, design, process and standards.  I reference some of these documents in my .claude file (which is the first thing CC sees when it loads).  I write my specs in markdown, but I often use CC as a technical writer, developing markdown specs based on my direction.</p>
<p><strong>Development</strong><br>
Once I have my scaffold stood up &amp; have developed my core specifications, I start development. I will keep one CC instance open as my devops manager.  Then I open new CC instances &amp; start developing features or components using Github Worktrees.  This allows multiple instances to work independently without conflicting.  Once development is largely complete, I will do UAT.  I will often iterate at this point based on feedback on the implementation.</p>
<p><strong>Optimization</strong><br>
When I’m ready to move forward, I will then hand the feature off to my optimizer persona.  I could probably split this into several workers, but currently, optimization includes enforcing the DRY principle, commenting, documentation and performance optimization.  The final step of optimization is to merge the Worktree back to main.  I think there is a lot of opportunity for improvement here.</p>
<p><strong>Deployment</strong><br>
When I am ready to deploy, I tell my devops instance of claudecode what environment I want to target.  It handles the entire process.</p>
<h2 id="setup">Setup</h2>
<p>First, you need a Claude Code account with enough capacity to handle your development workload.  I found that with a multi-worker setup, I need a lot more tokens than a single instance implementation.  When it is approved, we will have a mechanism for allocating enterprise keys to internal CC developers.</p>
<p><strong>Claude Code</strong></p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">npm</span> <span class="token function">install</span> -g @anthropic-ai/claude-code
</code></pre>
<p><strong>GitHub CLI</strong></p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">npm</span> <span class="token function">install</span> -g gh
</code></pre>
<p><strong>Vercel CLI</strong></p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">npm</span> <span class="token function">install</span> -g vercel
</code></pre>
<p><strong>Microsoft Playwright MCP Server</strong></p>
<pre class=" language-bash"><code class="prism  language-bash"><span class="token function">npm</span> <span class="token function">install</span> -g @modelcontextprotocol/server-playwright
</code></pre>

