:tocdepth: 1

.. sectnum::

.. note::

   **This draft is not under LSST change control.**

.. _summary:

Summary
=======

This document defines the Data Management Documentation Architecture: a system for authoring, maintaining, and publishing documentation.
Documentation serves the Data Management System from design, to implementation, and finally to operation.
By specifying management patterns and technologies, the goal of the Data Management Documentation Architecture is to ensure that documentation is available to the DM team and end-users when it is needed, in a format that are useful and appropriate.

The following aspects are covered by the Data Management Documentation Architecture:

- A :ref:`taxonomy of documentation classes <taxonomy>` that each fulfill specific roles.
- A platform for publishing all DM documentation (:ref:`LSST the Docs <publishing-ltd>`) and a platform for searching and browsing all DM documentation resources (:ref:`LSST DocHub <publishing-dochub>`).
- A :ref:`set of documentation formats <formats>` that maintain a consistent reading and discovery experience, while also promoting developer efficiency.
- Policies for organizing the production and maintenance of each class of documentation.

.. _taxonomy:

Documentation Taxonomy
======================

DM uses and produces multiple kinds of documentation and each fulfills a specific, unambiguous role.

.. _taxonomy-outline:

Document Classes
----------------

As an introduction, the classes of Data Management documentation are:

Requirements and Interface Control Documentation (LPM, LSE, ICD)
   These documents specify functionality that the Data Management System must deliver to the Project.
   Similarly, **Interface Control Documents** are agreements between subsystems on functionality that cross subsystem boundaries.
   LPM-FIXME authoritatively describes this documentation.

Design Documentation (LDM)
   These documents define the **scope** and **budget** of Data Management work that fulfills **Requirements** and **Interface Control Documentation**.
   Design Documents must be approved by the Change Control Board (CITE) before being considered actionable.
   All DM work must be consistent with these **Design Documents**.
   DM is responsible for updating design documentation whenever necessitated by revised project requirements, or by changing implementation realities.

Implementation Technical Notes (DMTN, SQR)
   These documents are design proposals for new systems, or design descriptions of existing systems.
   **Implementation Technical Notes** describe the *implementation* of functionality specified in **Design Documentation**.
   **Implementation Technical Notes** are not change-controlled, and can be created on demand.
   These documents are expected to be continuously updated (or deprecated) to reflect the state of a system.
   The primary audience of **Implementation Technical Notes** is DM team members who build, maintain or interface with a system.

Technical Notes (DMTN, SQR)
   Technical Notes are standardized, durable, documents that can be published on demand by Data Management team members to capture and share knowledge.
   Common uses of **Technical Notes** are descriptions of experiments with code or data, or reviews of literature or technologies.
   Technical Notes may propose designs and such documents will naturally become **Implementation Technical Notes** once they formally describe the design of a Data Management System.
   The primary audiences of **Technical Notes** are DM team members and the science community.

User Guides (DMG)
   These documentation products describe usage of DM software, platforms, and data projects to end-users.
   Typically, end-users are astronomers in the scientific community.
   Some **User Guides** may instead be considered internal, such as **Operational Guides** or **Developer Guides**.
   The most important aspect of *User Guides* is that they are written intentionally for their intended audience.
   Design and implementation details may be omitted from a user guide; instead a **User Guide** presents what the end-user should know to successfully operate or consume the software, data or platform produced by DM.

Publications
   Publications---namely journal articles, and conference presentations and proceedings---speak directly to the science community in the 
   Publications should be a synthesis of other DM documentation products (Design Documents, Implementation Technical Notes, Technical Notes, and User Guides).

.. _taxonomy-flow:

Information flow down
---------------------

The DM documentation taxonomy supports the LSST data management effort from research and design, to implementation, and finally operations.
:numref:`fig-information-flow` shows how information flows from design to implementation and operation documentation.

.. figure:: /_static/information_flow.svg
   :name: fig-information-flow
   :width: 60%

   Idealized information flow across documentation classes.

As :numref:`fig-information-flow` illustrates, the scope and functionality of the Data Management System is specified by Requirements Documents.
Design documents translate requirements into actionable designs and documentation of system implementations.
Designs originate in change controlled Design Documents (LDM), though details can be deferred to Implementation Technical Notes (DMTN).
In addition to requirements documents, Technical Notes inform design documentation.
User Guides are written for end users using a combination of information from the design documentation and the implemented software itself.
Verification documentation is written as a consequence of testing activities.
Finally, scientific publications are written as a holistic synthesis of the entire Data Management System for the community.

