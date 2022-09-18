.. _inspect_ws:

inspect_ws
--------------------------

**Command to inspect the contents in a RooWorkspace.**

A RooWorkspace file usually contains a single RooWorkspace (we also conventional call it `workspace`).
The following items in a workspace might be most interesting to know:
- workspace name,
- dataset names,
- Snapshot names (only available in ROOT 6.26+),
- PDF or Categories,
- Parameter of Interest values and status,
- Nuisance parameter values and status,
- Global observables values and status,
- Auxiliary variables values and status,

The status of a variable can be `constant` (C) or floated `(F)`.

Simple use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
To inspect a workspace file `workspace.root`, you can run:

.. code-block:: console

    quickstats inspect_ws -i workspace.root


Advanced use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: console

    quickstats inspect_ws -i workspace.root --items workspace,dataset,snapshot,category,poi,detailed_nuisance_parameter,auxiliary

It is important to make sure that all Auxiliary variables are constant otherwise limit setting or fitting is out of control.


Crazy use
^^^^^^^^^^^^^^^^^^^^^^^^^^^
.. code-block:: console

    quickstats inspect_ws -i workspace.root --items workspace,dataset,snapshot,category,poi,detailed_nuisance_parameter,auxiliary,global_observable