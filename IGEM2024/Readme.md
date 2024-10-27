# Enhance The Synthesis of SCFAs & GLP-1 to Regulates Glycolipid Metabolism LZU-MEDICINE-CHINA_2023

The mathematical modeling of Intelligent cholesterol management system. Team: LZU-MEDICINE-CHINA 2023

Details please refer to our Team [[wiki]](https://2024.igem.wiki/lzu-medicine-china/). 

\section*{Model Assumptions and Mechanism Elucidation}

\subsection*{Glucose Sensing Mechanism}
In developing a mathematical model for glucose sensing and the production of short - chain fatty acids (SCFAs) and glucagon - like peptide-1 (GLP-1) in engineered bacteria, we have established a series of key assumptions and mechanisms. These not only form the foundation of our model but also reflect our understanding and simplification of the system's complexity.

We hypothesize that bacteria employ a mechanism similar to the PTS system in Escherichia coli for glucose sensing and uptake. In the presence of environmental glucose, this system not only facilitates glucose transport but also transduces signals intracellularly through a series of phosphorylation reactions, thereby activating or inhibiting specific gene expression. Specifically, we assume an inverse relationship between glucose concentration and intracellular signal molecule (e.g., cAMP) levels, with changes in signal molecule concentration directly modulating the activity of key regulatory factors (e.g., CRP). These regulatory factor activity changes subsequently influence the expression of SCFAs and GLP-1 related genes. This assumption allows us to directly link environmental glucose concentrations with intracellular gene expression levels, simplifying model complexity while retaining the system's core dynamic features.

\subsection*{SCFAs Production Mechanism}
The production of short - chain fatty acids constitutes a crucial component of the engineered bacteria's metabolic process. We posit that SCFAs production primarily depends on substrate availability (mainly glucose metabolic intermediates), expression levels of key enzymes (such as butyrate kinase (Buk) and butyryl - CoA:acetate CoA - transferase (But)), and product inhibition effects (where high SCFAs concentrations may inhibit their own production).

Based on these considerations, we propose that the SCFAs production rate can be described using Michaelis - Menten kinetics, with $V_{max}$ regulated by gene expression and $K_m$ reflecting substrate affinity. We include a product inhibition term that increases with SCFAs concentration and describe the expression levels of key enzymes, regulated by glucose concentration, using Hill equations. These assumptions enable us to capture the non - linear dynamics of SCFAs production while accounting for the complexities of metabolic regulation.

\subsection*{GLP-1 Expression and Release Mechanism}
The expression and release of GLP-1 form another critical component of our model. Drawing from current biological knowledge, we assume that GLP-1 expression is positively regulated by glucose concentration, GLP-1 release is a time - dependent process with inherent delays, cell density influences GLP-1 production (possibly involving quorum sensing effects), and GLP-1 undergoes extracellular degradation at a certain rate.

Based on these assumptions, we propose that GLP-1 expression rate can be described by a Hill equation with glucose concentration as the regulatory factor. We model GLP-1 release using a time - dependent function to account for potential delay effects, introduce a cell density - related term to describe possible population effects, and consider GLP-1 degradation as a first - order kinetic process. These assumptions and mechanisms allow for a more comprehensive description of GLP-1 production and release processes, while also providing a theoretical foundation for subsequent model validation and experimental design.

\subsection*{DLPC Encapsulation Effect}
DLPC (dilauroylphosphatidylcholine) encapsulation serves as a strategy for protecting and controlling the release of engineered bacteria. We make the following assumptions regarding DLPC encapsulation: it forms a semi - permeable membrane allowing selective passage of small molecules (e.g., glucose, SCFAs, and GLP-1) while blocking larger molecules and immune cells; it affects bacterial growth rate, possibly due to limitations in nutrient and metabolite exchange; it influences the release kinetics of SCFAs and GLP-1, introducing additional diffusion resistance; and its integrity may change over time, affecting its barrier function.

Based on these assumptions, we propose introducing diffusion coefficients to describe the passage of small molecules through DLPC encapsulation, modifying bacterial growth equations to include a DLPC - related inhibition term, adding diffusion terms in SCFAs and GLP-1 release equations, and considering the time - dependent integrity of DLPC encapsulation, which may affect all aforementioned processes. These assumptions enable more accurate modeling of DLPC encapsulation effects on the entire system, providing theoretical guidance for optimizing encapsulation strategies.

\subsection*{Time Delay Effects}
Biological systems often exhibit time delays from signal sensing to gene expression and protein production. Considering this, we assume the existence of time delays between glucose concentration changes and the production of GLP-1 and SCFAs. These delays may result from multiple steps including transcription, translation, protein folding, and secretion, with potentially varying delays for different processes (e.g., GLP-1 production may have longer delays than SCFAs production).

Based on these assumptions, we propose introducing delay differential equations to describe time delay effects in the model, considering distributed delays rather than fixed delays to better reflect the complexity of biological processes, and using different delay parameters for various processes (such as GLP-1 and SCFAs production). By incorporating these time delay effects, our model can more accurately describe the system's dynamic behavior, particularly its transient characteristics in response to external stimuli.

These detailed assumptions and mechanism elucidations provide a solid theoretical foundation for our model, reflecting our in - depth understanding of the system's complexity. In the subsequent model construction and analysis, we will strive to balance model complexity and interpretability based on these assumptions, aiming to achieve results with both theoretical depth and practical application value.

\section*{Model Construction}

\subsection*{Bacterial Growth Model}
Bacterial growth is a complex process influenced by multiple factors. Our model considers the effects of glucose concentration, short - chain fatty acids (SCFAs), glucagon - like peptide-1 (GLP-1), and DLPC encapsulation. The differential equation for bacterial growth can be expressed as:

\begin{equation}
\frac{dN}{dt}=rN\left(1 - \frac{N}{K}\right)-\mu N+\frac{\alpha [Glu]}{K_g + [Glu]}-\frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n}+\frac{\gamma [GLP-1]}{K_p + [GLP-1]}-\delta\cdot DLPC\cdot N
\end{equation}

