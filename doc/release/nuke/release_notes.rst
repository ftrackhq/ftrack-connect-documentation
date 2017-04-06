..
    :copyright: Copyright (c) 2016 ftrack

.. _release/nuke/release_notes:


****
Nuke
****

.. release:: 0.5.0
    :date: 2017-04-06

    .. change:: new
        :tags: Widget

        Add new Global Context Switch dialog to menu.

    .. change:: changed
        :tags: Plugin, Internal

        Change and clarify structure of the plugin framework.

.. release:: 0.4.0
    :date: 2017-02-23

    .. change:: new
        :tags: Publish, Review

        Added support for adding web reviewable when publishing.

    .. change:: changed
        :tags: Publish

        Changed publish workflow icons.

    .. change:: fixed
        :tags: Publish

        Fixed issue with `Open in ftrack` button.

.. release:: 0.3.1
    :date: 2017-02-07

    .. change:: new
        :tags: Publish

        Added support to attach scene as reference when publishing.

    .. change:: new
        :tags: Publish

        Application version and name is saved as metadata on component.

    .. change:: new
        :tags: Publish

        Added support for creation of asset type if they do not exist.

    .. change:: new
        :tags: Validation

        Added support for pyblish validations.

    .. change:: changed
        :tags: Publish, User interface

        Changed style and layout of publish dialog.

    .. change:: changed
        :tags: Publish, Debugging

        Improved debugging tools when publishing.

    .. change:: changed
        :tags: Publish

        Improved result window for publishing using `Pyblish`.

    .. change:: fixed
        :tags: Publish

        Hard to understand what to type in the asset version description.

    .. change:: fixed
        :tags: Publish

        No empty text if there is nothing to publish.

    .. change:: fixed
        :tags: Publish

        Checkboxes are hard to see in the UI.

    .. change:: fixed
        :tags: Publish, Thumbnail

        Publish fails if no thumbnail is selected.

.. release:: 0.2.0
    :date: 2016-11-29

    .. change:: new
        :tags: Publish

        Added possibility to select scene as reference when publishing.

    .. change:: new
        :tags: Publish

        Added selection of thumbnail when publishing.

.. release:: 0.1.1
    :date: 2016-11-18

    .. change:: new
        :tags: Publish

        Added context switcher to publish dialog.

.. release:: 0.1.0
    :date: 2016-11-14

    .. change:: new
        :tags: Publish

        Initial release of technical preview of new :term:`publish dialog` for
        Nuke.
