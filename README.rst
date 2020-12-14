Glasgow-Maastricht Foot Model
#############################

This is a work in progress to reimplement the Glasgow-Maastricht (GM) Foot Model
with the TLEM 2.1 lower extremity model. The old implementation of the GM foot
model required its own modified implementation of the TLEM1 lower extremity
model. This was a nightmare to maintain and made it impossible to use the model
with new TLEM 2.1 model.

.. figure:: Tests/GM_foot.gif
  :align: center

The goal is to restructure the GM foot model to integrate nicely into the TLEM
2.1 model without duplicating the entire lower extremity model unnecessarily. We
are sharing the model on GitHub to give everyone early access to the model and
allow for users to help improve and test the model. 

We plan to re-integrate the GM foot model with the AMMR once it is sufficiently
stable and well tested. 



TODO: 
=====

#. Adjust (and validate) the new Ankle joint location, and ankle ligament insertions

#. Align scaling between foot and Leg (TLEM2).

#. Recrate the Joint moments measures with the new foot.

#. Fix Free posture example application.

#. Add GM foot example based on AnyMoCap.

#. Test and Validate results.


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
