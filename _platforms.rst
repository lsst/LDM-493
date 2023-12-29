.. _platforms:

Publishing Platforms
=====================

Three platforms facilitate publication and discovery of all DM documentation: LSST the Docs, DocuShare, and LSST DocHub.
Publishing all documentation in this system ensures consistency in presentation and discovery.
This section summarizes the functionality of these platforms for policies for their use.

.. _platforms-ltd:

LSST the Docs
-------------

LSST the Docs (LTD) is a platform for continuously publishing versioned documentation to the web.
LTD is more fully described in `SQR-006`_; please see that technote for details beyond the scope of this summary.

All DM documentation projects maintained in a version control system (specifically, Git with GitHub_) are published with LTD.
Other documents are published with :ref:`DocuShare, see below <docushare>`.

LSST the Docs's key features
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The following LTD features are key to the DM Documentation Architecture:

- **LTD is a service that hosts static websites,** that is, websites that do not require server-side rendering logic.
  Supporting only static websites ensures that LTD is reliable and scalable.
  This design decision also coerces documentation into a format that can be readily archived, which is important to DM's scientific legacy.

- **Each documentation project hosted by LTD is published from a unique subdomain of the lsst.io domain.**
  This helps to make human-friendly URLs.
  Audiences should see the ``lsst.io`` domain as a brand synonymous with LSST documentation.

- `LTD publishes multiple versions of a document <https://sqr-006.lsst.io/#versioned-documentation-urls>`_, each under a different URL path prefix.
  This feature integrates well with DM's Git-based development workflow where new documentation can be drafted on a branch.
  The DM team can review the rendered draft documentation without interfering with the production edition of the documentation.
  This feature also allows multiple versions of a document to be published to users, for example, to support multiple releases of a software product.

- **LTD integrates well with Git repositories and continuous integration (CI) services.**
  CI allows the final documentation product to be rendered automatically by software from relatively simple markup.
  As well, documentation generation can be coupled with science pipelines to enable automated and reproducible reporting in CI.
  For example, a Jupyter_ notebook can be run and published to LTD in the same CI job.

Requirements for compatibility with LSST the Docs
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

LTD imposes a few implementation constraints on DM documentation projects:

- The source for the published documentation must be hosted in a version controlled repository; typically this a Git repository hosted by GitHub.
  Documentation not hosted in GitHub is published directly from :ref:`DocuShare <docushare>`, see below.

- Each documentation project must be configured with a CI environment that builds and submits documentation whenever the underlying document source changes.
  Similarly, each documentation project requires software to transform documentation source into a static website.
  The SQuaRE team provides CI infrastructure and software to publish documentation in common source formats through LTD (see :ref:`formats`).

.. _docushare:

LSST Project DocuShare
----------------------

DocuShare is the LSST Project’s official document repository (see `LPM-51: Document Management Plan`_).

All :ref:`change controlled design documents <ldm>` (with LDM handles) are deposited in DocuShare once approved by the Change Control Board (CCB; see `LPM-19: Change Control Process`_), even if they are otherwise published through :ref:`LSST the Docs <platforms-ltd>`.
The LSST Project considers the version in DocuShare as the official version of a document that reflects a technical, schedule and budget baseline.
:ref:`LSST DocHub <platforms-dochub>` links to a document published in both :ref:`LSST the Docs <platforms-ltd>` and DocuShare, with DocuShare being denoted as the baselined version.

Although DocuShare will be used in conjunction with :ref:`LSST the Docs <platforms-ltd>`, some documentation formats are not managed in a version control system (Git) and thus are not publishable through :ref:`LSST the Docs <platforms-ltd>`.
These include documents from :ref:`'office' suites <office>`, such as Apple Pages, Google Docs, Dropbox Paper, Microsoft Word and Excel.
For such documents, DocuShare is the *only* publishing platform: a document only in Google Docs, for example, is not yet considered delivered.

.. _platforms-dochub:

LSST DocHub
-----------

