.. _Fundamentals_Joint:

Joint Inversion and Data Weighting
==================================

Joint inversion is used to recover a physical property model by inverting multiple datasets which all depend on the same diagnostic physical property. For example, any combination of MT, ZTEM, FDEM or TDEM data may be inverted jointly to recover a conductivity model. When performing a joint inversion, we are effectively solving an inverse problem for the following misfit function:

.. math::
    \phi (\mathbf{m}) = \phi_{d,1} + \phi_{d,2} + \ldots + \beta \phi_m


where the data misfit corresponding to each dataset has the form:

.. math::
    \phi_d = \sum_i^N \Bigg | \frac{d_i^{pre} - d_i^{obs}}{\varepsilon_i} \Bigg |^2


and :math:`\varepsilon_i` is the uncertainty for datum :math:`i`.

It is important that we fit our inversion fits every dataset in a balanced manner. If this is not accomplished, the inversion may overfit one dataset underfit others. Furthermore, information required to constrain certain structures may be underutilized. There are several techniques for ensuring appropriate results when attempting joint inversion.

.. _Fundamentals_Joint_Balancing:

Balancing Uncertainties for Joint Inversion
-------------------------------------------

Let us start by considering inversion for a single dataset. In practice, the uncertainties assigned to the data are rarely ideal and we must examine the Tikhonov curve to infer the iteration at which the recovered model fits the data globally without over-fitting. Even if the selected model does not correspond to a chi-factor of 1 (i.e. :math:`\phi_d = N`), the model is reasonable so long as 1) it reproduces the observed data accurately without overfitting, 2) there are no coherent artifacts in the misfit maps and 3) the level of misfit between each component and each frequency is balanced.

Joint inversion is more challenging, as the uncertainties assigned to each dataset must also be balanced so that one dataset is not overfit at the expense of any others. For each data object, we propose a simple approach for balancing the uncertainties.

Let :math:`\boldsymbol{\varepsilon}` be the original uncertainties used for independent inversion of a single dataset. If the model we chose as the recovered model corresponds to a chi-factor :math:`\chi` (not necessarily 1), then from our definition of the data misfit:

.. math::
    \chi = \frac{1}{N} \sum_i^N \; \Bigg | \frac{d_i^{pre} - d_i^{obs}}{\varepsilon_i} \Bigg |^2


If we want the recovered model to corresponded to a chi-factor of 1, we would simply need to multiply the original uncertainties by :math:`\sqrt{\chi}` and re-run the inversion given that:

.. math::
    1 = \frac{1}{N} \sum_i^N \; \Bigg | \frac{d_i^{pre} - d_i^{obs}}{\varepsilon_i \sqrt{\chi} } \Bigg |^2 = \frac{1}{N} \sum_i^N \; \Bigg | \frac{d_i^{pre} - d_i^{obs}}{\varepsilon_i^* } \Bigg |^2


where :math:`\boldsymbol{\varepsilon}^* = \sqrt{\chi} \boldsymbol{\varepsilon}` are the 'balanced uncertainties'.

In essence, we are multiplying the original uncertainties of each dataset so that if we were to re-run the set of independent inversions, the recovered models would all correspond to a chi-factor of 1. In doing so, we assume that each inversion fits their respective data equally at the same chi-factor. Furthermore, we assume this balance will transfer over when inverting the data jointly.


.. _Fundamentals_Joint_Weighting:

Inversion With Data Weighting
-----------------------------

Data weighting weighting is generally considered when:

    - datasets are not being fit evenly during joint inversion, even though we have assigned 'balanced uncertainties'
    - you want to prioritize fitting one dataset more than another due to the quality of the information it provides
    - the number of data in each dataset differs drastically and you would like the data misfit between all datasets to be equal

When data weighting is applied, we are effectively solving an inverse problem for the following misfit function:


.. math::
    \phi (\mathbf{m}) = \dfrac{N}{\sum C_i} \Big [ \; C_1\phi_{d,1} + C_2\phi_{d,2} + \ldots \; \Big ] + \beta \phi_m


where :math:`C_i` are the data weighting constants specified by the user and *N* is the number of datasets being jointly inverted. The term in front of the bracket ensures the balance between the data misfits and the model objective function is not altered by applying data-based weighting; i.e. we require :math:`N = \sum C_i`. Data weighting can be apply in a number of ways.

**General weights:**

In this case, we define a weights :math:`C_1, C_2, \ldots` for each dataset. The larger the weight relative to the others, the more emphasis the inversion has on fitting that dataset. E.g for two dataset, we may supply the numbers :math:`C_1=4` and :math:`C_2=1`. We want our weighting to fit the first dataset 4 times more strongly. From the above expression, **the actual constants multiplying each data misfit term are** 8/5 and 2/5, respectively.

**Weighting based on number of data:**

When one dataset has many more data components and/or locations than another, the inversion may not need to fit the smaller dataset well to reach target misfit. In this case, you may include a weighting such that the data misfit terms contribute equally; i.e. :math:`\phi_{d,1}=\phi_{d,2}=\ldots \;`.
Where :math:`n_i` is the total number of data for dataset *i*:

.. math::
    C_i = \frac{1}{n_i} \bigg [ \sum \frac{1}{n_i} \bigg ]^{-1}

E.g. for two datasets such that :math:`n_1 = 1000` and :math:`n_2 = 4000`, we would have :math:`C_1 = 4/5` and :math:`C_2 = 1/5`. And **the actual constants multiplying each data misfit term are** 8/5 and 2/5, respectively.

**Both**

Both custom weights and weighting based on the number of data can be applied simultaneously within GIFtools. The option to weight based on the number of data can be toggled on or off. And general weights can be modified or all set to a value of 1.




