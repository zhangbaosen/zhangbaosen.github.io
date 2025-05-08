# 1 Introduction

The purpose of this lab is to get you familiar with power
system transient stability analysis using computer software tools. In
this lab, you will learn the basic concepts of transient stability and
associated assessment methods. Case studies will be performed for you to
understand the nature of the power system transient stability behavior,
including generator 'swing' characteristics and associated voltage and
power oscillation dynamics. Through this lab, you will gain an improved
understanding on the various factors that affect the transient stability
of power systems.

---

## 1.1 Background

### 1.1.1 Power System Transient Stability

Transient stability is the ability of a power system to remain in
synchronism when subjected to large transient disturbances. These
disturbances may include faults on transmission elements, loss of load,
loss of generation, or loss of system components such as transformers or
transmission lines. Although many different forms of power system
stability have emerged and become problematic in recent years, transient
stability still remains a basic and important consideration in power
system design and operation. While it is true that the operation of many
power systems is limited by phenomena such as voltage stability or
small-signal stability, most systems are prone to transient instability
under certain conditions or contingencies and hence the understanding
and analysis of transient stability remain fundamental issues. Also,
transient instability can occur in a very short time frame (a few
seconds), leaving no time for operator intervention to mitigate
problems. It is therefore essential to deal with the problem in the
design stage or severe operating restrictions may result.

Following a disturbance, synchronous machine frequencies undergo
transient deviations from synchronous frequency and power angles change.
The objective of transient stability study is to determine whether or
not the machines will return to synchronous frequency with new
steady-state power angles. In many cases, transient stability is
determined using “swing curves” plotted for a generator subjected to a
particular system disturbance. Trace “a” shown below shows that the
generator power angle recovers and oscillates around a new equilibrium
point. It is deemed to be transiently stable. However, in trace “b”, the
power angle increases aperiodically and is considered transiently
unstable. What factors determine whether a machine will be stable or
unstable? How can the stability of large power systems be analyzed? If a
case is unstable, what can be done to enhance stability? These are some
of the questions to be solved in this lab.