This equation integrates several biological mechanisms:

Logistic growth term $rN(1 - N/K)$, describing bacterial growth under limited resources.
Basal death rate $\mu N$.
Glucose - promoted growth, described using the Monod equation $\frac{\alpha [Glu]}{K_g + [Glu]}$.
SCFAs inhibition of growth, described using the Hill equation $\frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n}$.
GLP-1's impact on growth, described using the Michaelis - Menten equation $\frac{\gamma [GLP-1]}{K_p + [GLP-1]}$.
DLPC encapsulation inhibition of growth, described using a linear function $\delta\cdot DLPC\cdot N$.

The innovation of this model lies in its comprehensive consideration of multiple factors affecting bacterial growth, particularly the incorporation of GLP-1 and DLPC effects. Recent studies suggest that GLP-1 may indirectly influence bacterial growth by affecting gut microbiota composition (Grasset et al., 2017). While DLPC encapsulation can protect engineered bacteria, it may also inhibit their growth to some extent (Zhang et al., 2019).

\subsection*{SCFAs Production Model}
SCFAs production is a key function of engineered bacteria. Our model considers factors such as substrate concentration, key enzyme expression levels, and product inhibition:

\begin{equation}
    \frac{d[SCFAs]}{dt}=\frac{V_{max}[S]}{K_m + [S]}\cdot E_{SCFAs}\cdot N - k_{deg}[SCFAs]-\frac{k_{inh}[SCFAs]^2}{K_{inh} + [SCFAs]^2}-D_{SCFAs}([SCFAs]-[SCFAs]_{ext})
\end{equation}

This equation includes the following mechanisms:

