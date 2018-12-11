## Meta-Formats Consortium (MFC)


### Introduction

It is generally the intelligence agencies, that have a need to integrate and understand and reuse large sets of heterogenous data, from a variety of sources, and trigger actions on diverse resources. During the recent history, such needs had arisen to multiple individual data companies too.

The existing initiatives, like JSON-LD, developed by W3C (World Wide Web Consortium) and OpenAPI, developed by Linux Foundation, are insufficient (focusing on specific formats, not general meta-formats, that would empower all legacy and future systems to inter-operate, no matter what APIs they have, or what protocols they follow).

Meta-formats introduces a general solution to this problem.

<i>**NOTE:** The abstraction level at which meta-formats operate, is comparable to the metalanguages like [BNF](https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form#Introduction), and is sufficiently expressive to, for example, rewrite [IEFT RFCs](https://www.ietf.org/standards/rfcs/) in machine-readable form.</i>

### Purpose

To introduce data meta-formats to maximize reusability of data and systems, in order to make them relevant and directly useful for the future of the [evolution of information](../metaformat/0001-metaform-philosophy/0001-metaform-philosophy.md#purpose).

### Vision

As a result, we are able to do arbitrary queries about the web, as if the web is one database. Think, `SELECT * FROM EVERYTHING`, in everyone's own language, from any source, and do actions `PERFORM * ON ANYTHING` on arbitrary world's resources. Data shall carry control interfaces, permissions, ontologies of the data fields, enabling to auto-combine, control the thigns represented by data, and pre-define analytics and procedures for AI and IoT applications. Not only shall we be able to have data auto-align but also things represented by data auto-control: `MY_THING.turn_lights_on()`, or `MY_CNC_MACHINE.cut()`, `MY_DRUG_DISCOVERY_EQUIPMENT.experiment()` just by having data representing the machine, without any extra programming.

It will `empower further evolution of information and automation of problem solving`, for example, machines learning for fixing issues becomes a self-evolving automatic process, rather than something that we have pay conscious attention to.

Efforts to automate the generation of the so-called [metaheader](../metaformat/0002-data-object-format/0002-data-object-format.md) through use of machine learning, shall enable us to completely automatic data alignment, and remote procedure calls regardless of language or format it comes from.

### Invitation to Agreement

See the [introduction](#meta-formats-consortium-mfc) for more details.

- **WHEREAS** Mindey has researched and developed a paradigm for universal data integration and reuse formats (called "metaformat" [[1]](../metaformat/0002-data-object-format/0002-data-object-format.md)) with the objective to empower the evolution of information maximizing the reusability of data and systems, and sees a greater potential in having the the specific metaformat further researched, developed and used within a group of friendly partner organizations, that share the data needs, and would want to be the first to reap the benefits of the capabilities that the pattern introduces.
- **WHEREAS**  (WeFindX Foundation, Ireland) has developed initial versions [[2]](https://gitlab.com/wefindx) for the implemenation of [metaformat requirements](../metaformat/0001-metaform-philosophy/0001-metaform-philosophy.md#metaformat-requirements), immediatelly usable to perform useful tasks, such as automated harvesting, normalizing, understanding, aligning, querying, reasoning with data.
- ..
- **WHEREAS** Partner organizations expressed interest in having a format with those capabilities:
    - **[Company SC]**
      Crawl, combine, and do recommendation systems and applications more efficiently ("we want a reliable and big data, to support supply chain intelligence needs.")
    - **[Company ST]**
      Empwoer browser users to collect, utilize and monetize all their personal web browsing data - be able to perform comparison analyses for any products, contacts, social posts, etc., that are available on the web, call any function, that was originally available in any site they visited, functinally turning browser into a powerful personal intelligence tool.
    - **[Company SP]**
      Automate combining and querying large sets of proprietary data from large set of companies ("we have a set of companies, where each has their own infrastructures, and formats, and want to be able to do generic and arbitrary queries about information available in a variety of large proprietary databases of those companies.")
    - **[Company IV]**
      Acquire data sources quickly for computing and providing metrics ("we want dirty real time data be available right away, to compute trust scores, so that insights can be delivered immediately - no disaster relief programs should wait for long time to get clean data, as everyone might be dead by then")
    - ..
- **WHEREAS** Mindey sees a potential for overal greater gains from sharing the technology with the partners, where each of clear vision, internal resources, and passion towards data and AI applications, in that:
    - Research and development together with friends is likely to lead to arriving at a more robust, and generally useful format.
    - The organizations in question are willing to contribute human resources for adoption of the metaformat for their own benefit, and may resolve discover and help resolve issues in the process.

**THEREFORE**

Mindey invites the representatives from organizations to the introductory meeting, to see the benefits, and consider forming a "universal data consortium", with the objective to benefit their organizations, and contribution to the further work on the metaformat and its implementation within the close-sourced codebase, hosted by WeFindX Foundations as lead provider organization, with publicly open format specification, yet implementation code available via non-public package managers (such as PyPI hosted by one of the organizations), initially closed, but with longer term perspective to have it open, and have the meta-formats ISO-certified.

# The Subject Matter

- Demonstration of the capabilities.
- Discussion on The Rules of Interaction and Cooperation.
- Inviting members to share creating robust and open implementation of metformat for greater capabilities.

# Proposed Rules of Interaction

1. The organizations enter the consortium up the free will of their CEO representatitves, with the intention to enjoy the technology, cooperation, benefit personally, and benfit the vision.
2. WeFindX Foundation shall take the role of [lead provider organization](http://www.valonline.org.uk/book/export/html/174#node-169), that provides guidance, private repository for cooperation, and private PyPI repository for use. Later, we can change lead provider organization by a collective vote.
3. None of the organizations shall start developing generic metaformat internally, without sharing it with the members of the consortium. Doing so will be considered a breach of trust between organizations, and the organization that did so, will have to pay a fine to be determined based on the competitive advantages reduced for ther members.
4. WeFindX Foudnation shall take the responsibility to introduce the metaformat, and provide teaching session that will be recorded for everyone's use, and educational purposes.
5. No organization-specific data shall be shared with member organizations, other than mocked up data for demo purposes, unless explicitly desired by any of the organizations on their own discretion.
6. Under no circumstances, shall the member organizations, or its employees or contractors will reveal the details of implementation of metaformat to external parties, without collective agreement, and shall not advertise the metaformat's publicly shared specification. (Specification is so abstract, that it takes a lot of development work to realize it, so, major value then is the implementation, but keeping quiet about it for the time being may still be beneficial.)
7. Organizations shall require zero fee, and will be expected to fund the work of research and development by allocating part of the time of their staff to work on applications of the metaformat to their internal business, and using a compromise as a way to decide on the generic choices during the metaformat and its implementation (software) development.
8. None of the organizations shall patent, license or try to take the ownership of the process alone, and the decision to do so, and how specifically to do so shall be made according to the decision-making model, in which case, we collectively can decide to change our operation model into a [Hub and Spoke Model](http://www.valonline.org.uk/book/export/html/174#node-167), and license the technology on behalf of dedicated legal entity, which members shall own equally.

# Proposed Decision Making Model

Decisions are made by voting from members of each organization.

- Each organization provides 2 members, where one is technical, another is C-level executive, for voting.
- Each vote has to have associated bona-fide argument, as to why the vote is such, and a philosophical rationale behind it, connecting directly to the **purpose**, as well as internal needs of each the company.
- Each member has the right to change vote, after reviewing the arguments.
- The majority rule.
- Each has a veto right with a bona-fide argument, only if the argument is directly related to the **purpose**, for example, in any way restricts the pursue of the purpose.

# Proposed Court and Jurisdiction for Agreement

- London (UK)
- International law, as possible.

# Tasks

## Schedule 1
- Fine-tuning the metaformat, and getting maximum utility from it to organize (align and inteface with) our internal data sets and data sources, enabling global searches, and intelligence, from code intelligence to data intelligence.

## Schedule 2
- Automation the generation of metaheader via machine learning and NLP.
