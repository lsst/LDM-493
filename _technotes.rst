.. _technotes:

Technical Notes
===============

This section describes technical notes (technotes), which are flexible, self-contained documents.

.. note:: This section supersedes `SQR-000: The LSST DM Technical Note Platform`_. 

Role
----

Technotes are containers for *ideas*, rather than documentation for products.
This distinguishes technotes from user guides.

Technotes can be used to describe results from an experiment (like a scientific paper).
They can also be used to investigate technologies or design decisions and suggest a plan.
Technotes are primarily a product *for* DM, not a product *by* DM.
Through technotes, DM captures its research effort to make better implementation choices. In :numref:`fig-information-flow`, technotes are shown as inputs to design documentation in DM's idealized information flow. 

Another use for technotes is to provide high level overviews of shipped products, pitched primarily to external audiences.
These narratives are like the blog posts that tech companies write about their products, and are opportunities to explain the philosophy and design reasoning of DM products.
Often the tone of such narratives does not fit in user documentation, but works well in a technote article.

Overall, technotes are catch-all containers for narratives that are not :ref:`design documentation <ldm>` nor :ref:`user guides <guides>`.

Technotes are created and published on-demand by DM team members.
There is no approval process for technotes other than the standard DM code review for ticketed work.
Through this lack of administrative process, and infrastructural automations (see below), the bar for creating a technote is intentionally low.
This is important since capturing more information in a standardized technote format increases the proportion of DM knowledge that is accessible through :ref:`DocHub <platforms-dochub>`.

Technical Implementation
------------------------

:ref:`Single-page Sphinx <formats-sphinx-documents>` projects are the recommended format for technotes.
This format publishes natively to the web, making these documents highly useable in browsing and information hunting contexts.
The single-page format is also straightforward to reduce into static, archived documents (like PDFs) that can be cited in scientific literature.
The single page format also emulates scientific papers, and is appropriate for a narrative format.

Where it is more convenient to the author, technotes can also be published through alternative formats (such as LaTeX_ articles and Jupyter_ Notebook collections) using the :ref:`Landing Page Framework <formats-alt>`.
Nonetheless, Sphinx projects are recommended over LaTeX projects for a better online reading experience.

Authorship
----------

Technotes have explicit author lists, similar to academic papers.
This property raises the profile of individual intellectual contributions, which is important for DM team members who are writing fewer academic papers, yet want to maintain a CV.
Associating individuals with technote authorship also builds trust in the content: technote authors are subject matter experts sharing knowledge with DM.

Because technote authors are intellectually responsible for their content, DM team members should always involve the original authors when making a pull request against a technote that is not theirs.

Maintenance
-----------

Technotes *do not need* to be updated.
Akin to a traditional paper publication, a technote implicitly represents a state of knowledge at the time of publication.
Creating a technote does not oblige the authors to continually re-assess and update the document.

When significant changes occur, authors can add metadata and other notices.
For example, if content from a technote has been migrated into a different document (upstream to a design document, or downstream to a user guide), the technote can be marked as deprecated.

A technote *can* be updated freely by the authors.
If new information needs to be documented that fits an existing technotes’ scope, that existing technote can be updated rather than create an entirely new document.
This approach reduces the amount of legacy documentation.
Archival tools and the :ref:`LSST the Docs <platforms-ltd>` publishing platform maintain older versions of technotes for historical interest.
