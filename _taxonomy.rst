.. _taxonomy:

Documentation Taxonomy
======================

Data Management uses and produces multiple classes of documentation.
Each class fulfills a specific role, and incorporates appropriate management and technical properties.

.. _taxonomy-outline:

Document classes
----------------

As an introduction, the classes of DM documentation are:

Requirements and Interface Control Documentation (LPM, LSE)
   These documents specify functionality that the Data Management System must deliver to the Project.
   Similarly, **Interface Control Documents** are agreements between subsystems on functionality that cross subsystem boundaries.
   The production of this documentation is described in `LPM-19: Change Control Process`_ and its management is described in `LPM-51: Document Management Plan`_.

DM Design Documentation (LDM)
   These documents define the **scope** and **budget** of Data Management work that fulfill the **Requirements** and **Interface Control Documentation**.
   All DM work must be consistent with these **Design Documents**.
   DM is responsible for updating design documentation whenever necessitated by revised project requirements, or by changing implementation realities.
   Design Documents must be approved by the Change Control Board (`LPM-19: Change Control Process`_) before being considered actionable.
   These documents are also subject to `LPM-51: Document Management Plan`_.

Implementation Technical Notes (DMTN, SQR)
   These documents are design proposals for new systems, or design descriptions of existing systems.
   **Implementation Technical Notes** describe the *implementation* of functionality specified in **Design Documentation**.
   **Implementation Technical Notes** are not change-controlled, and can be published on demand.
   These documents are expected to be continuously updated (or deprecated) to reflect the state of a system.
   The primary audience of **Implementation Technical Notes** is DM team members who build, maintain, or interface with a system.

Technical Notes (DMTN, SQR)
   Technical Notes are standardized, durable, documents that can be published on demand by Data Management team members to capture and share knowledge.
   Common uses of **Technical Notes** are descriptions of experiments with code or data, or reviews of literature or technologies.
   Technical Notes may propose designs and such documents will naturally become **Implementation Technical Notes** once they formally describe the design of a Data Management System.
   The primary audiences of **Technical Notes** are DM team members and the science community.

User Guides (DMG)
   These documentation products describe usage of DM software, platforms, and data products to end-users.
   Typically, end-users are astronomers in the scientific community.
   Some **User Guides** may instead be considered internal, such as **Operational Guides** or **Developer Guides**.
   The most important aspect of *User Guides* is that they are written intentionally for their intended audience.
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
Designs originate in change controlled Design Documents (LDM), though details can be deferred to Implementation Technical Notes (DMTN).
In addition to requirements documents, Technical Notes inform design documentation.
User Guides are written for end users using a combination of information from the design documentation and the implemented software itself.
Verification documentation is written as a consequence of testing activities.
Finally, scientific publications are written as a holistic synthesis of the entire Data Management System for the community.

Note that this is an *idealized* linear information flow. 
Software development work will spur new Technical Notes that in turn create revise design documentation.
However, :numref:`fig-information-flow` shows the role of each document class in supporting the Data Management System in reporting research, documenting designs, and documenting for users.
