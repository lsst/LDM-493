.. _purpose:

Purpose and Scope
=================

The Data Management Documentation Architecture defines LSST Data Management's technical process for authoring, maintaining, and publishing documentation.
This includes design documentation, technical implementation documentation, and operational documents such as user guides.
By specifying management patterns and technologies, the goal of the Data Management Documentation Architecture is to ensure that documentation is available to the DM team and end-users when it is needed, in formats that are useful and appropriate.

The Data Management Documentation Architecture covers:

- A :ref:`taxonomy of documentation classes <taxonomy>` describing how each type of document fulfills specific roles.
- Platforms for publishing all DM documentation (:ref:`LSST the Docs <platforms-ltd>`), making documentation discoverable (:ref:`LSST DocHub <platforms-dochub>`), and ensuring documentation is :ref:`citeable <citeable>`.
- A :ref:`set of documentation formats <formats>` that maintain a consistent reading and discovery experience, while also promoting developer efficiency.
- Policies for organizing the production and maintenance of each class of documentation.

This Architecture does **not** cover ad-hoc written communication channels.
The following are examples of subjects beyond the scope of this document:

- Communications platforms (e.g., the `LSST Community forum`, Slack).
  See `SQR-011`_.
- Meeting notes on Confluence.
  See `SQR-011`_.
- Confluence wiki pages being used to coordinate work.
  See `SQR-011`_.
- Requests for Comment (RFC) and Discussion (RFD).
  See the `DM Developer Guide <https://developer.lsst.io/processes/decision_process.html>`__.
- Presentations.

This Architecture applies only to Data Management documentation projects.
Policies for LSST Project documentation (including documents with "LPM" and "LSE" handles) are specified in `LPM-51: Document Management Plan`_, policies for scientific publications are documented in `LPM-162: Project Publication Policy`_.
