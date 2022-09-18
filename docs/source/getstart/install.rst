.. _install:

Install and Setup
==========================

Among other dependences, ``quickstats`` depends on `ROOT <https://root.cern.ch>`_, or to be precise, pyROOT.
While other Python dependences are normally easy to install, pyROOT installation is not straightforward.
Therefore, this section will try to cover pyROOT installation where necessary.

On CVMFS via LCG releases
--------------------------
If you are using CERN LXPLUS machines, or local clusters where CVMFS is mounted, you can first access pyROOT via the LCG releases.
This will avoid install pyROOT yourself.
In that case, you could use either install from source code (recommended) or install quickstats for user via ``pip install --user``.
We will cover the second way in next subsection.

.. code-block:: console

    git clone ssh://git@gitlab.cern.ch:7999/clcheng/quickstats.git
    cd quickstats && source setup.sh
    # first time use, compile c++ dependencies
    quickstats compile

Then make sure the executable is available via

.. code-block:: console

    which quickstats

Standalone environment
--------------------------
For a standalone use, first need to install ROOT (6.22+).
Recommand to use mini/anaConda and ROOT is `available <https://anaconda.org/conda-forge/root/>`_ in conda-forge.

.. code-block:: console

    conda install -c conda-forge ROOT
    pip install quickstats

Or for any reason that conda is infeasible, you can use the native Python environment and install quickstats with the user scope.
But it has to be true that Python3 and ROOT 6.22+ are available.

.. code-block:: console

    pip install --user quickstats

This will install ``quickstats`` under your $HOME directory.