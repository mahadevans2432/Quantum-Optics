# State population transfer in Rubidium-87 using STIRAP

## Abstract

In this repository, we explore methods to complete state transfer in Rubidium 87 5S and 5P levels. The methods employed for the same is STIRAP and we specifically look into a case of very unequal peaks for the pulses while also simulating examples of $N$-STIRAP and cavity-STIRAP. We successfully simulated an adiabatic state population transfer with an efficiency of $99.5\%$ with coherent Rabi pulses of Blackman shape with peaks of 100 MHz and 10 MHz with single photon detuning of 1 GHz and two photon detuning of 2.18 MHz over a 25$\mu$s timescale.

## Description of the N_STIRAP class

Here described is the <code>class N_STIRAP()</code> and it's member functions the exact code for which is written in [here](STIRAP.ipynb). All functions which start with an underscore in their name are private and are not meant to be accessed from outside the class. Following is the description of the public member functions and their arguments.

* <code>self.efficiencys()</code>: The output returned is the efficiency for the current parameter set defining this STIRAP instance.

* <code>self.plot(plot_pulses)</code>: here the input is a boolean which if given True will print the graph of the guess pulses of [blackman](https://en.wikipedia.org/wiki/Window_function#Blackman_window) shape. This is set to True by default. This function will show the final plot of the transfer of populations between the states.

* <code>self.scipy_opti_result(plot_pulses)</code>: here the input is again a boolean which when True will print the optimized graph pulses (which remain blackman here) and is set to True by default. The function will also show the final output of the population transfers between the states along with a printed log of the optimization details. The procedure used here is the [Powell method](https://docs.scipy.org/doc/scipy/reference/optimize.minimize-powell.html#optimize-minimize-powell) on the variables of the pulse widths, pulse starting times, and the $n$-photon detuning ($\delta$).

* <code>self.robustness(error=0.01)</code>: quantifies the change in efficiency by inducing error (input parameter) to the non optimized variables hence giving a measure of robustness. The aim is to keep this below 0.01 to have a robust STIRAP transfer.

This is also capable of simulating cavity STIRAP with the very final state being linked to a cavity by taking $2g(t) = \Omega_{N-1\to N}$ for the simulation and the value of $\Gamma$ for the final state being the same as the cavity decay $\kappa$ since they are essentially equivalent. The argument to initiate this is to use <code>is_cavity = True</code> in the initialization of the class instance. In this the emission rate is an additional graph that is plotted which is essentially just $2\kappa|\langle N|\psi\rangle|^2$.

Examples of demonstration of this class can be found in this [Jupyter notebook](STIRAP.ipynb). The method used is simple discretized matrix exponentiation for solving the Schrodinger's equation. The analysis included in the report was generated using codes present in this [Jupyter notebook](Rough/3-level-unqeual-peak-analysis.ipynb).

## Detailed report
The detailed report can be found [here][Weizmann_Intern_Report.pdf].

## Contributions
* [Prof. Barak Dayan](https://www.weizmann.ac.il/chembiophys/dayan/) (Supervisor)
* [Dr. Jeremy Raskop](https://www.researchgate.net/scientific-contributions/Jeremy-Raskop-2125704905) (Supervisor)
* [Mahadevan Subramanian](https://mahadevans2432.github.io/)
* [Drishti Baruah]()

