.. _ldm:

Change-Controlled Design Documents
==================================

This section describes LSST Project change-controlled design documentation in the context of the Data Management Documentation Architecture.

.. todo:: Many project management-oriented details are needed in this section.

Role
----

Change-controlled design documentation defines the scope and budget of the Data Management System.
New and revised change-controlled documents are reviewed by the LSST Project `Change Control Board <LPM-19: Change Control Process>`_.
Overall, the role and policy surrounding change-controlled documentation is described in `LPM-19: Change Control Process`_.

Authorship
----------

.. todo::

   This section needs clarification.

   - What is the official process for organizing change-controlled documentation efforts?
   - Does the DM manager, DMLT, or Technical Control Team govern what change-controlled documents should be written?
   - How do individuals propose new change controlled documents?

Maintenance
-----------

Design documents must always be consistent with the system's implementation since they formally define the Data Management System's scope and budget.
If an implementation exceeds the envelope of the design document, a ticket should be raised for the project management team to review and reconcile the design and implementation.

Technical Implementation
------------------------

DM change-controlled design documentation is subject to `LPM-51: Document Management Plan`_.
The Data Management Documentation architecture implements the Project standards specified in `LPM-51 <LPM-51: Document Management Plan>`_, while also taking advantage of the usability and overall consistency of the DM documentation architecture's platforms and formats.

Change-controlled design documents are published as single-page Sphinx projects or through the landing page framework (to support Word and LaTeX documents).
These formats follow the form of Project documentation (typically Word and PDF documents).
Spreadsheets, which are commonly used for sizing models, can also be published through the landing page framework.

A document's status in the `change control process <LPM-19: Change Control Process>`_ is reflected in its Git branches (and hence editions on LSST the Docs).
The ``master`` branch (and main :ref:`LSST the Docs <platforms-ltd>` edition) is reserved for versions of a document.
Ticket and integration branches allow intermediate drafts of the document to be shared.

When a document is accepted by `Change Control Board <LPM-19: Change Control Process>`_, that version is simultaneously merged to ``master`` and archived.
For Project purposes, a PDF version of the document is archived in :ref:`DocuShare`.
To facilitate citation in scientific literature, the accepted version is also archived in a science data archive (such as Zenodo) to be granted a :ref:`DOI`.
LSST DocHub is aware of each version of a document (as published on :ref:`LSST the Docs <platforms-ltd>`, on :ref:`DocuShare`, and :ref:`Zenodo <doi>`) and usefully direct a user to the relevant version and citation information.
