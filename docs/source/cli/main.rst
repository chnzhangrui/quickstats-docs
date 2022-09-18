.. _cli:

Command Line Interfaces
==========================
The easiest and quickest way to use ``quickstats`` is via its CLIs.
The following interfaces are available.
Use with:

.. code-block:: console

   quickstats <command> <options>

Check helper via:

.. code-block:: console

   quickstats --help
   quickstats <command> --help

=========================== ===============================================
**Statistical analysis**                     **Role**
--------------------------- -----------------------------------------------
  :ref:`inspect_ws`                Inspect workspace attributes
  :ref:`cls_limit`                 Tool for evaluating Asymptotic CLs limit
  :ref:`likelihood_fit`            Perform likelihood fit on a workspace
  generate_asimov           Generate Asimov dataset
  generate_standard_asimov  Generate standard Asimov dataset
  likelihood_scan           Evaluate a set of parmeterised likelihood values
  limit_scan                Evaluate a set of parmeterised asymptotic cls limits
  np_correlation            Evaluate post-fit NP correlation matrix
  run_pulls                 Tool for computing NP pulls and impacts
  plot_pulls                Tool for plotting NP pulls and impact rankings
  toy_limit                 Generate toys and evaluate limits
  toy_significance          Generate toys and evaluate significance
=========================== ===============================================

=========================== ===============================================
**Manipulate workspace**                      **Role**
--------------------------- -----------------------------------------------
  build_xml_ws              Build RooWorkspace from XML config files
  combine_ws                Combine workspace from XML config files
  compare_ws                Compare two workspace files
  modify_ws                 Modify workspace from XML/json config files
=========================== ===============================================

=========================== ===============================================
**Process RDataFrame**                      **Role**
--------------------------- -----------------------------------------------
  inspect_rfile             Inspect root files
  process_rfile             Process a ROOT file based on RDataFrame...
  harmonize_np              Harmonize NP names across different workspaces
=========================== ===============================================

.. toctree::
   :hidden:

   inspect_ws
   cls_limit
   likelihood_fit
