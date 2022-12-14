..
    :copyright: Copyright (c) 2016 ftrack

.. _developing/publish_using_pyblish:

************************
Publishing using pyblish
************************

As an example we will look at the Maya geometry asset which uses :term:`pyblish`
for publishing. Note that the concepts described in this article is generic and
can be applied to Nuke and other applications.

Let us have a look at the structure of the geometry asset plugin::

    ftrack_connect_maya_publish/asset/geometry/
        pyblish_plugins/
            __init__.py
            collect.py
            extract_alembic.py
            extract_mayabinary.py
        __init__.py
        geometry_asset.py

In the `pyblish_plugins` directory there are a number of pyblish plugins
defined. These takes care of the publish process: collecting what to publish,
validating and extracting the data, then integrating (registering) everything
in ftrack.

In the `geometry_asset.py` we define the asset plugin, how to publish,
import and switch to a different version for an already imported asset. The
asset plugin does not necessarily have to publish using :term:`pyblish`.

However, the asset plugin itself not registered here. Instead let us look at
register_geometry_asset.py in the `resource/` directory:

.. literalinclude:: /resource/geometry_asset_registration_example.py
    :language: python

Here we find the registration of the asset plugin for geometry. The asset plugin
will be registered with a unique identifier when the application's
ftrack-python-api session emits the
:ref:`developing/event/ftrack.pipeline.register-assets`. The create_asset_publish
argument, `PublishGeometry` instance will handle publishing.

.. note::

    In future versions there will be a import_asset and a switch_asset argument.

Let us look at a definition of the PublishGeometry class that got imported:

.. literalinclude:: /resource/geometry_asset_example.py

Here we see that it inherits `ftrack_connect_pipeline.asset.PyblishAsset` and
will, as the name suggests be using :term:`pyblish` for the publishing process.

While processing :term:`pyblish` plugins will be accessing options from the
interface. These options are defined in the methods on the `PublishGeometry`
class and and are following the syntax described in
:ref:`Developing actions user interface <developing/actions/user-interface>`.


There are two additional types only available in the new tools:

:group:

    Visually group a number of options in the UI. Options will be saved under
    the `name` key::

        {
            'type': 'group',
            'label': 'Maya binary',
            'name': 'maya_binary',
            'options': [..]
        }
    
:qt_widget:
    
    The `qt_widget` type can be used to present a custom widget to the user::

        {
            'widget': StartEndFrameField(start_frame=0, end_frame=1001),
            'name': 'frame_range',
            'type': 'qt_widget'
        }

    The options will be saved under the `name` key. The StartEndFrameField
    being a subclass of
    `ftrack_connect_pipeline.ui.widget.field.base.BaseField`. The widget must:

    #.  Implement the `value` method that returns the current value of the
        field.
    #.  Emit `value_changed` signal with value when the underlying value
        changes.

    Here is an example of a start/end frame qt based widget:

    .. literalinclude:: /resource/start_end_frame_widget_example.py

Notable methods that are implemented on the `PublishGeometry` class:

:get_publish_items:
    Return a list of items that can be published from the scene. In a pyblish
    based publish workflow this is ususally done by filtering on the pyblish
    instance family/families.

:get_options:
    Return a list of options that are general options for the publish.

:get_item_options:
    Return a list of options that are valid for the given item name.

These methods can access the current pyblish context on self::

    for instance in self.pyblish_context:
        print instance

Pyblish plugins
---------------

In the `pyblish_plugins` directory we have the plugins that will collect the
geometries from the scene and extract them as a maya binary and/or alembic.

Common :term:`pyblish` plugins are defined in
`ftrack_connect_maya_publish/shared_pyblish_plugins` and will be used for
collection and integration plugins that are shared between asset plugins.
