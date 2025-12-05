**The ai + history collaboratory is an online forum with synchronous and asynchronous components. We meet monthly online and maintain the ai-and-history-collaboratory GitHub repository for asynchronous communication between sessions. This collaboratory is a continuation of the December 2024 marinelives-collaboratory, in terms of its focus on ai and history. Depending on how the collaboratory develops, we may identify potential collective collaboratory projects, or simply share projects of individual members of the collaboratory. The repository has both a wiki and a discussion board.**

This season's AI + History collaboratory (2025/26) will run for six monthly sessions from December 2025 to May 2026, with a possible History Hackathon in June 2026 to be organised by our Collaboratory, but with a wider group of participants. I am already planning a second season (2026/27), which will run monthly from September 2026 to May 2027.

The topic of our first online session on Tuesday, December 9th 2025 will be the conceptualisation, design and development of a Socratic research tool powered by Gemini (https://github.com/Addaci/Generative-Lives-Research-App/wiki), and its potential application within historical research.

---
Confirmed participants [alphabetical]

*[Gavin Beinart-Smollan](https://www.linkedin.com/in/beismo/)* |
*[Maurice Brenner](https://www.linkedin.com/in/maurice-brenner-448134a/?originalSubdomain=uk)* |
*[David Brown](XX)* |
*[Abi Cunningham](https://www.linkedin.com/in/abi-cunningham-1b4481273/?originalSubdomain=uk)* |
*[Marc Eagle](https://www.wku.edu/history/staff/marc_eagle)* |
*[Jacob Forward](https://www.hist.cam.ac.uk/people/jacob-forward)* |
*[Colin Greenstreet (convenor)](https://marinelives.academia.edu/ColinGreenstreet)* |
*[Thiago Krause](https://clasprofiles.wayne.edu/profile/hq8728)* |
*[Oren Okhovat](https://jewishstudies.yale.edu/profile/oren-okhovat)* |
*[Mark L. Thompson](https://research.rug.nl/en/persons/mark-thompson/publications/)* |

Confirmed observers [alphabetical]

[Sam Kaislaniemi](https://www.helsinki.fi/en/researchgroups/variation-contacts-and-change-in-english/people/samuli-kaislaniemi) 

Our participants are members of, or associated with, a wide range of universities in the US, UK, and continental Europe, including the University of Cambridge, University of East Anglia, University of Groningen, New York University, Trinity College Dublin, Wayne State University, Western Kentucky University, Yale University, University of York.

---

**DRAFT SCHEDULE OF MEETINGS for 2025/26 SEASON**

### DECEMBER 2025

Tuesday, December 9th 2025 @ 4 pm UK time; 5 pm Paris, Berlin, Madrid; 11 am EST by ZOOM

### Socratic Research Agents

**Conceptualising, designing, and building a Socratic Research Agent for historical research powered by Gemini 3 Pro Preview** [Colin Greenstreet]

Introduction to Research Agents

Demonstration of Socratic Research Agent in Google AI Studio

Hands-on testing and improvement of the Agent in real time by members of the Collaboratory

---

### JANUARY 2026

Tuesday, January 20th 2025 @ 4 pm UK time; 5 pm Paris, Berlin, Madrid; 11 am EST by ZOOM

### HTR/NER

**Developments in HTR and NER and their implications for historical research**

Discussing Gemini 3 Pro Preview's native English language HTR and NER capabilities

Discussing Gemini 3 Pro Preview's low resource language HTR and NER capabilities.

> Use case: Armenian; Mixed Russian/Armenian
> 
> Use case: Yiddish

Reviewing theoretical basis of strong Gemini performance in machine transcription

Sharing experimental data for transcription of English High Court of Admiralty depositions

Contrasting Gemini 3 Pro Preview results with Leo and Transkribus

Sharing experimental data for transcription of primary source handwritten documents used by other Ai + History collaboratory members

```
FOR DISCUSSION SPECIFICALLY OF HANDS ON EXPERIENCE OF GEMINI 3 PRO PREVIEW

> Developing, iterating, critiquing and refining your transcription strategy with Gemini 3 Pro Preview for your particular use case
* Conducting an initial review of the palaeographical and content challenge of your material
* Conducting an initial review of available Ground Truth prepared for previous machine transcription, or for scholarly editions
* Conducting an initial review of past machine transcription output and workflows with other machine transcription services
and/or softwarefor your material [no one starts a new transcription project without history of past tools & workflows]

> Calling detailed well structured Systems Instructions with short User prompts
* Keep it simple and heavily visually grounded versus use semantic reading to clean up?

> Using glossaries encoded in JSON Schemas in System Instructions. Good idea or not?
>> COMPONENTS OF SCHEMA: Canonical; attested form (variants); definition

> Setting temperature, thinking level, and media resolution according to transcription strategy
>> LOW (0.1-0.2), LOW, DEFAULT (Mark Humphries)
>>> Evidence for settings, fit with transcription strategy, impact on quality of output, and impact on cost of input/output?
>> LOW (0.15 to 0.2), LOw/HIGH, DEFAULT (Colin Greenstreet)
>>> Evidence for settings, fit with transcription strategy, impact on quality of output, and impact on cost of input/output

> Are any Google AI Studio console tools relevant to transcription strategy?
>> Review purpose of structured outputs, code execution, function calling,
grounding with Google Search, and URL context

> Building a transcription workflow
>> Batch processing of images using a Colab Notebook and some basic python (generated by Gemini 3 Pro and tested
by Colin Greenstreet)

QUESTIONS
> Should transcription strategy with Gemini 3 Pro Preview vary according to English/Non-English primary material?
> Should transcription strategy with Gemini 3 Pro Preview vary for low resource languages?
e.g. Armenian, Ottoman Turkish, Yiddish?
```

***Suggested reading***

`Crosilla G, Klic L, Colavizza G (2025), "Benchmarking large language models for handwritten text recognition". Journal of Documentation, Vol. 81 No. 7 pp. 334–354, doi: https://doi.org/10.1108/JD-03-2025-0082.` Click [here](https://doi.org/10.1108/JD-03-2025-0082)

`Humphries, Mark, 'Gemini 3 Solves Handwriting Recognition and it’s a Bitter Lesson: Testing shows that Gemini 3 has effectively solved handwriting on English texts, one of the oldest problems in AI, achieving expert human levels of performance.', Generative History, November 24th 2025.` Click [here](https://generativehistory.substack.com/p/gemini-3-solves-handwriting-recognition).` 



---

### FEBRUARY 2026

### Search/Discovery

**Google search in ai mode, Gemini 3 Pro Preview and Google Scholar Labs as tools to assist in annotating and contextualising historical documents.** 

How might they be included in manual and/or automated research flows? 

How can forensic, carefully structured search be linked to hard to access, proprietary, firewalled databases? 

How can LLM enabled search interrogate library catalogues?

How can LLM enabled search interrogate large digital history databases like Old Bailey Online and the MarineLives Semantic Media Wiki?

See: [Google search in ai mode](https://search.google/ways-to-search/ai-mode),
See: [Google Scholar Labs](https://scholar.google.com/scholar_labs/search?hl=en) 

---

### MARCH 2026

### Databases

**Exploring the concept of different types of document agents to work with databases which contain metadata and text.**

The mental model I am thinking of is the legal tech product of the US company Chamelio, which is a Legal Intelligence platform targeted at in-house legal teams. The product has multiple agents optimised to do things like (a) initiate a new legal review (b) review contract revisions (c) create a document summary (d) ask questions. Each agent is optimised for a narrow set of tasks. 

**USE CASE:**
We could use English High Court of Admiralty depositions as a use case, where I have complex metadata and text extracts for many HCA 13/ volumes between the 1620s and late 1680s, and also have high quality full text. The obvious thing is to create a RAG database, using a LLM to help automate the creation and population of the database, stripping out the text from my GitHub HCA repository or from the MarineLives wiki. But purely as a demo we could create a flat Excel database populated with (say) 100 depositions and associated metadata. 

```
FOR DISCUSSION

> What skills do history domain agents would require to deal with large quantities 
of documents?
> Could we in our AI + History Collaboratory experiment with Model Context Protocol (MCP) to
facilitate LLM interaction with digital archives. 
>> We could create a small POC using the MarineLives SemanticMediaWiki as a Use Case
>> See Dan Cohen's August 2025 article.
```

See [Chamelio product demo](https://www.youtube.com/watch?v=k_VDUazeftE). 
> I think by the way that Chamelio's product is a wrapper over ChatGPT 5.1.

***Suggested reading***

`Anonymous, What is the Model Context Protocol (MCP), Technical documentation.` Click [here](https://modelcontextprotocol.io/docs/getting-started/intro?utm_source=dancohen&utm_medium=email&utm_campaign=ai-and-libraries-archives-and-museums-loosely-coupled)

`Anthropic, 'Claude can now connect to your world', Press Release, May 1st 2025.` Click [here](https://claude.com/blog/integrations?utm_source=dancohen&utm_medium=email&utm_campaign=ai-and-libraries-archives-and-museums-loosely-coupled)

`Cohen, Dan, 'AI and Libraries, Archives, and Museums, Loosely Coupled. A new framework provides a way for cultural heritage institutions to take advantage of the technology with fewer misgivings, and to serve students, scholars, and the public better', Human Ingenuity, August 18, 2025.` Click [here](https://generativehistory.substack.com/p/gemini-3-solves-handwriting-recognition).` 

`Scheinfeldt, Tom. 'Making an AI Frontend for ArchivesSpace. Have you ever wanted to talk with your finding aid?', Blog entry, November 19th 2025.` Click [here](https://foundhistory.org/making-an-ai-frontend-for-archivesspace/)

***Suggested resource***

5-Day AI Agents Intensive Course with Google: originally held live from November 10 - 14, 2025. It is now available as a self-paced Kaggle Learn guide. Click [here](https://www.kaggle.com/learn-guide/5-day-agents)

`Day 1 - Introduction to Agents: Explore the foundational concepts of AI agents, their defining characteristics, and how agentic architectures differ from traditional LLM applications, laying the groundwork for building intelligent, autonomous systems.`

`Day 2 - Agent Tools & Interoperability with Model Context Protocol (MCP): Dive into the world of tools, understanding how AI agents can "take action" by leveraging external functionalities and APIs, and explore the ease of discovering and using tools offered by the MCP.`

`Day 3 - Context Engineering: Sessions & Memory: Explore how to build AI agents that can remember past interactions and maintain context. Learn how to implement short-term and long-term memory to create more robust agents capable of handling complex, multi-turn tasks.`

`Day 4 - Agent Quality: Learn to build robust and reliable AI agents by mastering the critical disciplines of evaluating and improving agents. This session will cover observability, logging, and tracing to provide visibility, alongside key metrics and evaluation strategies to optimize agent performance.`

`Day 5 - Prototype to Production: Go beyond local testing and learn to deploy and scale AI agents for real-world use. This session will cover the best practices for deploying your agents so that others can use them, including how to create a truly multi-agent system with the Agent2Agent (A2A) Protocol`.

---

### APRIL 2026

### Simulations

**Developing historical simulations for teaching and research purposes.** 

Explore how students themselves can develop simulations, thus improving their generative-ai skills, including understanding python basics, the software development process, and the UI/UX design process etc. Members of the collaboratory to suggest ideas for simulations which are bite size and which interest them. 

**USE CASE:**
For example, I would be interested in developing a simulation to explore the writing of charter parties by scriveners and how merchants and masters and ship owners engaged in discussions and negotiations resulting in drafting of terms. I have high quality images and full transcriptions of actual charter parties from the 1620 to 1680 period. The simulation could also draw on statute and case law regarding charter parties and contracts grounded in C17th English practice.

---

### MAY 2026

### Skills/Tools

**Developing a core skills, and knowledge inventory for history-tech enhanced historical research.**

**Reinventing the History PhD in the world of ai-enabled research.**

SKILLS

> Building historical research agents to automate work processes
> 
> Designing, populating and interrogating flat databases using LLMs
> 
> Designing,  populating and interrogating RAG databases
> 
> Structuring and critiquing prompts and chains of thought

TOOLS

> Colab
> 
> Gemini 3 Pro; Claude 4.5; ChatGPT5.1
> 
> Google AI Studio
> 
> Python

 KNOWLEDGE

> Fundamentals of search and discovery
>
> Fundamentals of HTR, NER and Knowledge Graphs

```
FOR DISCUSSION

> What skills, tools and knowledge have you been using drawing on history tech?
> What would a process to develop a skills training curriculum look like?
> What would a one year preparatory skills training course look like? Would it increase non-academic post-PhD employability?
> How about a June 2026 face to face or online history tech hackathon for PhD and postdoc historians and computer scientists?
```
---

### JUNE 2026

### History Hackathon

**Possible June 2026 face to face or online history tech hackathon for PhD and postdoc historians and computer scientists**

---

**DRAFT SCHEDULE OF TOPICS FOR 2026/27 SEASON**

[Planned to start in September 2026 after a summer break for July and August]

### Metacognition

```
FOR DISCUSSION

> Developing your own "voice" and confidence when interacting with a LLM
> Designing and recording experiments to conduct with a LLM [Lab Notebooks]
> Co-development and documentation of hypotheses and arguments with a LLM [Research Notebooks]
```
### Tool Building

```
FOR DISCUSSION

> Developing your own tools vs. using existing tools?
> Repurposing old tools for new purposes using generative-ai to redesign them or to power them?
> What common protocols exist to enable tools to connect with each other and to connect with LLMs [e.g. MCP]
> Building tools into workflows?
```







