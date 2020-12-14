Glasgow-Maastricht Foot Model
#############################

This is the Glasgow-Maastricht (GM) Foot Model updated to work with 
with the TLEM 2.1 lower extremity model. 

The model was developed by AnyBody Technology developed in corporation with Glasgow Caledonian
University and University of Maastricht inside the `AFootprint EU project <http://www.afootprint.eu/>`_ .

The GM Foot Model is a a detailed multisegmental foot model, which is fully dynamic and
contains 26 segments representing all the foot bones, muscles,
ligaments, and joints connecting them.


.. figure:: Tests/GM_foot.gif
  :align: center

The model is currently distributed separate to the AnyBody Managed Model Repsitory (AMMR). 
We plan to re-integrate the GM foot model with the AMMR once it is sufficiently
stable and well tested.

.. caution:: Scaling of the model is one area which is not well tested.


Examples: 
==========

The model contains two example applications. 

1. Free posture: This shows how to include the model into any model and how to control its degrees of freedom.
2. MoCap: A motion capture model that shows how to use with MoCap data.

Usage: 
=============

.. note:: This implmentation only works with the TLEM 2 leg model, and requires a few 
          features which is only available in AMMR 2.0.1 or later. 

To use the GM foot model the file ``GM_Foot_libdef.any`` must be included before 
the first ``Main`` statement. 

.. code-block:: AnyScript

    // Include before the first Main
    #include "path/to/GM_Foot/GM_Foot_libdef.any"

    Main = {

        // Add body model configuration. E.g.
        #define BM_ARM_RIGHT OFF
        #define BM_ARM_LEFT OFF
        
        // Include the GM foot model. It handles inlcuding the human model as well.
        #include "<GM_FOOT_PATH>/GM_foot_model.any"


See :file:`Tests/test_footGM.any` for an example of including the GM foot. 
