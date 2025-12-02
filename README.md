**The ai + history collaboratory is an online forum with synchronous and asynchronous components. We meet monthly online and maintain the ai-and-history-collaboratory GitHub repository for asynchronous communication between sessions. This collaboratory is a continuation of the December 2024 marinelives-collaboratory, in terms of its focus on ai and history. Depending on how the collaboratory develops, we may identify potential collective collaboratory projects, or simply share projects of individual members of the collaboratory. The repository has both a wiki and a discussion board.**

The topic of our first online session on Tuesday, December 9th 2025 will be the conceptualisation, design and development of a Socratic research tool powered by Gemini (https://github.com/Addaci/Generative-Lives-Research-App/wiki), and its potential application within historical research.

---
Confirmed participants [alphabetical]

*[Gavin Beinart-Smollan](https://www.linkedin.com/in/beismo/)* |
*[Maurice Brenner](https://www.linkedin.com/in/maurice-brenner-448134a/?originalSubdomain=uk)* |
*[Abi Cunningham](https://www.linkedin.com/in/abi-cunningham-1b4481273/?originalSubdomain=uk)* |
*[Marc Eagle](https://www.wku.edu/history/staff/marc_eagle)* |
*[Jacob Forward](https://www.hist.cam.ac.uk/people/jacob-forward)* |
*[Colin Greenstreet (convenor)](https://marinelives.academia.edu/ColinGreenstreet)* |
*[Thiago Krause](https://clasprofiles.wayne.edu/profile/hq8728)* |
*[Oren Okhovat](https://jewishstudies.yale.edu/profile/oren-okhovat)* |
*[Mark L. Thompson](https://research.rug.nl/en/persons/mark-thompson/publications/)* |

---

**DRAFT SCHEDULE OF MEETINGS**

### DECEMBER 2025

Tuesday, December 9th 2025 @ 4 pm UK time; 5 pm Paris, Berlin, Madrid; 11 am EST by ZOOM

### Socratic Research Agents

**Conceptualising, designing, and building a Socratic Research Agent for historical research powered by Gemini 3 Pro Preview** [Colin Greenstreet]

Introduction to Research Agents

Demonstration of Socratic Research Agent in Google AI Studio

Hands-on testing and improvement of the Agent in real time by members of the Collaboratory

---

### JANUARY 2026

### HTR/NER

**Developments in HTR and NER and their implications for historical research**

Discussing Gemini 3 Pro Preview native English language HTR and NER capabilities

Reviewing theoretical basis of strong Gemini performance in machine transcription

Sharing experimental data for transcription of English High Court of Admiralty depositions

> Contrasting Gemini 3 Pro Preview results with Leo and Transkribus

Sharing experimental data for transcription of primary source handwritten documents used by other ai and history collaboratory members

```
FOR DISCUSSION SPECIFICALLY OF GEMINI 3 PRO PREVIEW

> Developing, iterating, critiquing and refining your transcription strategy with Gemini 3 Pro Preview for your particular use case
>> Conducting an initial review of the palaeographical and content challenge of your material
>> Conducting an initial review of available Ground Truth prepared for previous machine transcription, or for scholarly editions
>> Conducting an initial review of past machine transcription output and work flows with other machine transcription services
and/or software

QUESTION
> Should transcription strategy with Gemini 3 Pro Preview vary according to English/Non-English primary material?
> Shoudl transcription strategy with Gemini 3 Pro Preview vary for low resource languages
e.g. Yiddish, Armenian, Ottoman Turkish?

> Calling detailed well structured Systems Instructions with short User prompts

> Using glossaries encoded in JSON Schemas in System Instructions
>> COMPONENTS OF SCHEMA: Canonical; attested form (variants); definition

> Setting temperature, thinking level, and media resolution according to transcription strategy
>> LOW (0.1-0.2), LOW, DEFAULT (Mark Humphries)
>>> Evidence for settings, fit with transcription strategy, impact on quality of output, and impact on cost of input/output?
>> LOW (0.15 to 2.0), HIGH, DEFAULT (Colin Greenstreet)
>>> Evidence for settings, fit with transcription strategy, impact on quality of output, and impact on cost of input/output

> Are any tools relevant to transcription strategy? Review purpose of structured outputs, code execution, function calling,
grounding with Google Search, and URL context

```

***Suggested reading***

`Humphries, Mark, 'Gemini 3 Solves Handwriting Recognition and it’s a Bitter Lesson: Testing shows that Gemini 3 has effectively solved handwriting on English texts, one of the oldest problems in AI, achieving expert human levels of performance.', Generative History, November 24th 2025`. Click [here](https://generativehistory.substack.com/p/gemini-3-solves-handwriting-recognition).` 

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
> It would be interesting to discuss what history domain agents for dealing with large quantities 
of documents would require as skills. 
> I think by the way that Chamelio's product is a wrapper over ChatGPT 5.1.
```
See [Chamelio product demo](https://www.youtube.com/watch?v=k_VDUazeftE). 

---

### APRIL 2026

### Simulations

**Developing historical simulations for teaching and research purposes.** 

Explore how students themselves can develop simulations, thus improving their generative-ai skills, including understanding python basics, the software development process, and the UI/UX design process etc. Members of the collaboratory to suggest ideas for simulations which are bite size and which interest them. 

**USE CASE:**
For example, I would be interested in developing a simulation to explore the writing of charter parties by scriveners and how merchants and masters and ship owners engaged in discussions and negotiations resulting in drafting of terms. I have high quality images and full transcriptions of actual charter parties from the 1620 to 1680 period. The simulation could also draw on statute and case law regarding charter parties and contracts grounded in C17th English practice.

---

### MAY 2026

## Skills/Tools

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






