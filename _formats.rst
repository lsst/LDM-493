.. _formats:

Documentation Formats and Generators
====================================

This section describes the tools used to build static documentation sites that are published with :ref:`LSST the Docs <platforms-ltd>` and :ref:`DocuShare <docushare>`.

.. _formats-sphinx:

Sphinx
------

Sphinx_ is the first-class documentation generator for LSST Data Management.
All :ref:`user guides <guides>` are produced with Sphinx.
Although not required, other documentation classes should be preferably produced with Sphinx as well.

Some of the reasons Sphinx was chosen as DM's documentation generator include:

- Sphinx and reStructuredText are implemented in Python, which matches the DM technology stack.
- Since reStructuredText is plain text, Sphinx projects integrate well with Data Management's Git-based development workflow.
- Through Python APIs, both Sphinx and the reStructuredText markup language are thoroughly extensible, giving the :ref:`Documentation Engineer <doceng>` opportunity to build solutions that both improve developer efficiency, and improve the quality of documentation.
  For example, Sphinx is able to introspect Python code to build API reference documentation.

The DM Documentation Architecture uses two types of Sphinx projects, depending on the document class: :ref:`single-page projects <formats-sphinx-documents>` for narrative documents and :ref:`multi-page projects <formats-sphinx-guides>` for user guides.

.. _formats-sphinx-documents:

Single-page Sphinx projects
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Narrative-based information architecture
""""""""""""""""""""""""""""""""""""""""

The single-page website is an excellent format for narratives that coherently explore a single topic or idea.
By adopting the form of an academic article organized linearly by section headers, a single-page website is readily :ref:`citeable <citeable>` (a single URL, and thus a single :ref:`DOI <doi>`) and :ref:`archivable <docushare>` (a page can be transformed into a self-contained artifact like a PDF).
At the same time, a single page website *is a website* and benefits from native hyperlinks, exposure to search engines, and a visual presentation that adapts to the reader’s context (responsive design).

Implementation
""""""""""""""

Single-page Sphinx projects implement the idea of a single-page website.
Authors create new single-page Sphinx projects from a configurable template.
Each single-page Sphinx project is maintained in individual Git repositories and configured to publish automatically to :ref:`LSST the Docs <platforms-ltd>`.

Much of the design and logic for the format is centrally managed in separately from content in Git repositories maintained by the Documentation Engineer.
This makes single-page Sphinx projects manageable and consistent in form and function.
This technology stack is also shared with :ref:`multi-page Sphinx projects <formats-sphinx-guides>`, which are employed by :ref:`user guide <guides>` projects.

The single-page Sphinx format is recommended for :ref:`technotes <technotes>` and :ref:`change-controlled design documentation <ldm>`.
Alternatively, these document classes can be published through the :ref:`landing page framework <formats-alt>`.
Authoring and publishing through the single-page Sphinx format, however, creates a better reading experience due to features like deep hyperlinking to individual content objects and responsive design.

.. _formats-sphinx-document-archival:

Archival and citation workflow
""""""""""""""""""""""""""""""

In relation to the `LSST Document Management Plan <LPM-51: Document Management Plan>`_, single-page Sphinx projects are DM's equivalent to the Project's `Document-9224`_ document template.
:ref:`LSST the Docs <platforms-ltd>` continuously publishes DM single-page Sphinx projects as websites.
When a single-page Sphinx project is delivered (by merging to the ``master`` Git branch), the documentation infrastructure creates a PDF version of the document that matches the form of `Document-9224`_ as much as is feasible.
This PDF is deposited in `DocuShare per LPM-51 <LPM-51: Document Management Plan>`_.
Simultaneously, the PDF is also delivered to a science data archive to obtain a citeable :ref:`DOI <doi>`.

.. _formats-sphinx-guides:

Sphinx for user guides
^^^^^^^^^^^^^^^^^^^^^^

Topic-based information architecture
""""""""""""""""""""""""""""""""""""

The purpose of a :ref:`user guide <guides>` is to introduce users to a product, teach users how to use a product, and be a reliable reference for every relevant feature and behavior in a product.
As such, :ref:`user guides <guides>` are a constellation of marketing material, tutorials, conceptual guides, and references, as appropriate.
This type of documentation is markedly different from the narrative documentation that is supported by the :ref:`single-page Sphinx format <formats-sphinx-documents>` (and the :ref:`landing page framework <formats-alt>`).
:ref:`User guides <guides>` must be implemented as multi-page websites, where each page covers a different topic type. 

*Every Page is Page One* [#fn-eppo]_ is our guiding information architecture for documentation projects that DM implements in our user documentation.
In an Every Page is Page One (EPPO) architecture, every page of documentation is a self-contained topic.
Topics link to each other based on subject affinities to form a bottom-up information architecture (as opposed to a strictly top-down hierarchy that is established by narratives like :ref:`single-page Sphinx projects <formats-sphinx-documents>` and other report-like documents).
The EPPO architecture acknowledges that users will create their own curriculum for learning a product, and that a linear hierarchy is not well-suited for this.

EPPO also benefits DM documentation development and maintenance.
Each documentation page is self-contained, making documentation work easier to plan and schedule.
Interlinked, self-contained pages also naturally reduce content duplication and ease maintenance.

.. [#fn-eppo] Baker, Mark (2013). *Every Page is Page One: Topic-Based Writing for Technical Communication and the Web*. Laguna Hills: XML Press.

Implementation
""""""""""""""

Documentation in the EPPO-type information architecture exists natively on the web.
The multi-page Sphinx format is how DM implements all user documentation, without exception.
Each :ref:`user guide <guides>` project is embedded in the code repository of the product it documents.
In conjunction with :ref:`LSST the Docs <platforms-ltd>` continuous versioned documentation delivery, this arrangement ensures that documentation is always versioned in step with the product.
Indeed, API reference documentation is typically extracted from the code itself.
Keeping documentation close to the code also improves the workflow of engineers who contribute documentation.

All multi-page Sphinx projects share common infrastructure to maintain consistency in form and function.
This infrastructure is also shared with single-page Sphinx projects.

Runnable content
""""""""""""""""

