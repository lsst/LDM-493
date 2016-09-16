:tocdepth: 1

.. sectnum::

.. note::

   **This draft is not under LSST change control.**

.. _summary:

Summary
=======

This document defines the Data Management Documentation Architecture: a system for authoring, maintaining, and publishing documentation.
Documentation serves the Data Management System from design, to implementation, and finally to operation.
By specifying management patterns and technologies, the goal of the Data Management Documentation Architecture is to ensure that documentation is available to the DM team and end-users when it is needed, in a format that are useful and appropriate.

The following aspects are covered by the Data Management Documentation Architecture:

- A :ref:`taxonomy of documentation classes <taxonomy>` that each fulfill specific roles.
- A platform for publishing all DM documentation (:ref:`LSST the Docs <publishing-ltd>`) and a platform for searching and browsing all DM documentation resources (:ref:`LSST DocHub <publishing-dochub>`).
- A :ref:`set of documentation formats <formats>` that maintain a consistent reading and discovery experience, while also promoting developer efficiency.
- Policies for organizing the production and maintenance of each class of documentation.

.. _taxonomy:

Documentation Taxonomy
======================

DM uses and produces multiple kinds of documentation and each fulfills a specific, unambiguous role.

.. _taxonomy-outline:

Document Classes
----------------

As an introduction, the classes of Data Management documentation are:

Requirements and Interface Control Documentation (LPM, LSE, ICD)
   These documents specify functionality that the Data Management System must deliver to the Project.
   Similarly, **Interface Control Documents** are agreements between subsystems on functionality that cross subsystem boundaries.
   LPM-FIXME authoritatively describes this documentation.

Design Documentation (LDM)
   These documents define the **scope** and **budget** of Data Management work that fulfills **Requirements** and **Interface Control Documentation**.
   Design Documents must be approved by the Change Control Board (CITE) before being considered actionable.
   All DM work must be consistent with these **Design Documents**.
   DM is responsible for updating design documentation whenever necessitated by revised project requirements, or by changing implementation realities.

Implementation Technical Notes (DMTN, SQR)
   These documents are design proposals for new systems, or design descriptions of existing systems.
   **Implementation Technical Notes** describe the *implementation* of functionality specified in **Design Documentation**.
   **Implementation Technical Notes** are not change-controlled, and can be created on demand.
   These documents are expected to be continuously updated (or deprecated) to reflect the state of a system.
   The primary audience of **Implementation Technical Notes** is DM team members who build, maintain or interface with a system.

Technical Notes (DMTN, SQR)
   Technical Notes are standardized, durable, documents that can be published on demand by Data Management team members to capture and share knowledge.
   Common uses of **Technical Notes** are descriptions of experiments with code or data, or reviews of literature or technologies.
   Technical Notes may propose designs and such documents will naturally become **Implementation Technical Notes** once they formally describe the design of a Data Management System.
   The primary audiences of **Technical Notes** are DM team members and the science community.

User Guides (DMG)
   These documentation products describe usage of DM software, platforms, and data projects to end-users.
   Typically, end-users are astronomers in the scientific community.
   Some **User Guides** may instead be considered internal, such as **Operational Guides** or **Developer Guides**.
   The most important aspect of *User Guides* is that they are written intentionally for their intended audience.
   Design and implementation details may be omitted from a user guide; instead a **User Guide** presents what the end-user should know to successfully operate or consume the software, data or platform produced by DM.

Publications
   Publications---namely journal articles, and conference presentations and proceedings---speak directly to the science community in the 
   Publications should be a synthesis of other DM documentation products (Design Documents, Implementation Technical Notes, Technical Notes, and User Guides).

.. _taxonomy-flow:

Information flow down
---------------------

The DM documentation taxonomy supports the LSST data management effort from research and design, to implementation, and finally operations.
:numref:`fig-information-flow` shows how information flows from design to implementation and operation documentation.

.. figure:: /_static/information_flow.svg
   :name: fig-information-flow
   :width: 60%

   Idealized information flow across documentation classes.

As :numref:`fig-information-flow` illustrates, the scope and functionality of the Data Management System is specified by Requirements Documents.
Design documents translate requirements into actionable designs and documentation of system implementations.
Designs originate in change controlled Design Documents (LDM), though details can be deferred to Implementation Technical Notes (DMTN).
In addition to requirements documents, Technical Notes inform design documentation.
User Guides are written for end users using a combination of information from the design documentation and the implemented software itself.
Verification documentation is written as a consequence of testing activities.
Finally, scientific publications are written as a holistic synthesis of the entire Data Management System for the community.

This is an *idealized* information flow. 
Software development work will spur new Technical Notes that in turn create new designs.
However, :numref:`fig-information-flow` shows the role of each document class in supporting the Data Management System in reporting research, documenting designs, and documenting for users.

.. _publishing:

Publishing Technologies
=======================

This section describes how documentation should be published.

.. _publishing-ltd:

LSST the Docs
-------------

- All documentation must be published as static sites through LTD.

.. _publishing-dochub:

LSST DocHub
-----------

- DocHub provides an index and search service for all LSST documentation.
- Documentation must use the DocHub metadata format.
