.. _formats:

Documentation Formats and Generators
====================================

This section describes the tools that builds the static documentation sites that are published with :ref:`LSST the Docs <platforms-ltd>`.

.. _formats-sphinx:

Sphinx
------

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

Single-page Sphinx projects implement the idea of a single page website.
Authors create new single page projects from a configurable template.
Each single-page Sphinx project is maintained in individual Git repositories and configured to publish automatically to :ref:`LSST the Docs <platforms-ltd>`.

Much of the design and logic for the format is centrally managed by the TechDocs team in separate Git repositories.
This makes single-page Sphinx projects manageable and consistent in form and function.
This technology stack is also shared with :ref:`multi-page Sphinx projects <formats-sphinx-guides>`, which are employed by :ref:`user guide <guides>` projects.

The single-page Sphinx format is recommended for technotes, implementation technotes, and change-controlled design documentation. As an alternative, these formats can be published through the landing page framework. Authoring and publishing through the single-page Sphinx format, however, creates a better reading experience due to features like deep hyperlinking to individual content objects and responsive design.

Archival and citation workflow
""""""""""""""""""""""""""""""

In relation to the `LSST Document Management Plan <LPM-51: Document Management Plan>`_, single-page Sphinx projects are DM's equivalent to the Project's `Document-9224`_ document template.
:ref:`LSST the Docs <platforms-ltd>` continuously publishes DM single-page Sphinx projects as websites.
When a single-page Sphinx project is delivered (by merging to the ``master`` Git branch), the documentation infrastructure creates a PDF version of the document that matches the form of `Document-9224`_ as much as is feasible.
This PDF is deposited in `DocuShare per `LPM-51 <LPM-51: Document Management Plan>`_.
Simultaneously, the PDF is also delivered to a science data archive to obtain a citeable :ref:`DOI <doi>`.

.. _formats-sphinx-guides:

Sphinx for user guides
^^^^^^^^^^^^^^^^^^^^^^

For user guides and multi-page sites.

.. _formats-alt:

Landing Pages for Alternative Formats
-------------------------------------

Not all documentation is produced as a :ref:`Sphinx project <formats-sphinx>`.
DM team members have shown a preference for alternative formats that have unique qualities like: built-in collaboration facilities, a heritage in scientific publication, or integration with software and data.
Developer efficiency is paramount, and the DM Documentation Architecture must not impede developers from using the best tools at hand.

But a heterogeneous mixture of authoring formats does not imply a heterogeneous delivery system.
All DM documentation, even those produced by alternative formats, must be delivered and published through the system discussed in :ref:`platforms`.
To achieve this, documents authored in alternative formats are shimmed and published through a *landing page* framework.

The Landing Page framework
^^^^^^^^^^^^^^^^^^^^^^^^^^

Landing pages are static websites published with LSST the Docs, and indexed by DocHub.
Irrespective of the original authoring tool, landing pages provide a consistent experience for consuming documentation.

Each landing page presents metadata to the reader, like title, authorship, summary, and links back to DocHub and related publications.
Alongside this metadata, the landing page presents the document either as a list of links to other pages or files, or the document itself as an on-page iframe to a PDF.\ [#fn-gh-publisher]_

.. [#fn-gh-publisher] The concept of displaying a PDF in an iframe alongside metadata on a static site is based on the `gh-publisher`_ project by Ewan Mellor.

Landing pages are hosted as GitHub_ repositories that contains and versions the document's content and metadata.
Although content on another platform (Confluence, Google Docs) can be linked to, the content in the GitHub_ repository must be complete and self-contained.

Similar to Sphinx-based documents, a continuous integration service, like Travis or Jenkins, publishes the landing page to LSST the Docs whenever the Git repository is updated.
Automations also make provisioning landing pages efficient.

The landing page generator, page design, and automations are provided by the SQuaRE team.

Workflows for specific formats
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

This section describes workflows for publishing common document formats through the landing page framework.

.. note::

   This section will be moved to a documentation user guide; likely in https://developer.lsst.io.

LaTeX documents
"""""""""""""""

LaTeX documents, being plain text, should be hosted and authored entirely on GitHub_.
This GitHub_ repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The continuous integration service renders the LaTeX source into a PDF that is displayed on the landing page.

Google documents
""""""""""""""""

Once a Google Doc is delivered, such as by closing a ticket, it must be exported into a GitHub_ repository.
This GitHub_ repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The Google Doc should be exported as HTML (specifically, a zipped file that includes images), which will be displayed on the landing page.
PDF and EPUB versions can also be exported for offline reading; these files will be linked from the landing page.

Subsequent revisions to the document should be made on Google Docs and re-exported to the GitHub_ repository in a new Git commit.

Confluence pages
""""""""""""""""

Once a Confluence page is delivered, such as by closing a ticket, it must be exported to a GitHub_ repository.
This GitHub_ repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The page should be exported as a PDF document using Confluence's native PDF export function.
This PDF will be displayed on the landing page.

Subsequent revisions to the Confluence page should be re-exported to the GitHub_ repository in a new Git commit.

Jupyter notebooks
"""""""""""""""""

Being JSON-based, Jupyter_ notebooks should be natively hosted in a GitHub_ repository.
This repository is named after the document's handle, and also hosts DocHub metadata and continuous integration configuration.

The continuous integration service should, ideally, run the notebooks themselves.
This ensures that the notebooks are reproducible, and not tied to an individual developer's environment.

The landing page will contain metadata about the notebooks, along with a summary description, and a table of contents linking to individual notebooks.
If there is only a single notebook, that notebook can be displayed on the landing page itself.