SCFAs production using Michaelis - Menten kinetics $\frac{V_{max}[S]}{K_m + [S]}$, proportional to enzyme concentration $E_{SCFAs}$ and bacterial number $N$.
Natural degradation of SCFAs $k_{deg}[SCFAs]$.
Product inhibition effect $\frac{k_{inh}[SCFAs]^2}{K_{inh} + [SCFAs]^2}$, described using the Hill equation.
SCFAs diffusion due to DLPC encapsulation $D_{SCFAs}([SCFAs]-[SCFAs]_{ext})$.

The expression level of key enzymes can be described by the following equation:

\begin{equation}
\frac{dE_{SCFAs}}{dt}=\frac{a_{SCFAs}[Glu]^n}{K_{SCFAs}^n + [Glu]^n}\cdot BCoAT-\lambda E_{SCFAs}
\end{equation}

Here we introduce the influence of butyryl - CoA:acetate CoA - transferase (BCoAT), an important factor recently discovered in research (Louis \& Flint, 2017). The expression of BCoAT can be described by the following equation:

\begin{equation}
\frac{dBCoAT}{dt}=k_{BCoAT}\frac{[Glu]}{K_g + [Glu]}\cdot\frac{1}{1 + [SCFAs]/K_{inh}}-k_{BCoAT\_deg}\cdot BCoAT
\end{equation}

This equation considers the induction effect of glucose and the feedback inhibition of SCFAs.

\subsection*{GLP-1 Expression and Release Model}
The expression and release of GLP-1 is the core function of our engineered bacteria. Our model considers time - dependent expression, the influence of glucose concentration, and the regulatory role of BCoAT:

\begin{equation}
\frac{d[GLP-1]}{dt}=\nu_{max}(1 - e^{-\lambda t})\cdot N\cdot\frac{[Glu]}{K_m + [Glu]}\cdot\frac{BCoAT}{K_p + BCoAT}-\delta [GLP-1]-\epsilon [GLP-1]N - D_{GLP-1}([GLP-1]-[GLP-1]_{ext})
\end{equation}

This equation includes the following mechanisms:

Time - dependent expression rate $\nu_{max}(1 - e^{-\lambda t})$, considering the initiation time of GLP-1 expression. This term models the gradual increase in GLP-1 production as the system responds to glucose presence over time.
The influence of glucose concentration on GLP-1 expression, described using the Michaelis - Menten equation $\frac{[Glu]}{K_m + [Glu]}$. This term captures the saturation effect of glucose on GLP-1 production, where $K_m$ is the half - saturation constant.
The regulatory role of BCoAT on GLP-1 expression, described using the Michaelis - Menten equation $\frac{BCoAT}{K_p + BCoAT}$. This term models the enzyme kinetics where BCoAT acts as a catalyst in the production of GLP-1, with $K_p$ being the half - saturation constant for BCoAT.
Degradation of GLP-1 $\delta [GLP-1]$, representing the natural breakdown of GLP-1 molecules over time.
Reabsorption of GLP-1 by bacteria $\epsilon [GLP-1]N$, where $\epsilon$ is the reabsorption rate constant and $N$ is the bacterial population.
GLP-1 diffusion due to DLPC encapsulation $D_{GLP-1}([GLP-1]-[GLP-1]_{ext})$, modeling the diffusion - driven exchange of GLP-1 between the encapsulated environment and the external medium.

The innovation of this model lies in considering the regulatory role of BCoAT on GLP-1 expression. Recent studies suggest that SCFAs may regulate GLP-1 secretion by affecting L - cell function (Christiansen et al., 2018). We hypothesize that this regulation might be mediated through BCoAT, providing a new direction for future experimental research.

\subsection*{DLPC Encapsulation Effect Model}
DLPC encapsulation is a significant innovation in our engineered bacterial system. It not only protects bacteria but also affects the diffusion dynamics of various substances. Our model is as follows:

\begin{equation}
\begin{aligned}
\frac{dN_{DLPC}}{dt}&=\sigma\left(\frac{dN}{dt}\right)\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[SCFAs]_{DLPC}}{dt}&=\frac{d[SCFAs]}{dt}-D_{SCFAs}([SCFAs]_{DLPC}-[SCFAs]_{ext})\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[GLP-1]_{DLPC}}{dt}&=\frac{d[GLP-1]}{dt}-D_{GLP-1}([GLP-1]_{DLPC}-[GLP-1]_{ext})
\end{aligned}
\end{equation}

Here, $\sigma$ is the inhibition coefficient of DLPC on bacterial growth $(0 < \sigma< 1)$. This model considers the effects of DLPC encapsulation on bacterial growth, SCFAs, and GLP-1 diffusion.

Recent studies have shown that DLPC encapsulation can significantly improve the survival rate of engineered bacteria in the gastrointestinal environment (Zhang et al., 2019). However, DLPC encapsulation may also affect bacterial metabolic activities and the release of signal molecules. Our model provides a theoretical framework for studying these complex interactions.

\subsection*{Complete Model System}
Combining all the above sub - models, we obtain a complete system of differential equations:

\begin{equation} 
\begin{aligned}
\frac{dN}{dt}&=rN\left(1 - \frac{N}{K}\right)-\mu N+\frac{\alpha [Glu]}{K_g + [Glu]}-\frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n}+\frac{\gamma [GLP-1]}{K_p + [GLP-1]}-\delta\cdot DLPC\cdot N\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[Glu]}{dt}&=-k_{uptake}N\frac{[Glu]}{K_g + [Glu]}+D_{Glu}([Glu]_{ext}-[Glu])\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[SCFAs]}{dt}&=\frac{V_{max}[S]}{K_m + [S]}\cdot E_{SCFAs}\cdot N - k_{deg}[SCFAs]-\frac{k_{inh}[SCFAs]^2}{K_{inh} + [SCFAs]^2}-D_{SCFAs}([SCFAs]-[SCFAs]_{ext})\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[SCFAs]_{DLPC}}{dt} &= \frac{d[SCFAs]}{dt} - D_{SCFAs}([SCFAs]_{DLPC} - [SCFAs]_{ext}) \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[GLP-1]}{dt} &= \nu_{max}(1 - e^{-\lambda t})\cdot N\cdot\frac{[Glu]}{K_m + [Glu]}\cdot\frac{BCoAT}{K_p + BCoAT} \\
&\quad - \delta [GLP-1] - \epsilon [GLP-1]N - D_{GLP-1}([GLP-1]-[GLP-1]_{ext})\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{dBCoAT}{dt}&=k_{BCoAT}\frac{[Glu]}{K_g + [Glu]}\cdot\frac{1}{1 + [SCFAs]/K_{inh}}-k_{BCoAT\_deg}\cdot BCoAT\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{dN_{DLPC}}{dt}&=\sigma\left(\frac{dN}{dt}\right)\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[SCFAs]_{DLPC}}{dt}&=\frac{d[SCFAs]}{dt}-D_{SCFAs}([SCFAs]_{DLPC}-[SCFAs]_{ext})\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{d[GLP-1]_{DLPC}}{dt}&=\frac{d[GLP-1]}{dt}-D_{GLP-1}([GLP-1]_{DLPC}-[GLP-1]_{ext})
\end{aligned}
\end{equation}

This complete model system captures the main dynamic characteristics of engineered bacteria in glucose sensing, SCFAs production, and GLP-1 expression and release processes, while also considering DLPC encapsulation effects. It provides a powerful tool for understanding and predicting system behavior.

The selection of model parameters referred to the data in references. We fitted the historical data and obtained the following results:
\begin{figure}[htbp]
	\centering
	\includegraphics[width=0.65\linewidth]{111.jpeg}
	\caption{Model Simulation Result}
	\label{fig:1_fig}
\end{figure}