Examples and tutorials in user guides are engineered to be tested as part of the product’s continuous integration.
This ensures that documentation and implementation are kept in sync.
Tutorials are integrated in a way that allows the user to easily run and remix example code.
This may be done with technologies like Jupyter_ notebooks and the LSST science user interface itself.

.. _user-guide-citation:

Citeable content
""""""""""""""""

Since user documentation is the most detailed documentation of implemented DM products (thanks to its proximity to the code), user documentation is likely the most useful scientific reference.
As described above, user guides are implemented as assemblies of self-contained topics.
The individual topic (a page at a single URL) is therefore the most precise citeable entity.
Citations to a user guide, in general, do not help a reader find the relevant information.

To facilitate topic-level citation, individual pages of multi-page Sphinx sites are archived independently.
Each page is rendered into a self-contained PDF (:ref:`single-page Sphinx sites <formats-sphinx-document-archival>`) and deposited in a science data archive to be granted a :ref:`DOI <doi>`.
Each page, as published on :ref:`LSST the Docs <platforms-ltd>`, displays its DOI with citation instructions for researchers.

DM documentation infrastructure automates the workflow described above.
Since it is an expensive workflow, a multi-page Sphinx site is only archived as part of a merge to the documentation’s ``master`` branch (and designated maintenance branches for releases).

.. _formats-alt:

Landing Pages for Alternative Formats
-------------------------------------

Although Sphinx is the preferred DM documentation format, not all Git-backed documentation is produced as a :ref:`Sphinx project <formats-sphinx>`.
Some documents are written in LaTeX for legacy reasons or to be compatible with scientific publishers.
Jupyter_ notebooks are also being used for producing documents that are tightly integrated with code and data.

Since they are managed in Git, these document formats are eligible for being published as static websites with :ref:`LSST the Docs <platforms-ltd>`.
However, LaTeX documents, Jupyter_ notebooks, and similar formats, do not necessarily create polished websites that have the look and feel of LSST documentation.
Thus the DM Documentation Architecture shims these formats through a *landing page framework.*

The Landing Page framework
^^^^^^^^^^^^^^^^^^^^^^^^^^

Landing pages are static websites published with :ref:`LSST the Docs <platforms-ltd>`, and indexed by :ref:`DocHub <platforms-ltd>`.
Irrespective of the original authoring tool, landing pages provide a consistent experience for consuming documentation.

Each landing page presents metadata to the reader, like title, authorship, summary, and links back to :ref:`DocHub <platforms-ltd>` and related publications.
Alongside this metadata, the landing page presents the document either as a list of links to other pages or files, or the document itself as an on-page iframe to a PDF.\ [#fn-gh-publisher]_

.. [#fn-gh-publisher] The concept of displaying a PDF in an iframe alongside metadata on a static site is based on the `gh-publisher`_ project by Ewan Mellor.

Landing pages are hosted as GitHub_ repositories that contains and versions the document's content and metadata.
Similar to Sphinx-based documents, a continuous integration service, like Travis or Jenkins, publishes the landing page to `LSST the Docs <platforms-ltd>` whenever the Git repository is updated.
Automations also make provisioning landing pages efficient.

The landing page generator, page design, and automations are provided by the SQuaRE team.

Workflows for specific formats
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section describes workflows for publishing common document formats through the landing page framework.

.. note::

   This section will be moved to a documentation user guide; likely in https://developer.lsst.io.

.. _latex:

LaTeX documents
"""""""""""""""

