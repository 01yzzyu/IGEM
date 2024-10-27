
# Cholesterol-management-model_LZU-CHINA_2023

The mathematical modeling of Intelligent cholesterol management system. Team: LZU-CHINA 2023

Details please refer to our Team [[wiki]](https://2023.igem.wiki/lzu-china/). 



## Mechanism

From the oleic acid induction mechanism, we can divide the expression of the FadR promoter into the following two scenarios:

![mech](https://github.com/StatXzy7/cholesterol-management-model_LZU-CHINA_2023/blob/main/igem/model/figures/mech.png)	

​	With oleic acid: $\rightarrow$ acyl-CoA A $\rightarrow$ FadR protein departs from promoter PfadB $\rightarrow$ gene expresses normally, $\beta$-oxidation initiates.

​	Without oleic acid: $\rightarrow$ FadR protein binds to promoter PfadB $\rightarrow$ gene expression is inhibited.

## Model Establishment

We establish the ordinary differential equation model for the change rates of FadR(R), FadD (D), acyl-CoA (A), sequestered complex (C), growth-associated enzyme(Eg), and fluorescent protein(F).

![mech](https://github.com/StatXzy7/cholesterol-management-model_LZU-CHINA_2023/blob/main/igem/model/figures/model_equation.png)	




## Model Simulation

Summary: The model simulation show the effectiveness of the oleic acid inducer, and we can precisely control its reaction threshold by adding FadO operator. 

To model simulation, we firstly compared the difference between the oleic acid inducer and native circuit, validating the high efficiency of oleic acid inducer. Secondly, by adjusting the affinity of FadR to inhibit Ep synthesis in the model, we simulated the influence of increasing system FadO operators, confirming it makes the oleic acid inducer harder to activate, enabling precise control over the whole system. We also referred to the experiment data for further model parameter fitting and interpretation. The predicted F growed rapidly with the increase in OA(oleic acid) concentration, suggesting that the oleic acid inducer adaptively regulates its active intervention quantity in varying degrees of high-fat dietary situations. In addition, we conducted stability and sensitivity analysis on the model system, laying the groundwork for subsequent research. All the figures are shown in our [[wiki]](https://2023.igem.wiki/lzu-china/).