The figure \ref{fig:1_fig} shows the GLP - 1 production of different strains. It includes the truth value and model prediction value of the chassis, the model prediction value and truth value of the engineered bacteria, and the model prediction value and truth value of the engineered bacteria encapsulated with DLPC. The horizontal axis represents time (in hours), and the vertical axis represents the production of GLP - 1. It can be seen from the figure that as time progresses, the GLP - 1 production of different strains shows different changing trends. From 6 to 12 hours, the production of the chassis is relatively low and stable, while the production of the engineered bacteria and the engineered bacteria encapsulated with DLPC is relatively high. There are certain differences between the actual production and the model prediction production of the engineered bacteria at some time points, and a similar situation exists for the engineered bacteria encapsulated with DLPC.



\section*{Model Analysis}

\subsection*{Steady-State Analysis}
Steady-state analysis is crucial for understanding the long-term behavior of the system. At steady state, the derivatives of all variables are zero. Based on our model, we need to solve the following set of nonlinear equations:

\begin{figure}[htbp]
	\centering
	\includegraphics[width=1\linewidth]{22.png}
	\caption{Steady - state Solutions - Comparison of N Values}
	\label{fig:2_fig}
\end{figure}

\begin{equation}
\begin{aligned}
0 &= rN^*(1 - \frac{N^*}{K}) - \mu N^* - \beta \frac{SCFAs^* N^*}{K_s + SCFAs^*} + \gamma \frac{GLP1^* N^*}{K_p + GLP1^*} - \delta DLPC N^* \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
0 &= -k_{uptake} \frac{N^* Glu^*}{K_g + Glu^*} + D_{Glu}(Glu_{ext} - Glu^*) \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
0 &= V_{max} \frac{E_{SCFAs}^* N^* scfa\_interp(Glu^*)}{K_m + Glu^*} - k_{deg} SCFAs^* - D_{SCFAs}(SCFAs^* - SCFAs_{ext}) \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
0 &= a_{SCFAs} \frac{BCoAT^* Glu^*}{K_{SCFAs} + Glu^*} - \lambda_E E_{SCFAs}^* \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
0 &= \nu_{max} \frac{(GLP1_{target}^* - GLP1^*) BCoAT^*}{K_p + BCoAT^*} N^* - \delta_{GLP} GLP1^* - \epsilon GLP1^* N^* - D_{GLP}(GLP1^* - GLP1_{ext}) \\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
0 &= k_{BCoAT} \frac{Glu^*}{K_g + Glu^*} \cdot \frac{1}{1 + SCFAs^*/K_{inh}} - k_{BCoAT\_deg} BCoAT^*
\end{aligned}
\end{equation}

This set of nonlinear equations is challenging to solve analytically, so we typically use numerical methods such as the Newton-Raphson method. Recent studies have shown that microbial communities may exhibit multiple steady states (Gonze et al., 2018). Therefore, we need to carefully analyze the steady-state solutions under different initial conditions and parameter settings to reveal possible multistability in the system.

It is particularly noteworthy that the target value of GLP-1 ($GLP1_{target}^*$) is a complex function determined by both time and glucose concentration. This intricate regulatory mechanism may lead to rich dynamic behaviors in the system, including potential oscillations or bistability (Karin et al., 2020).


\subsection*{Local Stability Analysis}
For each steady - state solution, we need to perform a local stability analysis. This can be achieved by calculating the Jacobian matrix and evaluating its eigenvalues. Based on our model, the elements of the Jacobian matrix $J$ are defined as:

\begin{figure}[t]
    \centering
    \includegraphics[width = 1\linewidth]{333.png}
    \caption{Bifurcation Analysis for Different Strains engineered}
    \label{fig:3_fig}
\end{figure}

\begin{equation}
J_{ij} = \frac{\partial f_i}{\partial x_j}
\end{equation}
where $f_i$ is the right - hand side of the $i$-th differential equation, and $x_j$ is the $j$-th variable ($N$, $Glu$, $SCFAs$, $E_{SCFAs}$, $GLP1$, $BCoAT$).

