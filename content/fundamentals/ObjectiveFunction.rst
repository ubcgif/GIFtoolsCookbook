.. _Fundamentals_ObjectiveFunction:

The Objective Function
======================

Geophysical inversion recovers a physical property model which fits the data and has geologically reasonable structures. But how is this done in practice? The majority of geophysical inversion algorithms work by minimizing an objective function (:math:`\phi`) with respect to the physical property model (:math:`\mathbf{m}`):

.. math::
    \phi(\mathbf{m}) = \phi_d(\mathbf{m}) + \beta \phi_m(\mathbf{m})
    :label: ObjFun

This is sometimes referred to as "penalty-based optimization"; that is, the objective function is large if the model doesn't fit the data and/or has implausible structures. The objective function is comprised of three components:

    - **data misfit** :math:`\phi_d (\mathbf{m})`, which is responsible for ensuring the recovered model predicts data that fits the set of field observations.

    - **model objective function** :math:`\phi_m (\mathbf{m})`, which ensures that the recovered model contains plausible geological structures.

    - **trade-off parameter** :math:`\beta`, which weights the relative contribution of :math:`\phi_d (\mathbf{m})` and :math:`\phi_m (\mathbf{m})` towards the objective function.

.. _Fundamentals_ObjectiveFunction_dmis:

**Data Misfit:**

The Data misfit (:math:`\phi_d`) in :eq:`ObjFun` is given by:

.. math::
    \phi_d(\mathbf{m}) = \big \| \mathbf{W}_d [ \mathbf{F}(\mathbf{m})-\mathbf{d} ] \big \| ^2
    :label: DataMisfit

where

    - :math:`\mathbf{F[m]}` is the forward modeling operator; i.e. an operation that predicts the data for a given physical property model :math:`\mathbf{m}`.
    - :math:`\mathbf{d}` is the set of observed data.
    - :math:`\mathbf{W_d}` is a matrix which weights the difference in predicted and observed data by the data uncertainty. The uncertainty acts as an estimate of the standard deviation of random noise on each data point.

The :math:`\mathbf{W_d}` matrix is used for two reasons. 1) If the observed data span several orders of magnitude, we want to make sure that the inversion doesn't focus on fitting the large values at the expense of the small values. 2) If the noise on our data are independent and Gaussian, then the predicted data fits the noise to an appropriate tolerance when :math:`\phi_d` equals the number of data; that is, the inversion fits the signal without fitting the noise (over-fitting). As a result, we generally stop the algorithm when the data misfit is equal to the number of data (target misfit).


..    \phi_m(\mathbf{m}) = \alpha_s \int (w_s(\mathbf{r})(m(\mathbf{r})-m_0)^2 \delta v) + \alpha_x \int w_x(\mathbf{r})\left\( \frac{\delta(m(\mathbf{r})-m_0)}{\delta x}\right\)^2 \delta v + \alpha_z \int w_z(\mathbf{r})\left\( \frac{\delta(m(\mathbf{r})-m_0)}{\delta z}\right\)^2 \delta v + \alpha_z \int w_z(\mathbf{r})\left\( \frac{\delta(m(\mathbf{r})-m_0)}{\delta x}\right\)^2 \delta v


.. _modelObjectiveFunction:

**Model Objective Function/Regularization:**

The model objective function (:math:`\phi_m`) is where we impose structures on the recovered model. It also acts as a regularizer; i.e. stabilizes the inversion algorithm. The model objective function can be divided in two sections, the smallness and the smoothness:

.. math::
    \phi_m(\mathbf{m}) = \phi_{small}(\mathbf{m}) + \phi_{smooth}(\mathbf{m})
    :label: Regularizer

With:

.. math::
    \phi_{small}(\mathbf{m}) = {\alpha_s} ||\mathbf{W_s}\;\mathbf{R}_s(\mathbf{m}-\mathbf{m}_{ref})||_2^2
    :label: Smallness

- :math:`\phi_{small}` is the Smallness term. It defines how the model can vary from the reference model :math:`\mathbf{m}_{ref}` (:eq:`Smallness`).

And:

.. math::
    \phi_{smooth}(\mathbf{m}) = &{\alpha_x} ||\mathbf{W_x}\;\mathbf{R}_x \; \mathbf{G}_x(\mathbf{m}-\mathbf{m}_{ref})||_2^2 +\\
    &{\alpha_y} ||\mathbf{W_y}\;\mathbf{R}_y \; \mathbf{G}_y(\mathbf{m}-\mathbf{m}_{ref})||_2^2 +\\
    &{\alpha_z} ||\mathbf{W_z}\;\mathbf{R}_z \; \mathbf{G}_z(\mathbf{m}-\mathbf{m}_{ref})||_2^2
    :label: Smoothness

- :math:`\phi_{smooth}` is the Smoothness term. it defines how the gradients in each direction, defined by the matrices  :math:`G_x`,  :math:`G_y` and :math:`G_z`, of the model can vary from the gradient of the reference model (:eq:`Smoothness`).


..    \phi_m(\mathbf{m}) = \alpha_s ||W_s(\mathbf{m}-\mathbf{m}_0)||^p + \alpha_x ||W_x G_x(\mathbf{m}-\mathbf{m}_0)||^q + \alpha_y ||W_y G_y(\mathbf{m}-\mathbf{m}_0)||^q + \alpha_z ||W_z G_z(\mathbf{m}-\mathbf{m}_0)||^q

- The :ref:`weighting matrices<Fundamentals_WeightingMatrix>` :math:`\mathbf{W}_s`, :math:`\mathbf{W}_x`, :math:`\mathbf{W}_y` and :math:`\mathbf{W}_z` are cell-specific weightings for each of these terms. They can combine user-defined confidence models with depth or distance weighting.
- the :ref:`alphas parameters<Fundamentals_alphas>` :math:`\alpha_s`, :math:`\alpha_x`, :math:`\alpha_y`, and :math:`\alpha_z` control how important each of the four terms are relative to each other
- The sparsity weights :math:`\mathbf{R}_s`, :math:`\mathbf{R}_x`, :math:`\mathbf{R}_y` and :math:`\mathbf{R}_z` are defined by the :ref:`lp-norms <Fundamentals_Norms>`.
- In the UBC codes, the option SMOOTH_MOD_DIFF uses the reference model in all terms, while SMOOTH_MOD would only use the reference model in the Smallness term.

In this section, we will explore the effect of these different parameters on the recovered model through a susceptible block in a non-susceptible half-space mapped with a total magnetic ground survey.

.. figure:: ../../images/InversionFundamentals/model.png
    :align: right
    :figwidth: 100%
    :name: InvFundModel
