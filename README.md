This is the code used to generate the results for the ICML 2022 conference paper "Solving  Stackelberg Prediction Game with Least Squares Loss via Spherically Constrained Least Squares Reformulation".

This code has the following requirements:
- MATLAB 2020b or later
- MOSEK solver (https://www.mosek.com/)
- ROPTLIB solver (https://www.math.fsu.edu/~whuang2/Indices/index_ROPTLIB.html)
- The MATLAB Statistics and Machine Learning Toolbox (https://uk.mathworks.com/products/statistics.html)
- The MATLAB Parallel Computing Toolbox (https://uk.mathworks.com/products/parallel-computing.html)
- The MATLAB Optimization Toolbox (https://uk.mathworks.com/products/optimization.html)



All experimental results in our paper are saved as csv format in the file of "result". The file "datasets" is where our synthetic and real-world datasets are placed.  To save space, we only put wine and insurance datasets in "datasets" file, you can download other real-world datasets  from the following websites.

+ BlogFeedBack Dataset (https://archive.ics.uci.edu/ml/datasets/BlogFeedback)
+ Residential Building Dataset (https://archive.ics.uci.edu/ml/datasets/Residential+Building+Data+Set)

If you want to generate dense synthetic data, please run the ipynb file `generate_synthetic_dense.ipynb`. Then the correspondingly synthetic datasets would be placed at file "datasets/synthetic/dense_matrix".

If you want to generate sparse synthetic data, please run the matlab file `generate_synthetic_sparse.m`. Then the correspondingly synthetic datasets would be placed at file "datasets/synthetic/sparse_matrix".

#### How to get results

Noted that we did not provide detail codes of LTRSR ([Link](https://www.researchgate.net/profile/Leihong-Zhang-3/publication/318447764_A_Nested_Lanczos_Method_for_the_Trust-Region_Subproblem/links/5a600f3c458515b4377b8c2a/A-Nested-Lanczos-Method-for-the-Trust-Region-Subproblem.pdf)) and RTRNewton methods ([Link](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.156.2337&rep=rep1&type=pdf)) for copyright. You need to first complement functions "LTRSR1"，"LTRSR2"， "RTRNewton1"  and "RTRNewton2"  in our codes.  The difference between method1 and method2 is either you store result $H=\hat{L}^T\hat{L}$ beforehand and directly use $H$ in following process or multiply result $ \hat{L}r $ every time. To complement the function "LTRSR", you can use any Krylov subspace method such as Generalized Lanczos Trust Region (GLTR) method ([Link](https://cds.cern.ch/record/333498/files/SCAN-9709015.pdf)). To complement the function "RTRNewton", you should download ROPTLIB solver in website([Link](https://www.math.fsu.edu/~whuang2/Indices/index_ROPTLIB.html)). After you complement above functions, you can obtain results by following steps.

+ To run the experiments of real datasets, please `run main_realData.m`. 
+ To run the experiments of synthetic dense datasets, please `run main_syntheticData_dense.m`.
+ To run the experiments of synthetic dense datasets, please `run main_syntheticData_sparse.m`.

All the results of above experiments will be placed at file 'result'.

#### How to plot the figures

+ To obtain the figures of time comparison, you can use the function `plot_time(csvname)`, where "csvname" is the path of corresponding  time csv file. For example, `csvname = './result/wine_modest_time.csv'`

#### Citation

If you found the provided code useful, please cite our work.