\subsubsection*{Derivation of $J_{11}$}
The differential equation for bacterial growth is:
\begin{equation}
\frac{dN}{dt} = rN(1 - \frac{N}{K}) - \mu N + \frac{\alpha [Glu]}{K_g + [Glu]} - \frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n} + \frac{\gamma [GLP - 1]}{K_p + [GLP - 1]} - \delta \cdot DLPC \cdot N
\end{equation}
We calculate $J_{11} = \frac{\partial f_N}{\partial N}$ as follows:

\begin{equation}
\begin{aligned}
J_{11} &= \frac{\partial}{\partial N}\left(rN(1 - \frac{N}{K}) - \mu N + \frac{\alpha [Glu]}{K_g + [Glu]} - \frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n} + \frac{\gamma [GLP - 1]}{K_p + [GLP - 1]} - \delta \cdot DLPC \cdot N\right)\\
&= r\left(1 - \frac{2N}{K}\right) - \mu + 0 - 0 + 0 - \delta DLPC\\
&= r\left(1 - \frac{2N}{K}\right) - \mu - \beta \frac{SCFAs}{K_s + SCFAs} \times 0 + \gamma \frac{GLP1}{K_p + GLP1} \times 0 - \delta DLPC\\
&= r\left(1 - \frac{2N}{K}\right) - \mu - \beta \frac{SCFAs^*}{K_s + SCFAs^*} + \gamma \frac{GLP1^*}{K_p + GLP1^*} - \delta DLPC
\end{aligned}
\end{equation}

By calculating the complete Jacobian matrix and solving its characteristic equation, we can obtain the system's eigenvalues. The characteristic equation of the Jacobian matrix $J$ is $\vert J - \lambda I \vert = 0$, where $\lambda$ is the eigenvalue and $I$ is the unit matrix. We can solve this equation by numerical methods (such as the QR algorithm) to obtain the eigenvalues.

If the real parts of all eigenvalues are negative, then the steady state is locally stable.

Recent studies have indicated that the stability of microbial communities can be significantly affected by environmental fluctuations (Coyte et al., 2015). Therefore, we need to consider how the system's stability changes under different environmental conditions, such as varying glucose or DLPC concentrations.

When the glucose concentration changes, it affects the terms related to glucose in the model, such as $\frac{\alpha [Glu]}{K_g + [Glu]}$, thus changing the elements of the Jacobian matrix and then affecting the eigenvalues.

For the change of DLPC concentration, it affects the term $-\delta \cdot DLPC \cdot N$ in the model, also changing the Jacobian matrix and finally affecting the system's stability.

The steady - state parameters of engineered bacteria encapsulated with DLPC (Engineered\_DLPC) can be obtained by calculation, but the Jacobian matrix shows that they are not stable. The visualization results are as follows:

This figure \ref{fig:2_fig} presents a comparison of N values between engineered bacteria (Engineered) and engineered bacteria encapsulated with DLPC (Engineered\_DLPC) under steady - state conditions. It can be observed from the figure that, under different conditions (the horizontal axis does not clearly show the relevant condition labels), there are differences in the N values of the two types of bacteria, with the value range from approximately $10^{-13}$ to $10^{1}$.


\subsection*{Bifurcation Analysis}
Bifurcation analysis is a powerful tool for understanding the qualitative changes in the behavior of a dynamical system as a function of certain parameters. In our model of engineered bacteria, we consider the following key parameters for bifurcation analysis:
1. External glucose concentration $Glu_{ext}$
2. DLPC concentration
3. BCoAT expression rate $k_{BCoAT}$

\subsubsection*{Mathematical Derivation for $GLP - 1$ Concentration as a Function of $Glu_{ext}$}
We start from the GLP - 1 expression and release model:

\begin{equation}
\frac{d[GLP - 1]}{dt} = \nu_{max}(1 - e^{-\lambda t}) \cdot N \cdot \frac{[Glu]}{K_m + [Glu]} \cdot \frac{BCoAT}{K_p + BCoAT} - \delta [GLP - 1] - \epsilon [GLP - 1]N - D_{GLP - 1}([GLP - 1] - [GLP - 1]_{ext})
\end{equation}

