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

.. _citeable:

Citeable documentation
----------------------

LSST Data Management documentation should be considered scientific literature.
Being close to the implementation, continuously tested, and written by the collective team, DM’s technical documentation should be the most accurate and scientifically useful references for detailed aspects of the Data Management System.
To integrate with scientific literature, DM technical documentation must be citeable resources according to the expectations of the astronomy community and the LSST Project.
This section describes how DM documentation is made citeable through Digital Object Identifiers, registration with the NASA Astrophysics Data System, and storage on the LSST Project DocuShare.

Digital Object Identifiers
^^^^^^^^^^^^^^^^^^^^^^^^^^

Digital Object Identifiers (DOIs) are a standard for identifying digital artifacts.
A DOI is a universal identifier that can be resolved into a document’s URL.
The resolved URL can even be changed if the resources home on the web changes.
Thus a DOI acts as a permanent link.
In science, Datacite is a common DOI provider.
Although LSST could become a Datacite member and provision DOIs through Datacite’s API, institutions like LSST typically cannot guarantee the data longevity that is expected for DOIs.
Instead, science archives can permanently archive a copy of a document and provision a DOI through Datacite to that archived copy.
Zenodo is an example of such an archive operated by CERN for the science community.

As part of the continuous delivery process, DM documentation platforms automatically submit new or revised documents to a data archive and receive a DOI.
For multi-page documentation websites, each webpage is individually archived and given a DOI to prevent ambiguity in citations.
Published documents display this DOI as part of their citation instructions to readers.

Note that DOIs provisioned this way resolve to the data archive’s landing page rather than the website published on LSST the Docs.
While this does ensure the long term integrity of LSST documentation in scientific literature, it does compromise the present-day usability of DOI-cited LSST documents.
To work around this, metadata published on the data archive landing page includes a pointer to the live document published on LSST the Docs.

Archives, like Zenodo, provide discovery services in addition to storing resources and provisioning DOIs.
While this is good, the DM Documentation Architecture does not rely upon the discovery tools of specific archives.
Instead, DocHub is the fully-fledge document discovery platform for LSST DM.
DocHub affords DM flexibility and specialization in organizing and presenting documentation, and also insulates LSST from a specific archive.
Through DOIs, DocHub points to documents in archives, in addition to LSST the Docs.

NASA/SAO Astrophysics Data System
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ADS is how the astronomical community discovers literature.
ADS is not a document hosting service, but rather a metadata and search service.
ADS lists LSST technical documentation with record pages that include bibliographic information and links pointing to the published documentation on LSST the Docs.
The DM documentation platforms automatically submit new and updated DM documentation to ADS as part of the regular continuous delivery process.
Specifically, the documentation platforms cross-walk metadata already available through LSST DocHub into the ADS submission schema (`ADS Tagged Format`_). 

LSST Project DocuShare
^^^^^^^^^^^^^^^^^^^^^^

DocuShare is the LSST Project’s official document repository (see `LPM-51: Document Management Plan`_).
Design Documents (with LDM handles) must be deposited in DocuShare once approved by the Technical Control Team (TCT; see `LPM-19: Change Control Process`_).
The LSST Project considers the version in DocuShare as the official version of a document.
Such documents are also published to LSST the Docs and made available through LSST DocHub.
