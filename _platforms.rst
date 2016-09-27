.. _platforms:

Publishing Platforms
=====================

All Data Management documentation is formally published through a system of two platforms managed by DM: LSST the Docs, and LSST DocHub.
Publishing all documentation in this system ensures that documentation is consistent in presentation and discoverable.
This section reviews the functionality of these platforms.

.. _platforms-ltd:

LSST the Docs
-------------

LSST the Docs (LTD) is a platform for continuously publishing versioned documentation to the web.
LTD is formally described in `SQR-006`_; please see that technote for details beyond the scope of this summary.

All DM documentation projects are published with LTD.

LSST the Docs's features
^^^^^^^^^^^^^^^^^^^^^^^^

The following LTD features are key to the DM documentation architecture:

- **LTD is a service that hosts static websites,** that is, websites that do not require server-side rendering logic.
  Supporting only static websites assures that LTD is reliable and scalable.
  This design decision also coerces documentation into a format that can be readily archived, which is important to DM's scientific legacy.

- **Each documentation project hosted by LTD is published from a unique subdomain of the ``lsst.io`` domain.**
  This helps to make human-friendly URLs.
  Audiences should see the ``lsst.io`` domain as a brand synonymous with LSST documentation.

- `LTD publishes multiple versions of a document <https://sqr-006.lsst.io/#versioned-documentation-urls>`_, each under a different URL path prefix.
  This feature integrates well with DM's Git-based development workflow where new documentation can be drafted on a branch.
  The DM team can review the rendered draft documentation without interfering with the production edition of the documentation.
  This feature also allows multiple versions of a document to be published to users, for example, to support multiple releases of a software product.

- **LTD integrates well with Git repositories and continuous integration (CI) services.**
  CI allows the final documentation product to be rendered automatically by software from relatively simple markup.
  Even scientific computation pipelines can be performed in CI that enable reproducible scientific documentation.

Requirements for compatibility with LSST the Docs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

LTD imposes a few implementation constraints on DM documentation projects:

- The source for the published documentation must be hosted in a version controlled repository; typically this a Git repository hosted by GitHub.
  See :ref:`formats-alt` for the DM Documentation Architecture's approach to adapting documentation not natively to Git.

- Each documentation project must be configured with a CI environment that builds and submits documentation whenever the underlying document source changes.
  Similarly, each documentation project requires software to transform documentation source into a static website.
  The SQuaRE team provides CI infrastructure and software to publish documentation in common source formats through LTD (see :ref:`formats`).

.. _platforms-dochub:

LSST DocHub
-----------

LSST DocHub is a platform for discovering LSST documentation and other digital resources.
DocHub is both a metadata database and API, and also a set of user-facing web applications for searching and browsing LSST documentation.
All DM documentation must be available through DocHub.

.. note::

   DocHub's design will be presented in upcoming Technotes.

Requirements for compatibility with DocHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To be listed in LSST DocHub, projects must be registered with DocHub, and have a DocHub-compatible metadata file residing in the project's Git repository.

.. note::

   The DocHub metadata format will be specified in an upcoming Technote.