At steady state, $\frac{d[GLP - 1]}{dt} = 0$. So we have:


\begin{equation} 
\begin{aligned}
\nu_{max}(1 - e^{-\lambda t}) \cdot N \cdot \frac{[Glu]}{K_m + [Glu]} \cdot \frac{BCoAT}{K_p + BCoAT} - \delta [GLP - 1] - \epsilon [GLP - 1]N - D_{GLP - 1}([GLP - 1] - [GLP - 1]_{ext})  &= 0\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
[GLP - 1](\delta + \epsilon N) + D_{GLP - 1}[GLP - 1] - D_{GLP - 1}[GLP - 1]_{ext} &= \nu_{max}(1 - e^{-\lambda t}) \cdot N \cdot \frac{[Glu]}{K_m + [Glu]} \cdot \frac{BCoAT}{K_p + BCoAT}\\
\end{aligned}
\end{equation}
\begin{equation} 
\begin{aligned}
\frac{\nu_{max}(1 - e^{-\lambda t}) \cdot N \cdot \frac{[Glu]}{K_m + [Glu]} \cdot \frac{BCoAT}{K_p + BCoAT} + D_{GLP - 1}[GLP - 1]_{ext}}{\delta + \epsilon N + D_{GLP - 1}}  &=  [GLP - 1]
\end{aligned}
\end{equation}


This gives us the expression for the steady - state concentration of $GLP - 1$ as a function of various parameters including $[Glu]$. When we specifically consider the external glucose concentration $Glu_{ext}$, we can plot the bifurcation diagram of $GLP - 1^*$ as a function of $Glu_{ext}$.

\subsubsection*{Analysis of Bifurcation Points}
Saddle - node bifurcations and Hopf bifurcations are important bifurcation points that can occur in our system. For saddle - node bifurcations, we consider the conditions under which the number of steady - state solutions changes. This typically involves analyzing the derivatives of the steady - state equations with respect to the bifurcation parameter (in this case, $Glu_{ext}$).

Let's assume we have a function $F(Glu_{ext}, [GLP - 1]) = 0$ representing the steady - state equation for $GLP - 1$. The saddle - node bifurcation occurs when $\frac{\partial F}{\partial [GLP - 1]} = 0$ and $\frac{\partial^2 F}{\partial [GLP - 1]^2} \neq 0$.

For Hopf bifurcations, we consider the conditions related to the eigenvalues of the Jacobian matrix evaluated at the steady - state. If the real part of a pair of complex conjugate eigenvalues changes sign as the bifurcation parameter varies, then a Hopf bifurcation occurs.

\subsubsection*{Effect of DLPC Concentration on the System}
The effect of DLPC concentration on the system can be analyzed through its influence on the various equations in our model. For example, in the bacterial growth model:
\begin{equation}
\frac{dN}{dt} = rN(1 - \frac{N}{K}) - \mu N + \frac{\alpha [Glu]}{K_g + [Glu]} - \frac{\beta [SCFAs]^n}{K_s^n + [SCFAs]^n} + \frac{\gamma [GLP - 1]}{K_p + [GLP - 1]} - \delta \cdot DLPC \cdot N
\end{equation}
As DLPC concentration changes, the term $-\delta \cdot DLPC \cdot N$ changes, which affects the growth rate of bacteria and subsequently the overall dynamics of the system.

In the GLP - 1 expression and release model, the term $D_{GLP - 1}([GLP - 1] - [GLP - 1]_{ext})$ is affected by DLPC concentration. As DLPC concentration increases, the diffusion resistance for $GLP - 1$ may change, affecting its release and thus the steady - state concentration of $GLP - 1$.

