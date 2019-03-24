

### Introduction

##### Notion

- **Model Uncertainty**:measures the uncertainty in estimating the model parameters given the training data.

- **Model Uncertainty**:reducible as the size of training data increases.

- **Data Uncertainty**:irreducible uncertainty which arises from the natural complexity of the data.

- **Distributional Uncertainty**:mismatch between the training and test distributions,the model is unfamiliar with the test data and thus cannot conﬁdently make predictions.

### Current Methods

**Methods**: craft an implicit conditional distribution over a simplex (ﬁg. 1b) with the attributes that it is sharp at the corners of a simplex for inputs similar to the training data and ﬂat over the simplex for out-of-distribution inputs.

**Problems**:can not determine from the entropy whether this uncertainty is due to a high degree of data uncertainty, or whether the input is far from the region of training data.

### Prior Networks

The expected distribution $P(\omega_c|x^*,D)$ is obtained by marginalizing out the parameters $\theta$ and $\mu​$. ![image-20190324134250242](./images/image-20190324134250242.png)

if marginalizing out $\mu$,![image-20190324135636418](./images/image-20190324135636418.png)

if marginalizing out $\theta​$

![image-20190324135753583](./images/image-20190324135753583.png)

Besides, assume that a point-estimate of the parameters is sufficient given appropriate regularization and training data size.

$P(\omega_c|x^*;D)​$ $\approx​$ $P(\omega_c|x^*;\hat\theta )​$

##### Dirichlet Prior Network(DPN)

The posterior over class label is given by the mean of the DIrichlet:

![image-20190324143208184](./images/image-20190324143208184.png)

##### Training

minimize the KL divergence between the model and a sharp Dirichlet distribution focused on the appropriate class for in-distribution data, and between the model and a ﬂat Dirichlet distribution for out-of-distribution data.

![image-20190324144651431](./images/image-20190324144651431.png)

where $\widetilde\alpha_c=1$ and $\hat\alpha_c = \hat\alpha_0$, which is a hype-parameter.

### Uncertrainty Measure

**Max Probability**: full marginalization, for total uncertainty.

![image-20190324153544283](./images/image-20190324153544283.png)

**Entropy**: for total uncertainty.

![image-20190324153629890](./images/image-20190324153629890.png)

**Mutual Information**:

![image-20190324153822738](./images/image-20190324153822738.png)

![image-20190324153853936](./images/image-20190324153853936.png)

**differential entropy**: suited for distributional uncertainty.

![image-20190324154116471](./images/image-20190324154116471.png)

### Conclusion

**Prior Networks**  allows data, distributional and model uncertainty to be treated separately within a consistent probabilistically interpretable framework.

**Differential entropy of DPN** was best for OOD detection, especially when classes are less distinct.

#### More can do

can try applying DP to CV, NLP or regression tasks.

