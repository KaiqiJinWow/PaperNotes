### On Calibration of Modern Neural Networks

##### Aim:



##### Probelm:

Neural networks produce conﬁdences that do not represent true probabilities.Modern neural networks exhibit a strange phenomenon: probabilistic error and miscalibration worsen even as classiﬁcation error is reduced.

##### Information Collect:

- 20news
- Reuters
- Stanford Sentiment Treebank(SST)

### Method:

#### Binary Models:

##### Histogram binning:

All uncalibrated predictions $P_i​$ will be divided into a mutually exclusive bin $B_m​$, then $q_i​$ =$\theta_m​$.

The predictions $\theta_i$ are chosen to minimize the bin-wise squared loss:

![image-20190317105831705](/Users/jasin/Library/Application Support/typora-user-images/image-20190317105831705.png)

##### Isotonic regression:

The value of parameter must not decrease.

![image-20190317110545561](/Users/jasin/Library/Application Support/typora-user-images/image-20190317110545561.png)
$\theta_m$ is the value of piecewise constant function $f(p_m)$ 

##### Bayesian Bining into Quantiles(BBQ)

![image-20190317192418355](/Users/jasin/Library/Application Support/typora-user-images/image-20190317192418355.png)

![image-20190317192522175](/Users/jasin/Library/Application Support/typora-user-images/image-20190317192522175.png)

and can get a closed form expression for the marginal likelihood $P(D|S=s)$

##### Platt scaling

$q_i = sigmod(\alpha z_i + b)$ Where a,b $\in \real$ are scalar parameter.

### Multiclass models

The network output a class prediction $y_i$ = $argmax_k z_k^(k)$and confidence score $p_i$ for each input $X_i$ and the non-probabilistic output. 

![image-20190317194202881](/Users/jasin/Library/Application Support/typora-user-images/image-20190317194202881.png)

##### Extension of binning methods

K one-versus-all problem

##### Matrix and vector scaling

![image-20190317195345390](/Users/jasin/Library/Application Support/typora-user-images/image-20190317195345390.png)

##### Temperature scaling

![image-20190317195649190](/Users/jasin/Library/Application Support/typora-user-images/image-20190317195649190.png)

$ T$ is called the temperature and it raise the output entropy with T>1 and the probability fall to a point mess(i.e. $q_i$ =1) wth $T \rightarrow 0$ .

The class prediction $y_i'$remains unchanged and the temperature scaling does not affect the model's accuracy.

##### Reason & Assumptation:

##### Analysis results:

Temperature scaling outperforms all other methods on the vision tasks, and performs comparably to other methods on the NLP datasets.

calibration is best corrected by simple models.

