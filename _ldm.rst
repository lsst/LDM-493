.. _ldm:

Change-Controlled Design Documents
==================================

This section describes LSST Project change-controlled design documentation in the context of the Data Management Documentation Architecture.

Background
----------

Change-controlled design documentation defines the scope and budget of the Data Management System.
DM's change-controlled design documents carry "LDM" handles.
New and revised LDM documents are reviewed by the DM Technical Control Team (TCT), as described in `LDM-294: Data Management Organization and Charter`_, and submitted to the LSST Project `Change Control Board <LPM-19: Change Control Process>`_ for approval.
Overall, the role and policy surrounding change-controlled documentation is described in `LPM-19: Change Control Process`_.

Maintenance
-----------

Design documents must always be consistent with the system's implementation since they formally define the Data Management System's scope and budget.
If an implementation exceeds the envelope of the design document, a ticket should be raised for the project management team to review and reconcile the design and implementation.

Technical Implementation
------------------------

Per `LPM-51 <LPM-51: Document Management Plan>`_, all change-controlled documentation is deposited in :ref:`DocuShare <docushare>` upon acceptance by the `Change Control Board <LPM-19: Change Control Process>`_.

Some change-controlled documents are only available through :ref:`DocuShare <docushare>`, such as :ref:`word-processing files and spreadsheets <office>`, and all *classified* (non-public) documents.
In these cases, :ref:`DocHub <platforms-dochub>` indexes and links to the document from :ref:`DocuShare <docushare>`.
These documents are not be mirrored on :ref:`LSST the Docs <platforms-ltd>`.

DM members are encouraged to author documents in formats that can be version-controlled in Git and published by :ref:`LSST the Docs <platforms-ltd>` for improved collaboration.
:ref:`Single-page Sphinx <formats-sphinx-documents>` projects are preferred, and LaTeX documents published with the :ref:`Landing Page Framework <formats-alt>` are allowed secondarily.
The status of these Git-hosted documents in the `change control process <LPM-19: Change Control Process>`_ is reflected in its Git branches (and hence editions on LSST the Docs).
The ``master`` branch (and main :ref:`LSST the Docs <platforms-ltd>` edition) is reserved for change-controlled versions of a document.
Ticket and integration branches allow intermediate drafts of the document to be shared.
When a document is accepted by the `Change Control Board <LPM-19: Change Control Process>`_, that version is simultaneously merged to ``master`` and archived as a PDF to :ref:`DocuShare <DocuShare>`.

To facilitate citation in scientific literature, the accepted versions of un-classified documents are also deposited in a science data archive (such as Zenodo_) to be granted a :ref:`DOI <doi>`.

LSST DocHub is aware of each version of a document (as published on :ref:`LSST the Docs <platforms-ltd>`, on :ref:`DocuShare <docushare>`, and :ref:`Zenodo <doi>`) and usefully directs a user to the relevant version and citation information.
