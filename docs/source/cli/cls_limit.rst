.. _cls_limit:

cls_limit
--------------------------

*Command to set upper limit.*

A RooWorkspace file contains everything you need to perform a CLs limit setting.
Therefore it will be the only input file.
However, a RooWorkspace may contain additional information that is irrelevant to your study.
For example it may have multiple ``dataset``, but you are interested in one of them.
In addition, you may want to config the limit setting program in RooStats, fix or change variable values inside the workspace.
These demands can be met via the available options.

Simple use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
To evaluate the upper limit of a workspace file `workspace.root`, you can run:

.. code-block:: console

    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind

You must know the POI (parameter of interest) name (``mu_SIG``), the dataset name (``obsData``).
Use :ref:`inspect_ws` to check their names and availability.
Drop ``--unblind`` if you want to perform limit setting on Asimov data only.

Advanced use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
You may want to fix some values of variables in the workspace.
For example, you want to perform a statistical limit setting by fixing all NP (nuisance parameter) values to zero (so called prefit statistical limit).
Or you want to fix a group of nuisance parameters to different values.
You can easily achieve these use cases via one of the following commands:

.. code-block:: console

    # fix all nuisance parameter values to their initial values
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f '<nuisance_parameter>'
    
    # fix all constrained nuisance parameter values to their initial values
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f '<constrained_nuisance_parameter>'
    
    # fix all unconstrained nuisance parameter values to their initial values
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f '<unconstrained_nuisance_parameter>'

    # fix all nuisance parameters but ATLAS_lumi 
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f '<nuisance_parameter>' -r ATLAS_lumi

    # fix all ATLAS_xxx to 1 and THEO_xxx to 0
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f ATLAS_*=1,THEO_*=0
    
    # fix all POI to 1 (if there is more than one POIs) and ATLAS_xxx to 0, but mu_SIG will always be floated
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f '<poi>=1,ATLAS_*=0'

    # fix all ATLAS_xxx to 0 but ATLAS_lumi to 1 (orders are important so 'ATLAS_lumi=1,ATLAS_*=0' will not work as desired)
    quickstats cls_limit -i workspace.root -p mu_SIG -d obsData --unblind -f 'ATLAS_*=0,ATLAS_lumi=1'


If you don't know which NP is constrained which is unconstrained, check :ref:`inspect_ws`.

Crazy use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
You may need to do some special checks if something went wrong, or as requested by somebody.
The following options might be useful to be aware of:
- ``--eps``: the convergence criterium, also related to `tolerance` that people sometimes talk about. Default is 1 corresponding to 0.001 of tolerance. A common requirement could be tolerance of E-5, corresponding to ``-e 0.01``.
- ``--snapshot``: the snapshot to load. A snapshot saves all variable values (including POIs, NPs, global observables) at a certain timestamp. This is useful for postfit Asimov dataset where postfit NP values should be assigned to the global observables as well. Only if you load this snapshot, the postfit Asimov dataset can be truly reproduced.
- ``--strategy``: minimizer strategy, can take [0, 1, 2] with slower but more reliable. Can increase strategy if you observe a failure. Although it will be also raised when retrying.
- ``--retry``: retry limit setting with higher strategy. It not only increment strategy, but also start from the current failed variable values, therefore is more possible to converging than just incrementing strategy.
- ``--print_level`` and ``--verbosity``: useful when debugging.
- ``--outname``: useful if running multiple jobs in the same folder.