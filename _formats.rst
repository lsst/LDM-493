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

Not all documentation is produced as a Sphinx_ project.
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
