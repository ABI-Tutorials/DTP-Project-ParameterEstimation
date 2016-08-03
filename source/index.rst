.. _dtp_cp_project_parameterestimation:

Project: Parameter Estimation
=============================

This project was created as part of the Computational Physiology module in the `MedTech CoRE 
<http://medtech.org.nz>`_ Doctoral Training Programme. 

This project requires you to put together what you have learned in the tutorials to define a complete workflow which we will use to manually optimise the material properties of a tissue model for use in mechanical simulations.

Outline
-------

In this project we recreate a typical workflow that is often performed by scientists when creating a model. The standard cardiac workflow used in the DTP module is shown in :numref:`fig_dtp_cp_estimationproject_cardiac`, which can be abstracted into the generic workflow shown in :numref:`fig_dtp_cp_estimationproject_generic`.

.. _fig_dtp_cp_estimationproject_cardiac:

.. figure:: _static/DTP-CP-Workflow-01.png
   :align: center
   :width: 90%

   The standard example cardiac workflow used in the DTP Computational Physiology module.

.. _fig_dtp_cp_estimationproject_generic:

.. figure:: _static/DTP-CP-Workflow-02.png
   :align: center
   :width: 90%

   The generic DTP Computational Physiology workflow.
   
In this project, we adapt the generic workflow shown in :numref:`fig_dtp_cp_estimationproject_generic` to the specific scenario we are recreating. The specific workflow for this project is described in :numref:`fig_dtp_cp_estimationproject_projectwf`.

.. _fig_dtp_cp_estimationproject_projectwf:

.. figure:: _static/DTP-CP-Workflow-03.png
   :align: center
   :width: 90%

   The specific workflow for this project. The output for this workflow is to predict the passive mechanical material properties of a piece of cardiac tissue given the results from a mechanical testing experiment. As is commonly done, the actual experimental data will be extracted from a published paper where the actual data is only available as a printed figure. The extracted data will be used to predict the material properties of an existing cardiac tissue model.

Geometric model
---------------

As you may know, caridac tissue consists of cells aligned in fibres, as shown in :numref:`fig_dtp_cp_estimationproject_cardiacfibres`. Mechanically, the tissue is much stiffer in the fibre direction than in the cross-fibre direction, and so it is very important for any model of cardiac tissue to take this into account.

.. _fig_dtp_cp_estimationproject_cardiacfibres:

.. figure:: _static/cardiac-fibres.png
   :align: center
   :width: 90%

   Illustrations of the fibrous nature of cardiac tissue. 

In this project, we use the simplified geometric model shown in :numref:`fig_dtp_cp_estimationproject_mesh`. While this is a relatively trivial model, it is a reasonable approximation to an often used experimental preparation - the `cardiac trabecula <https://en.wikipedia.org/wiki/Trabeculae_carneae>`_.

.. _fig_dtp_cp_estimationproject_mesh:

.. figure:: _static/mesh.png
   :align: center
   :width: 90%

   The specific geometric model used in this project. In this tissue model the muscle fibres are aligned in the same direction, indicated by the silver line. The blue plane indicates the orthogonal direction.

Data collection
---------------

The first step in this project is to collect the experimental data that will be used in estimating the material properties of this tissue. In this project we are using simulated experimental data so that we have some hope that this will be an achievable task. You can see typical experimental data from a real cardiac trabecula that would be used in a lab here: https://youtu.be/_VHZyPEpxsc. Since our model is homogeneous and transversly isotropic, we can reduce the data required to parameterise the model to two stress-strain relationships - one for the fibre direction and one of the orthogonal cross-fibre direction. The actual data we will use is shown in :numref:`fig_dtp_cp_estimationproject_data` and the segmentation method we will use to extract the numerical values of the data is shown in :numref:`fig_dtp_cp_estimationproject_segmentation`.

.. _fig_dtp_cp_estimationproject_data:

.. figure:: _static/stress-strain-plot.png
   :align: center
   :width: 90%

   The "experimental" data we will use to estimate the material properties of our cardiac tissue model.

.. _fig_dtp_cp_estimationproject_segmentation:

.. figure:: _static/manual-segmentation.png
   :align: center
   :width: 90%

   Illustrating the "manual segmentation" method that we will use to obtain the actual experimental data. When extracting the numerical values, you will need to collect **5 data points** for each of the fibre and cross-fibre relationships.

You will need to start MAP Client and create a new workflow via the menu item  :menuselection:`File --> New --> Workflow`. This just requires you to select a folder: create a new, empty folder, for example "estimationproject" on the Desktop, and select it.

