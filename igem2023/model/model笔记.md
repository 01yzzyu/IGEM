为了描述我们的油酸诱导器控制系统的行为，我们查看了剂量-反应，即系统在不同油酸浓度下达到的稳态。在这里，我们详细描述了如何计算给定诱导剂浓度的稳态及其稳定性 。此处，为了模拟整体系统的稳态计算，我们加入荧光强度F的强度随时间的线性衰减项k，使得原方程化为$\frac{d F}{d t}=r_{seq}-k$

To describe the behavior of our oleic acid inducer control system, we  examined the dose-response, that is, the system's steady state achieved  at different oleic acid concentrations. Here, we detailed how to  calculate the steady state and its stability for a given inducer  concentration. Here, in order to simulate the steady-state calculation of the entire system, we added a linear decay term $k$ for the fluorescence intensity $F$, which modifies the original equation to:
$$
\frac{d F}{d t}=r_{\mathrm{seq}}-k
$$

$$
\text { Let } \frac{d F}{d t}=0, \quad i.e. \quad r_{\text {seq }}=k=k_{\mathrm{f}} A^2 R-k_{\mathrm{r}} C
$$
Also, let $\frac{d E g}{d t}=0 \quad r_{\mathrm{x}, E_{\mathrm{g}}}=\lambda(E_g) E_g \quad \lambda(E_ g)=E_g \lambda_{\text {min }}+\lambda_{\text {max }}-\lambda_{\text {min }}$ 

Thus,  $\frac{a_g \mathrm{K_g} R}{1+\mathrm{k_g} R}=E_g^2 \lambda_{\text {min }}+\left(\lambda_{\text {max }}-\lambda_{\text {min }}\right) E_g$

From which we get:  $E_g=\frac{-\lambda \text { min }+\sqrt{\lambda_{\text {min }}^2+\frac{4 \max _1-\lambda_{\min }}{1+k_g R^2}} \text { agkgR }}{2\left(\lambda_{\max }-\lambda_{\min }\right)}$

Letting (1), (2), (3), and (4) equal 0, when $r_{\mathrm{seq}}=k$ , we obtain:
$$
\begin{aligned}
R &=\frac{r_{\mathrm{x}, \mathrm{R}}-k}{\lambda (E_g)},\\
\end{aligned}
$$

$$
D =\frac{r_{\mathrm{x}, \mathrm{D}}}{\lambda E_ g} = \frac{b_D+\frac{a D}{1+\frac{K_0^2}{\lambda E_{g}^2}\left(b R-k+P_R(R)\right)^2}} {\lambda E_ g} \\
$$

$$
A=\frac{r_D-r_B-2 k}{\lambda E_ g}
$$

$$
C=\frac{K}{\lambda E_ g}
$$