LaTeX documents, being plain text, are hosted and authored entirely on GitHub_.
This GitHub_ repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The continuous integration service renders the LaTeX source into a PDF that is displayed on the landing page.

.. _jupyter-notebooks:

Jupyter notebooks
"""""""""""""""""

Being JSON-based, Jupyter_ notebooks are natively hosted in a GitHub_ repository.
This repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The continuous integration service runs the notebooks themselves.
This ensures that the notebooks are reproducible, and not tied to an individual developer's environment.

The landing page contains metadata about the notebooks, along with a summary description, and a table of contents linking to individual notebooks.
If there is only a single notebook, that notebook can be displayed on the landing page itself.

Formats not Managed in Git
--------------------------

All formats previously in this section are published with :ref:`LSST the Docs <platforms-ltd>`, as they are managed in a version control system (specifically, Git with GitHub_).
This section describes policies for formats not publishable with :ref:`LSST the Docs <platforms-ltd>`.

.. _office:

Office documents
^^^^^^^^^^^^^^^^

Office documents are those produced by office and word processing suites, either in native applications (such as Microsoft Word and Excel, and Apple Pages) or in the cloud (such as Google Docs and Dropbox Paper).
These formats may be used for :ref:`change-controlled (LDM) documents <ldm>`.
Note that such documents are only published though DocuShare.
In DocuShare, both a PDF rendering and an editable version is included in the document's stack.

Authors can register new office documents with DocHub so that their existence is known to the DM team, even before being officially delivered to DocuShare.
DocHub can link to the document's read-only preview if available from the cloud application.
However, note that such draft documents are not stored by the LSST Project, and thus are not considered to be delivered.
For example, a JIRA ticket may not be closed if it merely links to a Google Docs page, or an attached Word file, rather than a DocuShare deposition.

.. _confluence:

Confluence pages
^^^^^^^^^^^^^^^^

Some authors may choose to draft documents in LSST's Confluence wiki to take advantage of its commenting features and online editing.
A Confluence page is not considered a delivered document, however.
The authors must convert the wiki page into a format accepted for the document's class.
A technical note must be converted into a single-page Sphinx project, and change controlled documents may be converted into either single-page Sphinx projects or office documents.
Once converted, authors must delete the original wiki page.

While the documented is being drafted, authors can register the document with DocHub to make it discoverable by the DM team.
The document is only considered delivered, however, once the Confluence page has been converted and published in either DocuShare or LSST the Docs.
A JIRA ticket, for example, may not be closed with a link to a Confluence page as evidence of documentation.
