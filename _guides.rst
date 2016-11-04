.. _guides:

User Guides
===========

This section describes what DM user guides are, and how they are produced by user guide working groups.

Role
----

User guides empower the people who use DM's software, platforms, and data products.
A user guide can contain reference information, conceptual narratives, task guidance, tutorials, and even marketing information.
In many cases, a user guide can be the primary web-facing manifestation of a DM product.

User guides can be aimed at internal or external audiences, or both simultaneously.
The `DM Developer Guide`_, and back-end operations guides, are examples of internal guides.
User guides, of course can also be public facing: documentation of software products, web platforms, and data products.
Public documentation also has tremendous value to the team itself.
A good example of this is documentation for open source software where the information needs of a consumer are nearly the same as a developer or contributor.

Unlike design documentation, user guides are tightly integrated with a DM product's implementation and delivery.
Consequently, user guides are the most definitive references for what DM products are and how they work.
Their content will be used by scientists to create science.
These aspects make DM guides ideal primary references for scientific literature.
We enable this usage by making individual pages of guides :ref:`citeable <citeable>` entities (see :ref:`user-guide-citation`).

Technical Implementation
------------------------

All DM user guides are created as :ref:`multi-page Sphinx projects <formats-sphinx-guides>`.
This format facilitates a topic-based information architecture needed for comprehensive documentation projects.

Given that astronomers will use multiple DM products simultaneously (for example: Pipeline software, DataSpace, and data release), mandating the :ref:`multi-page Sphinx <formats-sphinx-guides>` format unifies the user experience across LSST’s astronomer-facing documentation.

Organization
------------

Every DM software, platform and data product has a corresponding user guide.

Rather than a monolithic DM documentation site, user documentation is partitioned according to the codebase or data product that each guide documents.
This approach keeps documentation close to the source so that documentation is versioned and delivered in step with the product itself.

The organization of user guides reflects, and even shapes, the perception of a DM product.
A project may have multiple user guides if the user audience is highly disjoint (for example a project may have an internal operations guide that is separate from a guide for consumers).
Multiple audiences can share a common user guide if their interests are similar.
This is common for open source APIs, like `pipelines.lsst.io`_.
Finally, multiple source repositories may share a common user guide project.
For example, the Science Pipelines consist of many Git repositories, yet are commonly documented at `pipelines.lsst.io`_ since we want to portray the Pipelines as a coherent entity.

Because user guides are websites, links allow independently produced user guides to still act like a consistent, monolithic resource.
Instead of duplicating or rephrasing content from a different guide, user guides always link to the most authoritative page.

Relation between user guides and design documentation
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Design documentation and user guides both refer to the same thing: a DM product.
Depending on the user guide's intended audience, design documentation may flow and be transformed into user guide content.
For example, the Science Pipelines user guide is an open source software project where users are also developers.
Successfully using and extending the LSST Science Pipelines may require documentation of implementation details originally described in design documentation.
Rather than maintain a parallel set of overlapping design and user documentation, in this case the design documents should be deprecated in favor of the user guide.

User Guide Working Groups
-------------------------

User guides are DM products, much like the software, platforms and datasets they accompany.
To oversee their delivery, each user guide project is managed by a corresponding working group.

User guide working groups are a mixture of subject matter experts (SMEs; usually the engineers, scientists, or managers directly involved in building a product) with the :ref:`Documentation Engineer <doceng>` who provides expertise in infrastructure, technical writing, and information architecture. These working groups are structured to solve key management challenges:

- User guides need strong cohesion and editorial curation, especially in their early development.
  A working group can provide consistent vision to a user guide project.
- DM products are highly technical, and their guides cannot be effectively produced by a separate technical writing team (see :ref:`people`).
  Subject matter experts (SMEs) must be involved in producing documentation for the products they build.
  SMEs in the working group ensure that the user guide is technically appropriate and complete.
  SMEs in the working group can also liaison with the rest of the engineering team to manage documentation contributions.
- Individual user guides exist within a larger environment of LSST documentation.
  The Documentation Engineer embedded in the working group develops the common infrastructure necessary for producing and publishing content.
  The Documentation Engineer also contributes knowledge in areas of information architecture and technical writing.
  Being shared across user guide working groups, the Documentation Engineer provides consistency and quality to the LSST documentation experience.

Each user guide working group’s composition will be unique and tuned to the project’s needs.
However, the following roles should be filled, possibly by the same or multiple people:

- **Subject matter expert** who leads the curriculum development of the user guide.
- **T/CAM** who is able to schedule effort for all engineers that may need to contribute documentation content.
- **The Documentation Engineer** who provides documentation infrastructure and provides advice on content (technical writing) and organization (information architecture).

Again, user guide working groups play a leadership role in documentation delivery.
The engineering and scientific teams who build a project will be responsible for producing most of a user guide's content, especially reference content.
The Documentation Engineer will also contribute critical (highly used) and complex content pieces.

Maintenance
-----------

User guides are continuously delivered in step with product development.

As APIs change or are added, software developers must update the corresponding reference documentation.
This process is convenient for developers since reference documentation is typically extracted from source code itself.
Reference documentation writing is expected to be part of all software development tickets.

Tutorial and conceptual documentation is more expensive to produce than reference documentation, and is typically written in tickets separate from software development.
API changes may break conceptual or tutorial documentation.
Where possible, the software development ticket’s scope should including fixing incompatibilities in the documentation.
Where the changes are too numerous, the outdated documentation should still be identified and excluded from documentation builds, and a follow-up documentation ticket should created and scheduled.

User guides and community.lsst.org
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

`Community.lsst.org`_ is DM’s primary long-form communication venue, both internally and with end-users.
Through conversation, original knowledge is naturally published on `Community.lsst.org`_.
Thanks to its open nature and search capabilities, `Community.lsst.org`_ can serve as an emergent knowledge base for LSST.

However, `Community.lsst.org`_ should not surpass any user guide as a primary source of information.
User guide working groups should monitor Community forum conversations.
When a question on the Community forum cannot be answered by the user guide, the working group should seek to distill the conversation’s information into the user guide.
Once the new user guide is updated, the working group should post a reply to the Community topic that links to the new content in the user guide.
This helps future readers find user guide content through the Community forum.
