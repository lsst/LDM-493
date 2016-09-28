.. _implementation-technotes:

Implementation Technical Notes
==============================

This section describes implementation technical notes.
Implementation technotes work much like :ref:`general technotes <technotes>`, except that they are geared toward detailed design documentation.
The close relationship between an implementation technote and the resulting code base and :ref:`user guide <guides>` requires special maintenance procedures to avoid documentation duplication.

Role
----

Change-controlled design documents often only specify broad functionality and baseline requirements.
Many design decisions are required to translate a baseline design into an implementation.
Implementation technotes are a low-overhead means of creating and sharing design information.  

Since implementation technotes operate within the scope of an existing change-controlled document, implementation technotes can be created and published on-demand.

The formalism of implementation technotes relates to how they are published and maintained.
Previously, low-level DM design documentation was spread across media like Confluence pages (in both personal and DM spaces) and personal Google Docs.
Being aware that design documentation existed relied upon being given a link specifically by the author.
This silo approach to design documentation reduced the efficiency of DM as a distributed team.
Another concern is that Google Docs or Confluence pages might be listed as products of a JIRA ticket.
Documents delivered this way are difficult to manage at scale and can be easily misplaced or forgotten.

Implementation technotes solve this delivery problem by providing a lightweight process for publishing documentation with :ref:`LSST the Docs <platforms-ltd>` and being discoverable through :ref:`LSST DocHub <platforms-dochub>`.
In doing so, design knowledge created in the course of DM work is integrated into the larger DM Documentation Architecture.

Technical Implementation
------------------------

Implementation technotes document ideas through narratives.
Thus they are presented as :ref:`single-page sphinx projects <formats-sphinx-documents>`, or as documents published in a :ref:`landing page framework <formats-alt>`.
The :ref:`landing page framework <formats-alt>` allows authors to use their favored collaborative writing platforms, while still publishing that content in a durable manner that can be consistently discovered and read by the DM team.

Like :ref:`general technotes <technotes>`, implementation technotes are published with DMTN or SQR document handles.

Authorship
----------

Like :ref:`general technotes <technotes>`, implementation technical notes are intellectual contributions by individual DM team members.
Pull requests by non-authors should always be reviewed by the original authors since, in most cases, the original authors are responsible for the described system's implementation.

Maintenance
-----------

Implementation technotes are intended to be a lightweight documentation class.
The structure and process that this class *does* enforce are to assist the DM team in discovering and referring to detailed design documentation.
Since implementation technotes are likely to be authored outside GitHub_, in Confluence or Google Doc formats, authors should *at least* publish their document when a ticket has closed.
Confluence pages or Google Documents are not acceptable products of a design ticket.

Implementation technote authors are free, and encouraged, to update an implementation technote after its initial publication whenever the design changes.

The utility of implementation technotes is only to direct the development of the Data Management System.
An implementation technote is not documentation for the **implemented** product; that responsibility lies with the product’s :ref:`user guide <guides>`.
To avoid having two documents attempt to authoritatively describe a product, implementation technotes should be gradually deprecated.
The suggested procedure is:

1. Designs are originally written in implementation technical notes. 
2. As aspects of the design are implemented, documentation should be migrated into the product’s user guide.
   This migration requires re-writing the content's tone, as well as re-organizing the content from a single-page narrative to a multi-topic format for the user guide.
   Once migrated, sections or paragraphs of the implementation technote should be marked as 'deprecated.'
   The deprecation notices include links to the equivalent documentation in the :ref:`user guide <guides>`.
3. Once a design document or implementation technote is fully migrated, it should be marked as deprecated in its metadata.
   This alerts consumers that the design document is no longer being maintained, and that the implementation may have potentially diverged.

This deprecation procedure is a key feature that distinguishes implementation technical notes from general technotes that capture ideas not directly tied to a DM product.
