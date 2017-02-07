..
    :copyright: Copyright (c) 2016 ftrack

.. _developing/event:

***********
Events list
***********

The following are standard ftrack events published by the framework.

.. _developing/event/ftrack.pipeline.register-assets:

ftrack.pipeline.register-assets
===============================

Emitted by the framework when it requires the assets to register to the given
session. The event is emitted synchronous::

    Event(
        topic='ftrack.pipeline.register-assets',
        data=dict()
    )

A common use is to register using the `ftrack_connect_pipeline.asset.Asset`::

    def create_asset_publish():
        '''Return asset publisher.'''
        return geometry_asset.PublishGeo(
            description='publish geometry to ftrack.',
            asset_type_short='geo'
        )


    def register_asset_plugin(session, event):
        '''Register asset plugin.'''
        geometry_asset = ftrack_connect_pipeline.asset.Asset(
            identifier='geo',
            label='Geometry',
            icon='http://www.clipartbest.com/cliparts/9cz/EzE/9czEzE8yi.png',
            create_asset_publish=create_asset_publish
        )
        # Register geo asset on session. This makes sure that discover is called
        # for import and publish.
        geometry_asset.register(session)

Where geometry.register will attach relevant event / action listeners.
