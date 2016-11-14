..
    :copyright: Copyright (c) 2016 ftrack

.. _developing/asset_plugin:

************
Asset plugin
************

The publishing and later importing and switching of an asset version is governed
by the definition of an asset plugin. The idea is to allow 3rd party integrators
to write custom asset plugins or extend existing ones.

Bundled assets plugins are based on class definitions in the respective `asset`
submodule in the ftrack_connect_maya_publish and ftrack_connect_nuke_publish
modules.

The asset plugins will register from event hooks in the `resource` directory
when the application's ftrack-python-api session emits the
:ref:`developing/event/ftrack.pipeline.register-assets` event.

An asset plugin will contain the following functionality:

*   Publish asset version (Available now)
*   Import asset version (Available later)
*   Switch asset version (Available later)