This is an *idealized* information flow. 
Software development work will spur new Technical Notes that in turn create new designs.
However, :numref:`fig-information-flow` shows the role of each document class in supporting the Data Management System in reporting research, documenting designs, and documenting for users.

.. _publishing:

Publishing Technologies
=======================

This section describes how documentation should be published.

.. _publishing-ltd:

LSST the Docs
-------------

- All documentation must be published as static sites through LTD.

.. _publishing-dochub:

LSST DocHub
-----------

- DocHub provides an index and search service for all LSST documentation.
- Documentation must use the DocHub metadata format.

.. _formats:

Documentation Formats and Generators
====================================

This section describes the tools that builds the static documentation sites that are published with LSST the Docs.

.. _formats-sphinx:

Sphinx
------

.. _formats-sphinx-documents:

Sphinx for design documents
^^^^^^^^^^^^^^^^^^^^^^^^^^^

For design documents and technotes.

.. _formats-sphinx-guides:

Sphinx for user guides
^^^^^^^^^^^^^^^^^^^^^^

For user guides and multi-page sites.

.. _formats-alt:

Landing Pages for Alternative Formats
-------------------------------------

Not all documentation is produced as Sphinx sites.
DM team members have shown a preference for alternative formats that have unique qualities like: built-in collaboration facilities, a heritage in scientific publication, or integration with software and data.
Developer efficiency is paramount, and the DM Documentation Architecture must not impede developers from using the best tools at hand.

But a heterogeneous mixture of authoring formats does not imply a heterogeneous delivery system.
All DM documentation, even those produced by other formats, must be delivered and published through the system discussed in :ref:`publishing`.
To achieve this, documents authored in alternative formats are shimmed and published through a *landing page* framework.

The Landing Page framework
^^^^^^^^^^^^^^^^^^^^^^^^^^

Landing pages are static websites published with LSST the Docs, and indexed by DocHub through the landing page framework.
Landing pages provide a consistent experience for consuming documentation.

Each landing page presents metadata to the reader, like title, authorship, summary, and links back to DocHub and related publications.
Alongside this metadata, the landing page presents the document either as a list of links to other pages or files, or the document itself as an on-page iframe to a PDF.\ [#fn-gh-publisher]_

.. [#fn-gh-publisher] The concept of displaying a PDF in an iframe alongside metadata on a static site is based on the `gh-publisher`_ project by Ewan Mellor.

Landing pages are hosted as GitHub repositories that contains and versions the document's content and metadata.
Although content on another platform (Confluence, Google docs) can be linked to, the content in the GitHub repository must be complete and self-contained.

Similar to Sphinx-based documents, a continuous integration service, like Travis or Jenkins, publishes the landing page and to LSST the Docs whenever the Git repository is updated.
Automations also make provisioning landing pages efficient.

The landing page generator, page design, and automations are provided by the SQuaRE team.

.. _gh-publisher: https://github.com/ewanmellor/gh-publisher

Workflows for specific formats
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section describes workflows for publishing common document formats through the landing page framework.

.. note::

   This section will be moved to a documentation user guide; likely in https://developer.lsst.io.

LaTeX documents
"""""""""""""""

LaTeX documents, being plain text, should be hosted and authored entirely on GitHub.
This GitHub repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration..

The continuous integration service renders the LaTeX source into a PDF that is displayed on the landing page.

Google documents
""""""""""""""""

Once a Google Doc is delivered, such as by closing a ticket, it must be exported into a GitHub repository.
This GitHub repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration..

The Google Doc should be exported as HTML (a zipped file that includes images), which will be displayed on the landing page.
PDF and EPUB versions can also be exported for offline reading; these files will be linked from the landing page.

Subsequent revisions to the document should be made on Google Docs, and re-exported to the GitHub repository in a new Git commit.

Confluence pages
""""""""""""""""

Once a Confluence page is delivered, such as by closing a ticket, it must be exported to a GitHub repository.
This GitHub repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration..

The page should be exported as a PDF document using Confluence's native PDF export function.
This PDF will be displayed on the landing page.

Subsequent revisions to the Confluence page should be re-exported to the GitHub repository in a new Git commit.

Jupyter notebooks
"""""""""""""""""

Being JSON-based, Jupyter notebooks should be natively hosted in a GitHub repository.
This repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The continuous integration service should, ideally, run the notebooks themselves.
This ensures that the notebooks are reproducible, and not tied to an individual developer's environment.

The landing page will contain metadata about the notebooks, along with a summary description, and a table of contents linking to individual notebooks.
If there is only a single notebook, that notebook can be displayed on the landing page itself.