LSST DocHub is a platform for discovering LSST documentation and other digital resources.
DocHub is both a metadata database and API, and also a set of user-facing web applications for searching and browsing LSST documentation.
All DM documentation is available through DocHub.

.. note::

   DocHub's design is ongoing and will be presented in upcoming technotes.

Requirements for compatibility with DocHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

To be listed in LSST DocHub, projects must be registered with DocHub.
Documentation projects hosted on GitHub have a DocHub-compatible metadata file residing in the project's Git repository.
Metadata is mirrored between DocHub's database and the metadata file stored in Git.
Documentation projects published exclusively though DocuShare are also registered in DocHub, though their metadata is editable through a web interface instead of a file.

.. note::

   The DocHub metadata format will be specified in an upcoming technote.

.. _citeable:

Citeable documentation
----------------------

LSST Data Management documentation is considered on par with scientific literature.
Being close to the implementation, continuously tested, and written by the collective team, DM’s technical documentation is the most accurate and scientifically useful reference for detailed aspects of the Data Management System.
To integrate with scientific literature, DM technical documentation is citeable according to the expectations of the astronomy community.
This section describes how DM documentation is made citeable through Digital Object Identifiers and registration with the `NASA Astrophysics Data System <ads>`_.

.. _doi:

Digital Object Identifiers
^^^^^^^^^^^^^^^^^^^^^^^^^^

Digital Object Identifiers (DOIs) are a standard for identifying digital artifacts.
A DOI is a universal identifier that can be resolved into a document’s URL.
The resolved URL can even be changed if the resources home on the web changes.
Thus a DOI acts as a permanent link to the artifact (in this case, a document).
In science, DataCite_ is a common DOI provider.
Although LSST could become a DataCite_ member and provision DOIs through DataCite_\ ’s API, institutions like LSST typically cannot guarantee the data longevity that is expected for DOIs.
Instead, science archives can permanently archive a copy of a document and provision a DOI through DataCite_ to that archived copy.
Zenodo_ is an example of such an archive operated by CERN for the science community.

As part of the continuous delivery process, DM documentation platforms automatically submit new or revised documents to a data archive and receive a DOI.
For multi-page documentation websites, each webpage is individually archived and given a DOI to prevent ambiguity in citations.
Published documents display this DOI as part of their citation instructions to readers.

Note that DOIs provisioned this way resolve to the data archive’s landing page rather than the website published on :ref:`LSST the Docs <platforms-ltd>`.
While this does ensure the long term integrity of LSST documentation in scientific literature, it does compromise the present-day usability of DOI-cited LSST documents.
To work around this, metadata published on the data archive landing page includes a pointer to the live document published on :ref:`LSST the Docs <platforms-ltd>`.

Archives, like Zenodo_, provide discovery services in addition to storing resources and provisioning DOIs.
While this is a nice feature, the DM Documentation Architecture does **not** rely upon the discovery tools of specific archives.
Instead, :ref:`DocHub <platforms-ltd>` is our in-house fully-fledge document discovery platform for LSST DM.
:ref:`DocHub <platforms-dochub>` affords DM flexibility and specialization in organizing and presenting documentation, and also insulates LSST from a specific archive.
Through DOIs, :ref:`DocHub <platforms-dochub>` points to documents in archives, in addition to :ref:`LSST the Docs <platforms-ltd>`.

NASA/SAO Astrophysics Data System
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

ADS_ is how the astronomical community discovers literature.
ADS_ is not a document hosting service, but rather a metadata and search service.
ADS_ lists LSST technical documentation with record pages that include bibliographic information and links pointing to the published documentation on :ref:`LSST the Docs <platforms-ltd>`.
The DM documentation platforms automatically submit new and updated DM documentation to ADS_ as part of the regular continuous delivery process.
Specifically, the documentation platforms cross-walk metadata already available through :ref:`LSST DocHub <platforms-dochub>` into the ADS submission schema (`ADS Tagged Format`_). 