$$
\left\{\begin{array}{l}
R=\frac{r_{\mathrm{x}, \mathrm{R}}-k}{\lambda\left(E_g\right)} \\
D=\frac{r_{\mathrm{x}, \mathrm{D}}}{\lambda (E_g)}=\frac{b_D+\frac{a D}{1+\frac{K_0^2}{\lambda (E_g)^2}\left(b R-k+P_R(R)\right)^2}}{\lambda (E_g)} \\
A=\frac{r_D-r_B-2 k}{\lambda (E_g)} \\
C=\frac{K}{\lambda (E_g)}
\end{array}\right.
$$


根据分析，我们只需解出$\lambda(E_g)$ 即可解出其他系数。 而$\lambda(E_g)$ 与R有关，即我们可以通过R得到其他变量的解析解 

根据 $\quad R=\frac{r_{x, R}-k}{\lambda (E g)}$， $\text { 将 } r_{x, R}=b_R+P_R(R) \text {. }$代入
$$
\frac{-\lambda_{min }^2+\lambda_{min} \sqrt{\lambda_{min }{ }^2+\frac{4 a_g k_g R}{1+4 k g R}(\lambda_{max} -\lambda_{min} )}}{2\left(\lambda_{\max }-\lambda_{\min }\right)}+\lambda_{\max }-\lambda_{\min } -\frac{a_R}{1+k_R}=b_R-k
$$
经过一系列化简，最后方程化为关于$s = t + c = \frac{a R}{1+K_R R } + (b_2+\lambda_{\min }-\lambda_{\text {max }}-k)$的一元三次方程组，求解即可得到$R=\frac{a_R-t}{t k_R}$ 

和$\lambda (E g)$的解析解。

Based on the analysis, we only need to solve for $\lambda\left(E_g\right)$ to determine the other coefficients. And since $\lambda\left(E_g\right)$ is related to $R$, by solving for $R$, we can derive the other quantities.
Using the relation $R=\frac{r_{x, R}-k}{\lambda E_g}$ and substituting in $r_{x, R}=b_R+P_R(R)$, we get:
$$
\frac{-\lambda_{min }^2+\lambda_{min} \sqrt{\lambda_{min }{ }^2+\frac{4 a_g k_g R}{1+4 k g R}(\lambda_{max} -\lambda_{min} )}}{2\left(\lambda_{\max }-\lambda_{\min }\right)}+\lambda_{\max }-\lambda_{\min } -\frac{a_R}{1+k_R}=b_R-k
$$
After a series of simplifications, the final equation becomes a cubic equation in terms of $s$, where $s=t+c=\frac{a R}{1+K_R R}+\left(b_2+\lambda_{\min }-\lambda_{\max }-k\right)$.

通过以上分析和推导，我们给出这一油酸诱导器系统的不同组分稳态的解析解，为进一步的研究和实验提供了一个有价值的起点

Through the above analysis and derivation, we provide analytical  solutions for the steady states of different components in this oleic  acid inducer system, offering a valuable starting point for further  research and experiments.



attribution

**Ziyang Xu (Mathematical modeling team member)**

He completed the construction of the mechanism of chemical  reaction equation of that project on the basis of full understanding of  the chemical background. Then, he proposed reaction kinetics equations  of whole process. Next, he devoted himself into learning the  transcriptional regulatory network, on the basis of relevant knowledge,  to further simplify the model, and using the algorithm of particle swarm simulation optimization model parameters. The sensitivity analysis of  the model was also carried out. To sum up, he had Successfully completed the mathematical model of the project.   

他广泛查阅资料文献，与实验组同学交流讨论，充分理解油酸诱导器的分子机制。在此基础上，他与数模组成员合作完成了该项目的反应方程机制的构建，并编写相应代码进行模型模拟。然后，他展开模型的拓展构思，从多种角度验证了模型的优越性：首先通过与native circuit的对比验证了油酸诱导器的灵敏性，再通过模拟验证了在实验层面添加FadO操作符精确控制反应阈值的可拓展性，还将模型与真实湿实验数据相结合进行了参数估计。总的来说，他的工作展现了团队合作，模型的建立和模拟达成预期目标，具备指导意义。

He extensively consulted papers and communicated with team members, gaining a thorough understanding of the  molecular mechanism of the oleic acid inducer. Based on this, he  collaborated with peers to construct  the reaction equation mechanism for the project and wrote corresponding code for model simulation. Then, he embarked on model expansion ideas,  verifying the superiority of the model from multiple angles: confirming the sensitivity of the oleic acid inducer by comparison; verifying the  expandability of precisely controlling the reaction threshold by adding  the FadO operator at the experimental level by simulation; combining the model with wet-lab experiment data for parameter estimation. To sum up, his work showcased team collaboration, and the establishment and  simulation of the model met the expected objectives, offering valuable  guidance.





为实验提供指导和解释的可拓展模型

我们本次构建的数学模型充分建模了油酸诱导器的分子机制，并在多方面提供可拓展方向，同时展示了理论优越性：我们首先通过与native circuit的对比验证了油酸诱导器的灵敏性，再通过模拟验证了在实验层面添加FadO操作符精确控制反应阈值的可拓展性，还将模型与真实湿实验数据相结合进行了参数估计，此外模型的稳定性和灵敏性分析也具有参考价值。

值得一提的是，对于在添加FadO操作符的数学模拟充分体现了干湿模型的团队合作。这一拓展操作首先由湿实验团队提出，作为适应不同人体环境的定量操作方案。随后，干实验团队对这一操作进行建模，验证了增加FadO操作符减少油酸诱导器激活时间的预期效果和各项变量随时间变化的估计值，反过来指导了进一步实验方案的选取，可以说非常成功。

The Expandable Model Providing Guidance and Interpretation for Experiments

The mathematical model we constructed this time thoroughly models the molecular mechanism of the oleic acid inducer and offers various directions for expansion, while demonstrating its theoretical superiority. We first validated the sensitivity of the oleic acid inducer by comparing it with the native circuit. Then, through simulation, we confirmed the expandability of precisely controlling the reaction threshold by adding the FadO operator at the experimental level. Additionally, we combined the model with real wet-lab data for parameter estimation, and the stability and sensitivity analysis of the model also hold referential value.

It's worth noting that the mathematical simulation of adding the FadO operator fully exemplifies the collaboration between the dry and wet lab teams. This expansion operation was initially proposed by the wet-lab team as a quantitative operational plan to adapt to different human environments. Subsequently, the dry-lab team modeled this operation, validating the expected effect of reducing the activation time of the oleic acid inducer by adding the FadO operator and estimating the values of various variables over time. This, in turn, guided the selection of further experimental schemes, which can be described as highly successful.
