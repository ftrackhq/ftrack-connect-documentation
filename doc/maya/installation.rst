..
    :copyright: Copyright (c) 2016 ftrack

.. _maya/installation:

************
Installation
************

adding something on top
=======================

Installation guide
==================

#.  Download and install ftrack Connect from
    https://www.ftrack.com/portfolio/connect.
#.  Open the <connect-plugin-directory> by from the Connect menu:
    (click on service icon) > Open plugin directory.
#.  Download the plugins from: https://s3-eu-west-1.amazonaws.com/ftrack-deployment/ftrack-connect/plugins/ftrack-connect-maya-publish-0.5.1.zip
#.  Unzip ftrack-connect-maya-publish-0.5.1.zip in <connect-plugin-directory>
#.  Restart ftrack Connect.
#.  Now you can launch Maya through Connect.

Starting from Connect
=====================

#.  Start ftrack Connect (close and start if already running).
#.  Start Maya for a task using ftrack connect or the ftrack web UI.
#.  Open menu `ftrack new` and choose one of the publish actions.

Building from source guide
==========================

#.  Download and install ftrack Connect from
    https://www.ftrack.com/portfolio/connect.
#.  Open a terminal and navigate to a <connect-plugin-directory. The directory
    can be found from Connect menu (click on service icon) > Open plugin
    directory.
#.  git clone https://bitbucket.org/ftrack/ftrack-connect-maya-publish.git to
    <connect-plugin-directory>.
#.  Checkout the latest tag::

        git tag --list
        git checkout <latest-tag>

#.  cd to <connect-plugin-directory>/ftrack-connect-maya-publish/
#.  Install all dependencies to a ftrack-connect-maya-publish into a directory
    with::

        pip install --target=dependencies --verbose --upgrade --process-dependency-links .

#.  This is all good if you want to try things out. But if we want to use the
    source rather than the installed ftrack_connect_maya_publish package you
    will need to remove it::

        rm -r dependencies/ftrack_connect_maya_publish
        rm -r dependencies/ftrack_connect_maya_publish-VERSION-py2.7.egg-info