\subsubsection*{Effect of BCoAT Expression Rate on the System}
The BCoAT expression rate $k_{BCoAT}$ affects the system through its influence on the expressions of key enzymes and ultimately on the production of GLP - 1. From the equations for the expression of key enzymes and BCoAT:
\begin{equation}
\frac{dE_{SCFAs}}{dt} = \frac{a_{SCFAs}[Glu]^n}{K_{SCFAs}^n + [Glu]^n} \cdot BCoAT - \lambda E_{SCFAs}
\end{equation}
\begin{equation}
\frac{dBCoAT}{dt} = k_{BCoAT} \frac{[Glu]}{K_g + [Glu]} \cdot \frac{1}{1 + [SCFAs]/K_{inh}} - k_{BCoAT\_deg} \cdot BCoAT
\end{equation}
As $k_{BCoAT}$ increases, the production of BCoAT and subsequently the expression of key enzymes related to SCFAs production may change. This in turn affects the production of GLP - 1 through its influence on the substrate availability and enzyme kinetics.

The figure \ref{fig:3_fig} respectively shows the bifurcation analysis results of different strains (engineered chassis and engineered\_dlpc) under different conditions. For the steady - state concentration of GLP - 1, with the change of external glucose concentration (Glu\_ext), different strains show different changing trends. For example, within certain ranges of glucose concentration, the GLP - 1 concentration of the engineered chassis strain shows complex fluctuations, while the changing trend of the GLP - 1 concentration of the engineered\_dlpc strain is different. In addition, it also shows the change of GLP - 1 concentration with the change of BCoAT expression rate.




\subsection*{Sensitivity Analysis}
Sensitivity analysis can help us determine which parameters have the most significant impact on system behavior. We can calculate sensitivity coefficients:

\begin{figure}[b]
	\centering
	\includegraphics[width=1\linewidth]{image.png}
	\caption{Range Sensitivity Analysis of GLP - 1 Steady State Concentrationt}
	\label{fig:4_fig}
\end{figure}

\begin{equation}
S_{ij} = \frac{\partial x_i}{\partial p_j} \cdot \frac{p_j}{x_i}
\end{equation}

\begin{equation}
S_{log} = \frac{\partial \log x_i}{\partial \log p_j} = \frac{\partial x_i}{\partial p_j} \cdot \frac{p_j}{x_i}
\end{equation}

where $x_i$ is the $i$-th variable, and $p_j$ is the $j$-th parameter.

For our model, important parameters include:\\
1. Bacterial growth rate $r$\\
2. Maximum GLP-1 expression rate $\nu_{max}$\\
3. SCFAs degradation rate $k_{deg}$\\
4. BCoAT expression rate $k_{BCoAT}$\\


The figure \ref{fig:4_fig} conducts a range sensitivity analysis on the steady - state concentration of GLP - 1 for engineered bacteria (Engineered), engineered bacteria encapsulated with DLPC (Engineered\_dlpc), and chassis bacteria (Chassis). The results show that different strains have different sensitivities to parameters (such as $\nu_{max}$, $k_{deg}$, $k_{BCoAT}$). With the change of these parameter values, the steady - state concentration of GLP - 1 shows different degrees of change, and the changing trends and magnitudes among different strains also vary.

By calculating the sensitivity coefficients of these parameters, we can identify the key control points of the system. This is crucial for subsequent experimental design and system optimization.



## Project Summary:

We are concerned about T2DM, a chronic disease with serious complications and a rising incidence rate worldwide. We focus on BcoAT to enhance the synthesis of its SCFAs and program the glucose responsive secretion of GLP-1 to build a synthetic biological reactor through the method of synthetic biology, with the probiotic ECN1917 as the chassis. When blood sugar levels rise after each meal, GLP-1 is released to rapidly lower blood sugar to baseline levels. In order to achieve the above functions, this project designed a GLP-1 recombinant protein, with PelB as the lead sequence connected to GLP-1 to enhance its extracellular secretion function. DnaK, a key protein of the blood glucose control module, is expressed at the tail of GLP-1 through flexible linker peptides to achieve its programmed release. During the experimental phase, the release of GLP-1 regulated by glucose concentration was validated through gradient dilution and ELISA quantitative detection. 
