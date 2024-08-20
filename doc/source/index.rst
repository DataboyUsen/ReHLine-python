.. dnn-inference documentation master file, created by
   sphinx-quickstart on Sun Aug  8 20:28:09 2021.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

🦌 ReHLine
==========

.. image:: logo.png
   :width: 18%
   :align: right

.. -*- mode: rst -*-

|PyPi|_ |MIT|_ |Python3|_ |downloads|_

.. |PyPi| image:: https://badge.fury.io/py/rehline.svg
.. _PyPi: https://pypi.org/project/rehline/

.. |MIT| image:: https://img.shields.io/pypi/l/dnn-inference.svg
.. _MIT: https://opensource.org/licenses/MIT

.. |Python3| image:: https://img.shields.io/badge/python-3-blue.svg
.. _Python3: www.python.org

.. |downloads| image:: https://pepy.tech/badge/rehline
.. _downloads: https://pepy.tech/project/rehline


**ReHLine** is designed to be a computationally efficient and practically useful software package for large-scale ERMs. 

- Homepage: `https://rehline.github.io/ <https://rehline.github.io/>`_
- GitHub repo: `https://github.com/softmin/ReHLine-python <https://github.com/softmin/ReHLine-python>`_
- Documentation: `https://rehline.readthedocs.io <https://rehline.readthedocs.io/en/latest/>`_
- PyPi: `https://pypi.org/project/rehline <https://pypi.org/project/rehline>`_
- Paper: `NeurIPS | 2023 <https://openreview.net/pdf?id=3pEBW2UPAD>`_
.. - Open Source: `MIT license <https://opensource.org/licenses/MIT>`_

`ReHLine` is designed to be a computationally efficient 
and practically useful software package for large-scale regularized ERMs.

The proposed **ReHLine** solver has appealing exhibits appealing properties:

.. list-table::
    :widths: 20 80

    * - **Flexible losses**
      - It applies to ANY convex piecewise linear-quadratic loss function, including the hinge loss, the squared-hinge the check loss, the Huber loss, etc.
    * - **Flexible constraints**
      - It supports linear equality and inequality constraints on the parameter vector.
    * - **Super-Efficient**
      - The optimization algorithm has a provable **LINEAR** convergence rate, and the per-iteration computational complexity is **LINEAR** in the sample size.

🔨 Installation
===============

Install ``rehline`` using ``pip``

.. code:: bash

	pip install rehline

See more details in `installation <./installation.rst>`_.

📮 Formulation
--------------

`ReHLine` is designed to address the empirical regularized ReLU-ReHU minimization problem, named *ReHLine optimization*, of the following form:

.. math::

  \min_{\mathbf{\beta} \in \mathbb{R}^d} \sum_{i=1}^n \sum_{l=1}^L \text{ReLU}( u_{li} \mathbf{x}_i^\intercal \mathbf{\beta} + v_{li}) + \sum_{i=1}^n \sum_{h=1}^H {\text{ReHU}}_{\tau_{hi}}( s_{hi} \mathbf{x}_i^\intercal \mathbf{\beta} + t_{hi}) + \frac{1}{2} \| \mathbf{\beta} \|_2^2, \ \text{ s.t. } \mathbf{A} \mathbf{\beta} + \mathbf{b} \geq \mathbf{0},


where :math:`\mathbf{U} = (u_{li}),\mathbf{V} = (v_{li}) \in \mathbb{R}^{L \times n}` 
and :math:`\mathbf{S} = (s_{hi}),\mathbf{T} = (t_{hi}),\mathbf{\tau} = (\tau_{hi}) \in \mathbb{R}^{H \times n}` 
are the ReLU-ReHU loss parameters, and :math:`(\mathbf{A},\mathbf{b})` are the constraint parameters. 
This formulation has a wide range of applications spanning various fields, including statistics, 
machine learning, computational biology, and social studies. 
Some popular examples include SVMs with fairness constraints (FairSVM), 
elastic net regularized quantile regression (ElasticQR), 
and ridge regularized Huber minimization (RidgeHuber).

.. image:: ./figs/tab.png


Reference
---------
If you use this code please star 🌟 the repository and cite the following paper:

.. code:: bib

   @article{daiqiu2023rehline,
   title={ReHLine: Regularized Composite ReLU-ReHU Loss Minimization with Linear Computation and Linear Convergence},
   author={Dai, Ben and Yixuan Qiu},
   journal={Advances in Neural Information Processing Systems},
   year={2023},
   }


.. toctree::
   :maxdepth: 0
   :hidden:

   getting_started
   tutorials
   installation
   examples/index
   benchmark
