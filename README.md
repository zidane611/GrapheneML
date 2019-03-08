# GrapheneML
Accelerated Discoveries of Mechanical Properties of Graphene Using Machine Learning and High-Throughput Computation

This repo contains the training dataset and a trained KNN model for the work above. 
- raw_data.csv
-- 1440 data points including 4 features and 3 targets
- normalized_data.csv
-- Feature values normalized between 0 and 1
- graphene.regressor
-- Trained model for mechanical property predictions

Example:  
A defect free graphene at temperature 100 K under stain rate of 0.001 ps<sup>-1</sup> in the armchair direction can be represented by  
0，0，0.001，100  
After normalization, the data is  
0，0，0.387755，0.0825688  
To predict the mechanical properties for this case, the trained model can be used directly with the python program below:
```python
import numpy
norm_feature = numpy.array([0,0,0.387755,0.0825688]).reshape(1, -1)

from joblib import load
regr = load('graphene.regressor')
prediction = regr.predict(norm_feature)
```
The predicted fracture strain, fracture strength and Young's modulus are 0.16, 97.1 GPa and 965.3 GPa, respectively. The MD simulation results are 0.155, 96.2 GPa and 962.9 GPa, respectively.
