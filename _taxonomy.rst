.. _taxonomy:

Documentation Taxonomy
======================

Data Management uses and produces multiple classes of documentation.
Each class fulfills a specific role, with a consistent management and technical process.

.. _taxonomy-outline:

Document classes
----------------

The classes of DM documentation are:

Requirements and interface control documentation (LPM, LSE)
   These documents specify functionality that the Data Management System must deliver to the Project.
   Similarly, **interface control documents** are agreements between subsystems on functionality that cross subsystem boundaries.
   The production of this documentation is described in `LPM-19: Change Control Process`_ and its management is described in `LPM-51: Document Management Plan`_.

Change-controlled DM design documentation (LDM)
   These documents define the **scope** and **budget** of Data Management work that meet the **requirements** and **interface control documentation**.
   DM work is expected to be consistent with these **design documents**.
   LDM document authors are responsible for updating design documentation whenever necessitated by revised project requirements, or by evolving implementation choices.
   Design documents must be approved by the Change Control Board (`LPM-19: Change Control Process`_) before becoming the new baseline.
   These documents are also governed by `LPM-51: Document Management Plan`_.
   See :ref:`ldm` for how change-controlled documents are handled by the Data Management Documentation Architecture.

Technical notes (DMTN, SQR)
   Technical notes are a standardized, durable, document series allowing useful information to be published on demand by any Data Management team member wishing to capture and share knowledge.
   Common uses of **technical notes** are descriptions of experiments with code or data, reviews of literature or technologies, usage notes, or technical documents that are too limited to trigger the change-control process.
   The primary audiences of **technical notes** are DM team members who build, maintain, or interface with a system and the science community.
   See :ref:`technotes` for details.

User Guides (DMG)
   These documentation products describe usage of DM software, platforms, and data products to end-users.
   Typically, end-users are astronomers in the scientific community.
   Some **user guides** may instead be considered internal, such as **operational guides** or **developer guides**.
   The most important aspect of **user guides** is that they are written intentionally for their intended audience.
   See :ref:`guides` for details.

Publications
   Publications---namely journal articles, and conference presentations and proceedings---speak directly to the science community.
   With respect to the Data Management Documentation Architecture, publications should be a synthesis of DM documentation products (Design Documents, Implementation Technical Notes, Technical Notes, and User Guides).
   Publications are described in `LPM-162: Project Publication Policy`_.

.. _taxonomy-flow:

Information flow down
---------------------

DM's documentation taxonomy facilitates a flow of information from research and design, to implementation, and finally to operations.

.. figure:: /_static/information_flow.svg
   :name: fig-information-flow
   :width: 60%

   Idealized information flow across documentation classes.

As :numref:`fig-information-flow` illustrates, the scope and functionality of the Data Management System is specified by Requirements Documents.
Design documents translate requirements into actionable designs and documentation of system implementations.
Designs are reflected in :ref:`change controlled design documents (LDM) <ldm>`, though details can be deferred to :ref:`technical notes (DMTN, SQR) <technotes>`.
:ref:`User guides <guides>` are written for end users using a combination of information from the design documentation and the implemented software itself.
Verification documentation is written as a consequence of testing activities.
Finally, scientific publications are written as a holistic synthesis of the entire Data Management System for the community.

Note that this is an *idealized* linear information flow. 
Software development work will spur new :ref:`technical notes <technotes>` that in turn create revise design documentation.
However, :numref:`fig-information-flow` shows the role of each document class in supporting the Data Management System in reporting research, documenting designs, and documenting for users.