![](https://www.dropbox.com/scl/fi/xrtbm1ic17rn1v2aff5ts/stable_vs_unstable.jpeg?rlkey=k5gfjolx3nex6dwsbyhczsl1x&dl=1)

figure 1. Typical swing curves.

### 1.1.2 Methods of Transient stability Analysis

You may have learned the theory of swing equation and equal area
criterion in the lecture. It can be used to conduct analytical studies
on small systems. For a practical system with large numbers of
generators, transmission units and loads, the time-domain based
simulation method is a more applicable approach.

For stability assessment, the power system is normally represented
using a positive sequence model. The network is represented by a
traditional positive sequence power flow model that defines the
transmission topology, line reactances, connected loads and generation,
and pre-disturbance voltage profile.

Generators can be represented with various levels of detail, selected
based on such factors as length of simulation, severity of disturbance,
and accuracy required. The most basic model for synchronous generators
consists of a constant internal voltage behind a constant transient
reactance, and the rotating inertia constant. This is the so-called
classical representation that neglects the machine physical construction
factors (damper windings, saturation, etc), the generation controls
(excitation and governor systems) and the details of the prime mover.
More detailed models have been utilized in commercial transient
stability programs.

Transient stability studies are commonly performed after power flow
studies. Based on the pre- disturbance system profiles, time-domain
simulation can be conducted. The results are examined, usually through a
graphical plotting, to determine if the system remains stable and to
assess the details of the dynamic behavior of the system. Typical
procedures for the transient stability analysis are as follows.

1. Collect data of network topology and power system components for
   power flow studies

   - one-line diagram of the network

   - transmission line and transformer data

   - shunt capacitors and reactors data

   - bus load data

   - generator real power output, scheduled voltage

2. Collect specified data for transient stability studies

   - Dynamic data: Includes model types and associated parameters for
     generators, motors, protections, and other dynamic devices and their
     controls.

   - Switching data: Includes the details of the disturbance to be
     applied. This includes the time at which the fault is applied, where the
     fault is applied, the type of fault and its fault impedance if required,
     the duration of the fault, the elements lost as a result of the fault,
     and the total length of the simulation.

   - Program control data: Specifies such items as the type of
     numerical integration to use and time-step.

   - System monitoring data: This specifies which quantities are to be
     monitored (output) during the simulation.

3. Solve power flow for the system

4. Perform transient stability studies

   - Perform time domain simulation.

   - Plot system swing curves to determine if the system remains
     stable.

   - Repeat the above process for different fault locations and
     different scenarios.

   - Document all study results

## 1.2 Required Software

The following software is installed on the computers that are
provided in the laboratory. The following installation instructions are
provided if you care to install the software on your own computers. It
is your responsibility to get this working on your own hardware as
little support will be provided by the laboratory staff as it can become
too time consuming. Both Matlab/Simulink and the PSAT toolbox should be
able to be installed on Windows, macOS and Linux.

### 1.2.1 Matlab/Simulink

As a UW student, you have access to Matlab. More information [here](https://it.uw.edu/uware/matlab/)

### 1.2.2 PSAT

The Power System Analysis Toolbox (PSAT) is a Matlab toolbox for
electric power system analysis and simulation.

![](https://www.dropbox.com/scl/fi/4o52xkq3wq8yizvulqii0/psat_logo.png?rlkey=9x5vxg0fix55r28uoswyxw7eq&dl=1)

figure 2. PSAT (Power System Analysis Toolbox)

#### 1.2.2.1 Installation Instructions

1. Download the Power System Analysis Toolbox (PSAT) from [here](http://faraday1.ucd.ie/psat.html)

2. Extract the downloaded `.zip` file to the Matlab
   toolbox directory at `Program files/MATLAB/2025a/toobox/` by
   default on Windows. There should be a similar directory for other
   operating systems.

3. Add a PSAT toolbox installation path to the same directory that
   you extracted the toolbox too using the `Set Path` button on
   the toolbar in Matlab.

![](https://www.dropbox.com/scl/fi/s8a5g5u47tkg3hlj220hn/matlab_set_path.png?rlkey=l5ftaqftb0tcba36kzq3egim2&dl=1)

figure 3. Set PSAT toolbox path in MATLAB.

4. Launch PSAT by typing `psat` in the Matlab command window
   and after a few moments the PSAT control windows should be displayed as
   shown below.

![](https://www.dropbox.com/scl/fi/e1d7uws9cdd3eofnv2gx8/psat_window.png?rlkey=2n96qvgy3chgkbcr0lae8c21x&dl=1)

figure 4. PSAT main command windows.

# 2 Lab Procedure

The system used for this experiment consists of 9 buses and 3
generating stations. It is so called WSCC 3-machine, 9-bus system and is
widely used in power system transient stability studies. The system is
shown in figure 5.

![](https://www.dropbox.com/scl/fi/61w3ix9b47u83nr9wngng/the_system.png?rlkey=4t862jsn22w462oya6j9a3dn3&dl=1)

figure 5: The test system (The WSCC 3-machine, 9-bus
system)

## 2.1 PSAT Familiarization

PSAT is a free Matlab toolbox for electric power system analysis and
control. It includes power flow, continuation power flow, optimal power
flow, small signal stability analysis and time domain simulation. All
operations can be assessed by means of graphical user interfaces (GUIs)
and a Simulink-based library provides a user friendly tool for network
design.

### 2.1.1 Load the Basecase

1. Download the .zip file from below which contains the Base Case that
   will be used for this lab and extract it somewhere you can find in your
   user space. It is usually easiest if you put the file in your default
   Matlab workspace. The extracted .zip file contains a single .mdl file
   titled `Lab_4_Basecase.mdl`.

#### [Base Case Download](https://www.dropbox.com/scl/fi/uf4g9xv2ml177v0bqxbp1/Lab_4_Basecase.mdl?rlkey=vg4fegltuppf156eig301gbwb&dl=1)

2. In the PSAT command window click on the `Open Data File`
   button as shown below or navigate the menus to
   `File/Open/Data File`.

![](https://www.dropbox.com/scl/fi/v3g4cabmcxgau3moeygge/open_data_file.png?rlkey=q0v2aaoym174gi0m4zif1skc1&dl=1)

figure 6. Open Data file button.

3. From the opened Load Data File screen, navigate the directory
   structure to where you have the .mdl file extracted. Make sure that the
   Filters is to `PSAT Simulink (.mdl)` and select the correct
   Basecase file under `Files in current path:` and then click
   on the `Load` button.

**Note:** The mdl file contains the single-line 9-bus
system diagram in a Simulink file format which was constructed with the
PSAT simulink library. When we `Load Data file`, PSAT
extracts the data from the Simulink and creates another file which ends
with a `.m`, which it then uses in its simulation
calculations. You can review some of this conversion process in the
Matlab Command Window.

![](https://www.dropbox.com/scl/fi/yok94wbevq60m2lobno0j/load_data_file.png?rlkey=lc5x67qkvxhipobcinfjr2lm6&dl=1)

figure 7. Load a simulink .mdl file into the PSAT
toolbox for analysis.

4. To view and/or edit the single-line diagram of the system in
   Simulink, you can go to `File/Open/Simulink Model` and open
   the same downloaded .mdl file.

**Note:** If you make changes to the Simulink model you
need to first save the new model in the .mdl format and then make sure
that you `Load Data file` in PSAT before carrying out any
simulation.

**Note:** The Simulink library blocks may have an
Unrecognized functions or variables error and are highlighted in red. As
we are not using the Simulink solver this does not matter. If the red
highlight bothers you, you can try simulating the model in Simulink,
nothing will really simulate but it will create the missing variables
and the errors will go away.

**Note:** You can double click on the blocks in the
model to edit their `Block Parameters`.

![](https://www.dropbox.com/scl/fi/gtwmany9siim6gwz1xvkn/simulink_model.png?rlkey=zitw2548al0yni91joiy40v69&dl=1)

figure 8. An open .mdl file in Simulink where the
system can be edited.

5. Change the system frequency to 60 Hz in the main PSAT window as this
   is the typical system frequency in North America, it defaults to 50Hz as
   the PSAT software is written somewhere in Europe where that is the
   typical system frequency.

![](https://www.dropbox.com/scl/fi/px89krxqwluopc179umfi/base_freq.png?rlkey=kmpynx4j4mwb2t83v2z6dn8fb&dl=1)

figure 9. Change the system base frequency to
60Hz.

### 2.1.2 Simulate the Basecase

6. To complete a Power Flow Analysis of the system press the “Power
   Flow” button in the PSAT main window, the status of the simulation gets
   logged in the Matlab Command Window.

![](https://www.dropbox.com/scl/fi/dmzdmp2nhstprufu0hoce/power_flow.png?rlkey=leqcem28a0ktjsgs6lkovzvgz&dl=1)

figure 10. Complete a Power Flow Analysis of the
System.

7. Press the button shown below to view the Static Report of the Power
   Flow Analysis results.

![](https://www.dropbox.com/scl/fi/953m3u3pofeasbxhdba1i/static_report_button.png?rlkey=0znky3nky0le30e9ezlqjb9rl&dl=1)

figure 11. Open the Static Report of the Power Flow
Analysis.

8. An example of the Static Report results are shown below.

**Note:** In the upper parameter boxes the highlighted
entries indicate the values of the selected bus.

**Note:** You can change the units displayed in the
boxes by clicking on the unit displayed at the top of each box.

**Note:** For Active and Reactive Power you can also
select where to display the following

- G - The generated power on the bus.
- L - The comsumed power on the bus.
- I - Shows both: generated as a positive number and consumed as a
  negative number.

**Note:** You can click on the icon to open up a
bargraph plot to compare the results of each bus.

**Note:** You can generate/save a Static Report by
pressing on the Report button. The report output format and other
options can be configured by selecting what you want under the
`Preferences Menu`.

![](https://www.dropbox.com/scl/fi/5v65krbfo80541sgf1a0e/static_report.png?rlkey=ga6978guchgl04o71ao59ms7j&dl=1)

figure 12. An example Static Report.

### 2.1.3 Basecase results

9. Compare your Power Flow Analysis results in the Static Report with
   the reference results shown below.

|       |              |           |            |            |             | POWER FLOW RESULTS |
| ----- | ------------ | --------- | ---------- | ---------- | ----------- | ------------------ |
| Bus # | Voltage (pu) | phase (°) | P_gen (pu) | Q_gen (pu) | P_Load (pu) | Q_Load (pu)        |
| ---   | ---          | ---       | ---        | ---        | ---         | ---                |
| 1     | 1.02500      | 9.28000   | 1.63       | 0.06654    | —           | —                  |
| 2     | 1.04000      | 0.00000   | 0.71641    | 0.27046    | —           | —                  |
| 3     | 1.02500      | 4.66480   | 0.85       | -0.1086    | —           | —                  |
| 4     | 1.02580      | 3.71970   | —          | —          | —           | —                  |
| 5     | 1.01590      | 0.72754   | —          | —          | 1           | 0.35               |
| 6     | 1.01270      | -3.68740  | —          | —          | 0.9         | 0.3                |
| 7     | 1.02580      | -2.21680  | —          | —          | —           | —                  |
| 8     | 0.99563      | -3.98880  | —          | —          | 1.25        | 0.5                |
| 9     | 1.03240      | 1.96670   | —          | —          | —           | —                  |

Table 1. Reference Power Flow results for the Base Case.

10. Change the Report output format to Excel by going to
    `Preferences/Select Test Viewer` and selecting
    `Excel` and clicking on OK. Generate the Report and Save it
    with an appropriate name. Have a look at the report to see what is
    included.

## 2.2 Transient Stability Analysis

Transient stability examines the impact of disturbances on power
systems considering the operating conditions. The analysis of the
dynamic behavior of power systems for the transient stability gives
information about the ability of a power system to sustain synchronism
during and after a disturbance.

In this task, a fault will be placed on one of the buses to
demonstrate how the system behaves. A system can recover if a fault is
cleared quickly enough before the whole system collapses.

11. Add a fault to bus 4 by doing the following.
    1. With the Simulink model of the system open also open the PSAT
       simulink library by clicking on the appropriate button in the PSAT main
       window.

![](https://www.dropbox.com/scl/fi/jj5getqgrl72rf5hnv65j/psat_library_button.png?rlkey=lqqh4i1o5cft17f2zk5h4bdzj&dl=1)

figure 13. PSAT Simulink library button.

```
2. In the base case Simulink model, double click on bus 4 (the thick
   black line) to open the `Block Parameter` window for Bus 4.
   Change the `Number of outputs:` from 2 to 3. You will then
   see another output appear on the bus 4 in the Simulink model.
```

![](https://www.dropbox.com/scl/fi/zsgzzwnci87asjuaq2mk3/bus_4_new_output.png?rlkey=4yx3qgodlc3kmunze5wpfcyjv&dl=1)

figure 14. Adding a new output on bus 4.

```
3. From the PSAT Simulink library, either drag and drop or copy and
   paste a `Fault` (from the Faults and Breakers library) to
   your base case some where near bus 4.
```

![](https://www.dropbox.com/scl/fi/q3071jb0u7j5uxwa6dvbj/insert_fault.png?rlkey=vphn93mdp0qimpulxv3ubtrj9&dl=1)

figure 15: Faults and Breakers catalogue of the PSAT
Simulink library.

```
4. Wire the newly added Fault to the new output your created on bus
   4.
```

![](https://www.dropbox.com/scl/fi/rsymzmgl6nsg9clrvup3o/wire_fault.png?rlkey=0q2ox6q89joezxkjqmzm5csgv&dl=1)

figure 16: Connect the new Fault to bus 4.

```
5. Double click the fault and setup the following parameters:


   - Power, voltage and frequency: \[100 230 60\]
   - Fault time: 1.0
   - Fault clearing time: 1.15
```

**Note:** The duration of the fault will be the
`Fault clearing time` minus the `Fault time` as
both of the times above are the times in the simulation that the events
occur.

```
6. Save this new case with a new appropriate name making sure to
   save it as an .mdl file so it can be loaded into PSAT.
```

12\. Load the new .mdl Data File you just created by clicking on the
`Open Data File` button in the PSAT main window. Make sure to
adjust the file type `Filter` so `.mdl` files can
be seen.

13. Go to Settings in the PSAT main window and check the selection of
    `Convert PQ bus to Z` to increase the simulation’s stability.

![](https://www.dropbox.com/scl/fi/2f49ek74ine2fwny21kj3/convert_PQ_to_Z.png?rlkey=auc0btn9zzajv8qntkj6fda9j&dl=1)

figure 17: Convert PQ bus to Z.

14. Run a Time Domain simulation in PSAT by clicking on the button shown
    below. The Time Domain solution requires an initial Power Flow solution
    before it is run and it will do it automatically if a current solution
    is not available.

![](https://www.dropbox.com/scl/fi/o8irha2bjej7qkkohpmqg/time_domain.png?rlkey=x0uctv8gdd86mem7fbke8nci3&dl=1)

figure 18: Run a Time Domain simulation.

15. Using the PSAT `Plot tool`, plot the following and
    save the resulting graphs using a screen capture tool like
    `Snip & Sketch` to save the plot as an image file to
    include in your Postlab.

    **Note:** The first 3 plots below have a fault clearing
    time of 0.15s.

    **Note:** You can change the length of the simulation
    from the PSAT main window as shown below.

    ![](https://www.dropbox.com/scl/fi/orgasyeaw1xrvfeqjqnlk/end_time.png?rlkey=x2ys47b8kstxia2ttuonjw6pf&dl=1)

    figure 19. Simulation End Time.

    **Note:** You can examine the resulting waveforms in
    more detail by using the plots zoom controls.
    1. **Power Angle at Generator Buses**: Select the power
       angle (δ) of the 3 synchronous generators (ie. delta_Syn_1) to plot them
       against time. Use delta_Syn_1 as reference angle by selecting it in the
       appropriate box. Click on the `Plot` button to generate the
       graph in the available space. Use the default simulation end time of 20
       seconds.

![](https://www.dropbox.com/scl/fi/at6it6wvgkbg9rsyx9n92/psat_plot.png?rlkey=di1f10dtp17kioay4o0xt0pv1&dl=1)

figure 20. Select the parameters that you would like
to plot. The power angles of the 3 generators shown.

```
2. **Voltage at Generator Buses:** Select the bus
   voltages that the 3 synchronous generators are attached to (ie. V\_Bus 1)
   to plot them against time. Click on the `Plot` button to
   generate the graph in the available space. Change the simulation end
   time to 3 seconds (or use the Zoom tool) so what is occuring to the
   voltages during the fault can be seen.

3. **Power at Generator Buses:** Select the 3
   synchronous generator power quantities (ie. p\_Syn\_1) to plot them
   against time. Click on the `Plot` button to generate the
   graph in the available space. Change the simulation end time back to 20
   seconds.

4. **Unstable - Power Angle at Generator Buses:** The
   longest fault time duration that the system can recover from and remain
   stable is named as critical fault clearing time. Run the simulation
   while increasing the fault duration by 0.01 second increments to find
   the critical fault clearing time for bus 4. Record the critical fault
   clearing time in the appropriate places in the results table and plot
   the power angle (δ) of the 3 generators when the system goes
   unstable.
```

#### 

### 2.2.1 Postlab Questions

Is the system stable? Explain why.

Explain what is occurring in the generator plots for both the voltage and the power, that you obtained, when a fault is applied to bus 4 between 1.0 to 1.15 seconds of the simulation.

## 2.3 Impact of Fault Location

The amount of time a fault is sustained before the system collapses
can vary depending on where in the system the fault occurs. Therefore
the system’s critical fault clearing time should be different if a fault
occurs in a different location (ie. on a different bus).

16. Using a similar procedure as the previous section to complete the
    table below, determine the systems critical fault clearing time when a
    single fault occurs at each of the 9 buses. Record your results in the
    table provided on your results sheet.

    **Note:** You already completed bus 4 in the previous
    section.

|       |                  | CRITICAL FAULT CLEARING TIME     |
| ----- | ---------------- | -------------------------------- |
| Bus # | Bus Voltage (kV) | Critical fault clearing time (s) |
| ---   | ---              | ---                              |
| 1     | 18.0             |                                  |
| 2     | 16.5             |                                  |
| 3     | 13.8             |                                  |
| 4     | 230.0            |                                  |
| 5     | 230.0            |                                  |
| 6     | 230.0            |                                  |
| 7     | 230.0            |                                  |
| 8     | 230.0            |                                  |
| 9     | 230.0            |                                  |

Table 3. The systems critical fault clearing time for a fault occuring
at each bus separately.

#### Note

It is important that the fault voltage rating matches the voltage
rating of the bus.

![](https://www.dropbox.com/scl/fi/e16se2p91o0rcing42gyp/bus_voltage.png?rlkey=jlp8jdhi92st532t8jc410jkc&dl=1)

figure 21. The rated bus voltage.

![](https://www.dropbox.com/scl/fi/i22fprv2pphgq8luiugn4/fault_voltage.png?rlkey=pnho1lecxsb7uhn2u8e5ucff7&dl=1)

figure 22. The rated fault voltage.

### 2.3.1 Postlab Questions

Which fault location is most susceptible to cause a system
transient that will lead to an unstable system? What are the potential
reasons for that?

Explain why doing a fault location scan, like was completed in
the lab, could be useful.

## 2.4 Impact of Line Tripping

If a circuit breaker protecting a transmission line trips either
before or during a fault event the critical fault clearing time will be
effected.

For this case, we will start with the same case that we used in the
`Transient Stability Analysis` where we had a fault on bus 4.
However for this new case we will add a breaker in the line from bus 7
to bus 8 that will open before the fault occurs and then close again
after the fault transient has subsided. The goal of this task is to see
how a change in the system effects the critical fault clearing time.

17. Add a Breaker to the line from bus 7 to bus 8 by doing the
    following.
    1. Open the `.mdl` file that you saved in the
       `Transient Stability Analyses` section where you just added a
       fault on bus 4 into Simulink. As this is the case we want to compare
       to.

    2. Open the PSAT Simulink library and copy a `Breaker`
       from the `Faults & Breakers` catalogue someone near
       either bus 7 or bus 8 in your base case.

![](https://www.dropbox.com/scl/fi/jfaw75d0pt48xjlq2qp13/insert_breaker.png?rlkey=rtxgwubogipllsvo2qmy71q3y&dl=1)

figure 23. A Breaker in the Faults and Breaker
catalogue of the PSAT Simulink library.

```
3. Delete the wire connecting the bus to the line element and place the
   new Breaker in series with the line by wiring the breaker to both the
   line element and the appropriate bus.
```

![](https://www.dropbox.com/scl/fi/tmf7pgfrmlyoqabg1id0e/wire_breaker.png?rlkey=1bx7q8lpl6eytznn50nz7mxii&dl=1)

figure 24. A breaker inserted in series with the line
that connects bus 7 to bus 8.

```
4. Double click on the `Breaker` element and the
   `Block Parameters` for the `Breaker` will open.
   Set the parameters as shown below.
```

![](https://www.dropbox.com/scl/fi/kel2vps2i3hbadcwlu4qe/breaker_settings.png?rlkey=sc7iidvdri86uh1ub2a4bpcxp&dl=1)

figure 25. The breakers parameter settings.

```
5. Save the new case with a new appropriate name as a `.mdl`
   file.
```

18\. Load the newly saved file into PSAT using the PSAT command
window.

19. Like you did in the previous sections, determine the system’s new
    critical fault clearing time when the newly added Breaker is open.
    Record your results in the table provided on your results
    sheet.

### 2.4.1 Postlab Questions

How does a line being removed from the system effect the systems transient stability? Explain.

## 2.5 Impact of Inertia

The inertia of a generator will effect how fast the power angle
changes when a transient occurs which means that it will either take
longer or shorter for that generator to reach the point of instability
depending if the inertia is increased or decreased.

For this case, we will again start with the same case that we used in
the `Transient Stability Analysis` where we had a fault on
bus 4. However for this new case we will increase the inertia of all
three of the generators of the system to demonstrate its effect on the
critical fault clearing time.

20. For this test we are going to double the inertia of all three of
    the generators in the system. Follow the steps below to change the
    inertia of a generator.
    1. Start again by reopening the `.mdl` file that you
       saved in the `Transient Stability Analyses` section where you
       just added a fault on bus 4 into Simulink. As this is the case that we
       want to compare to.

    2. Double click the generator to open the
       `Block Parameter` window. Double the `Inertia`
       value that is shown below.

       **Note:** You can use math in the parameters so you can
       simply add a 2\* infront of the inertia parameter to double it.

![](https://www.dropbox.com/scl/fi/ipd6bub24macil6uc0nre/gen_inertia.png?rlkey=erohmge5vppo76duogj8qt55l&dl=1)

figure 26. Setting the Inertia of a generator.

```
3. Modify all 3 generators so that their inertia is
   doubled.

4. Save the new case with a new appropriate name as a
   `.mdl` file.
```

21. Load the newly saved file into PSAT using the PSAT command
window.

22. Like you did in the previous sections, determine the systems new
    critical fault clearing time when the systems generators inertia are all
    doubled. Record your results in the table provided on your results
    sheet.

### 2.5.1 Postlab Questions

How does the inertia of all of the generators in the system
effect the systems transient stability? Explain.
