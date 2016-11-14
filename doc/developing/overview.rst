..
    :copyright: Copyright (c) 2016 ftrack

.. _developing/overview:

********
Overview
********

The new publish tools are built as a plugin to :term:`ftrack connect`. As
such they can be checked out and run from source. See
:ref:`Maya installation <maya/installation>` and
:ref:`Nuke installation <nuke/installation>` for more details.

Hooking into maya launch
========================

The `hook/listen_to_maya_launch.py` in the repository root will hook into the
`ftrack.connect.application.launch` and modify environment variables to load
the plugin and dependencies.

Hooking into nuke launch
========================

The `hook/listen_to_nuke_launch.py` in the repository root will hook into the
`ftrack.connect.application.launch` and modify environment variables to load
the plugin and dependencies.

Application specific repositories
=================================

The source code with corresponding asset plugins can be found in the
following repositories:

*   Nuke: https://bitbucket.org/ftrack/ftrack-connect-nuke-publish
*   Maya: https://bitbucket.org/ftrack/ftrack-connect-maya-publish

Pipeline repository
===================

The new repository, https://bitbucket.org/ftrack/ftrack-connect-pipeline,
contains widgets, asset base classes and other utils that will be reused in
ftrack pipeline tools and integrations.

Notable classes are those defined in `source/ftrack_connect_pipeline/asset/`
