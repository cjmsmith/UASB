# UASB, Fall 2018
### Ian Cullings, Ananya Gangadhar, Cara Smith, Nina Blahut
#### October 26, 2018


[**CEO: This is a very good report. Great job adjusting the format where it makes sense. The only thing that seems out of place is the Gates Grant description...but I'm not sure where else you would put that..so it is fine how it is. Requires only minor edits.**]

## Table of Contents
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


  - [Abstract](#abstract)
  - [Introduction](#introduction)
  - [Literature Review and Previous Work](#literature-review-and-previous-work)
  - [Timeline of UASB](#timeline-of-uasb)
      - [Summer 2016](#summer-2016)
      - [2016](#fall-2016)
      - [Spring 2017](#spring-2017)
      - [Summer 2017](#summer-2017)
      - [Fall 2017](#fall-2017)
      - [Spring 2018](#spring-2018)
      - [Summer 2018](#summer-2018)
  - [Fall 2018 Goals](#fall-2018-goals)
- [Lab Experiments](#lab-experiments)
  - [Tapioca Tests](#tapioca-tests)
    - [Experimental Apparatus](#experimental-apparatus)
    - [Set Up](#set-up)
    - [Experimental Procedure](#experimental-procedure)
    - [Cleaning Procedure](#cleaning-procedure)
  - [ProCoDa Method File](#procoda-method-file)
  - [Results](#results)
  - [Analysis](#analysis)
  - [Design Modifications](#design-modifications)
- [Gates Grant](#gates-grant)
- [Future Work](#future-work)
- [EPA Funding Assurance](#epa-funding-assurance)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## Abstract
Since Spring 2017, the AguaClara Upflow Anaerobic Sludge Blanket (UASB) Team has been working on a detailed design of a pilot-scale UASB reactor. A UASB reactor treats wastewater anaerobically and produces biogas as a byproduct. Working towards that goal, the team has created Python code to record the design process and calculations for this AguaClara UASB.

For Fall 2018, the team will continue design work on the UASB with the goal of completing a full design.  Once this is done, the team will begin preparations for fabrication and implementation of the UASB at the Ithaca Area Wastewater Treatment Plant (IAWWTF).  Another goal for the semester is to begin researching flow patterns through the UASB to optimize treatment and prevent short-circuiting.

## Introduction

Many countries in the world lack proper access to wastewater treatment and release their wastewater directly into the environment untreated. The organic and fecal matter present in domestic water can cause harmful effects to the environment and on human health.

Organic matter in wastewater is broken down by bacteria that feed on it, consuming oxygen in the process. Depletion of dissolved oxygen levels in water can threaten and kill aquatic life.  Additionally, nutrients such as nitrogen and phosphorus present in high concentrations in wastewater can lead to explosive algal growth in waterways, which depletes oxygen levels and can create dead zones through a process known as [eutrophication](https://oceanservice.noaa.gov/facts/eutrophication.html). Fecal matter in wastewater can also cause the spread of infectious waterborne diseases like cholera, salmonella, and diarrhea, making it a huge threat to public health.

The current technology in the United States for treating municipal wastewater requires long retention times, large land areas and high monetary and energy costs. The large infrastructure and associated costs make conventional wastewater treatment unfeasible for small communities, who then resort to directly discharging their wastewater into streams. This problem can be addressed with the use of Upflow Anaerobic Sludge Blanket (UASB) reactors.

UASB reactors are used for primary treatment and clarify wastewater by removing suspended solids organic matter ([Chong et. al, 2012](https://www.sciencedirect.com/science/article/pii/S0043135412002400?via%3Dihub)). Organic carbon in the wastewater flowing up through the sludge blanket is consumed by the microbes residing within the sludge.  UASB reactors also produce methane as a by-product of anaerobic digestion.  This methane can be captured and burned for energy production or heating.

UASB reactors rely on gravity to clarify wastewater and biological processes to remove organic matter and convert it to biogas. They are less energy intensive than other forms of preliminary wastewater treatment that use aerobic processes.

In January 2017, a novel gravity-powered UASB reactor was designed by AguaClara for the EPA People, Prosperity and the Planet (P3) [Student Design Competition proposal](https://docs.google.com/document/d/1geug1EyFjCRLQgO79vTOXUUFia3RBw3bhaIHPUiqu44/edit?usp=sharing). This reactor was designed to improve the accessibility of wastewater treatment for small communities. The proposed UASB reactor design identified areas to improve conventional reactor design, making the system cheaper and easier to fabricate and implement globally. The team later applied for Phase II funding from the same organization to support development and implementation of additional reactors for testing.

In the Fall 2018 semester, the team will focus on benchtop testing of the various components of the UASB reactor, and simulate the movement of water through the sludge blanket in order to better understand flow patterns within the reactor and possible failure modes.

[**CEO: The intro is very well written!**]

## Literature Review and Previous Work

UASB reactors are currently being used for wastewater treatment to varying degrees of success. In 2005, Sato et. al performed a case study done on 16 full-scale UASBs in the Yamuna River Basin in India [(Sato, 2005)](https://www.sciencedirect.com/science/article/pii/S0301479705002860). The study found that the concentration of pollutants in effluent from these UASBs usually did not meet the effluent standards of most developing countries (Sato, 2005). Despite the failings of UASB reactors, the study is significant in showing that these reactors are an affordable option for wastewater treatment.   The study also emphasizes the importance of redesigning a UASB reactor to produce acceptable discharge standards.

One of the main drawbacks of UASB reactors is that there is a long initial start-up period before steady-state conditions are achieved; this time is usually in the range of several months [(Wang, 2018)](https://link.springer.com/article/10.1007%2Fs11356-017-0457-5
). Methods to decrease startup time include increasing load, optimizing temperature for anaerobic digestion, using a sufficient amount of sludge, and adding metal or an inert carrier. Wang et al. concluded that the addition of $FeCl_3$ during the initial stage of the UASB reactor start-up to promote granulation combined with the addition of Zero Valence Ions (ZVI) during the middle stage of reactor start-up is highly effective in reducing the initial start-up period (Wang, 2018). Once the team fabricates the pilot UASB, studies similar to this one will be useful in strategizing how to speed up the start-up period to test UASB quicker.

In typical UASB reactors, studies have found that removal of total suspended solids (TSS) is inversely proportional to upflow velocity within the reactor.  This parameter is difficult to minimize since decreasing upflow velocity requires decreasing flow rate, which reduces the total amount of wastewater treated, reducing reactor efficiency. *Seghezzo et al.* compared efficiency of reactors at various upflow velocities and various sludge blanket heights. At lower upflow velocities, the height of the sludge blanket did not impact efficiency significantly, provided the height was roughly 2/5 the height of the tank. At higher upflow velocities, it was found that a sludge blanket height of 0.92m in a 2.5m tall reactor provided optimal conditions compared to higher sludge blanket heights.  [(Seghezzo, 2018)](https://www.researchgate.net/publication/266880587_The_effect_of_sludge_discharges_and_upflow_velocity_on_the_removal_of_suspended_solids_in_a_UASB_reactor_treating_settled_sewage_at_moderate_temperatures). The model reactor at these dimensions removed 80% of the TSS and 90% of the volatile suspended solids (VSS).  The overall findings of the paper suggested lower upflow velocities and taller sludge blankets are optimal for UASB efficiency.

[MAYBE RESOLVED?-AG-Show the units and chemical formulas in appropriate format. You may find something useful here: https://confluence.cornell.edu/display/AGUACLARA/Style+Guide+for+Figures%2C+Tables%2C+and+Equations]

Additionally, [Lattinga et. al. (1993)](https://ac.els-cdn.com/096085249390038D/1-s2.0-096085249390038D-main.pdf?_tid=c83c2cd0-507e-4bba-a527-852fb5b2d0ed&acdnat=1537204715_6f79df9120ffd2cb0883ce08f1828336) highlights how the process of granulation within the UASB reactor is positively impacted by high upflow velocities within the UASB reactor and low hydraulic retention times. Both of these studies will be important when designing for UASB efficiency.  

[**CEO:Do these studies contradict each other? How will you optimize both in your desgin?**]


## Timeline of UASB
#### Summer 2016
The UASB team was formed in the Summer of 2016. At that point, the objective of the team was to design and implement a functional lab-scale UASB reactor to treat synthetic blackwater. Blackwater [**CEO: one word or 2? be consistent**] is wastewater from toilets. In the summer of 2016, the UASB team constructed four small-scale UASB reactors and found that those small-scale reactors could successfully treat synthetic wastewater. The team also found that increased wastewater concentration and higher residence times resulted in higher biogas removal and increased Chemical Oxygen Demand (COD) removal.

[RESOLVED-AG-Define COD (chemical oxygen demand).]

#### Fall 2016
In the fall of 2016, the UASB team underwent several changes. First, the team altered the design of the small-scale UASB reactors by implementing shorter and narrower influent lines. The team also changed the synthetic wastewater recipe. More specifically, the team substituted glucose with insoluble carbon compounds. The team also researched retention time in the reactors with fluoride tracer tests, and found a HRT of 3.22 hours in one of the reactors (close to the target of 4 hours).

#### Spring 2017
During the spring of 2017, the team worked on assessing the efficiency of two modifications to the UASB reactor: plate settlers and the submerged gas collection lid. After conducting granule settling tests, the team was unable to conclude whether or not plate settlers significantly improve solid retention time. The team also conducted a Submerged Gas Capture Lid Test and concluded that a check valve would be useful to allow for continuous collection into a gas tank without loss of biogas.

#### Summer 2017
In the summer of 2017, the UASB team continued with similar research and testing to that of the Spring 2017 semester. This time, the team determined that plate settlers were not required for a full scale reactor. Instead, a smaller settling apparatus, such as a sloped exit weir, can achieve similar sludge retention time (SRT).

#### Fall 2017
During the fall of 2017, the UASB team made several strides. Firstly, the team settled on the critical design assumptions for the fabrication of a UASB reactor at the IAWWTF . The critical design assumptions were as follows: a reactor diameter of 3 feet, a reactor height of 7 feet, a 4 hour hydraulic residence time, a flow rate of .036 L/s. The  team also designed a biogas capture lid. In this system, as biogas is produced in the reactor, it displaces water out from under the lid. Gas is then stored there until it is manually removed.

The team also wrote Python calculations in Jupyter notebook (available on GitHub) to estimate biogas production based on COD input.

Next, the team decided to add plate settlers back to the effluent tube. Plate settlers are intended to prevent dislodged granules from escaping the reactor. The fall 2017 team also worked on designing a sludge weir for the UASB reactor.

<!--[EM: Fix grammar and spelling errors. Addressed NB]-->

#### Spring 2018
UASB continued efforts to improve the design of the pilot-scale UASB reactor in Spring 2018. A major area of focus was the influent flow system. After extensive research, the team chose top influent flow instead of bottom influent flow to prevent clogs. Next, the team decided to incorporate pulse flow into the reactor to achieve the desired flow of .03 L/s. The team proposed two methods to produce pulse flow: a tipping bucket design and a siphon.

UASB also worked on biogas production. The team wrote code to estimate biogas production rate based on the flow rate through the reactor, the COD concentration of influent, and the temperature of the reactor. The team decided on a gas bag system to store biogas as it is flexible, easy to connect to the reactor, affordable, and easily transported. The team also wrote code to determine the required volume and dimensions for the lid of the biogas system. The team also looked into a fats, oils and greases (FOG) removal system. The concluded that manual skimming of FOG could always be used as a backup option.

Next, the team developed the design for the pilot UASB reactor's sludge sampling and removal system. For the sludge weir, the team chose a tube with a 6 inch diameter jutting out of the reactor at the predicted height of the sludge blanket at a downwards angle with two valves.

Lastly, the team wrote code to calculate the optimal size of the pilot UASB reactor's tube settler, the number of plates required, and the overall height of the settling arm.

#### Summer 2018
The summer team continued work on the hydraulic design of the UASB system.  The major design project was creating the tipping bucket system to deliver wastewater in pulses.  The system consists of a pivoting bucket which fills with wastewater before tipping and delivering the wastewater in a large pulse at a high flow rate.  After brainstorming the idea, the team designed and tested models to determine optimal design and flow rates for the system.  The team also continued developing code for the entire system, and made a Computer Aided Design (CAD) [model of the UASB reactor](https://cornell47.autodesk360.com/g/shares/SH7f1edQT22b515c761e1224485004ae7e44?viewState=NoIgbgDAdAjCA0IDeAdEAXAngBwKZoC40ARXAZwEsBzAOzXjQEMyzd1C0IBOAEx4GYeAFgBsAWgBMjAGY8xQgKwTxjLl3H8A7KoBGEABwQd-IZrQBfEAF0gA) using Fusion 360.

## Fall 2018 Goals

In the fall semester of 2018 [**CEO: as above specify the semester even in paragraph**-Addressed CJMS], the team will finalize the UASB reactor design before fabrication. First, bench top tests will be performed to study the flow patterns through the sludge, which will be simulated using tapioca. Tapioca was chosen to use for a model of a sludge blanket because tapioca has material properties similar to that of sludge.
These tests will allow us to test various reactor and influent conditions and check for failure. The UASB reactor design can be modified based on the results of the tapioca tests. The team plans on consulting Dr. Monroe Weber-Shirk and Dr. Todd Cowen for the details of the hydraulic design of the reactor and conducting literature searches for reactor designs. After these steps, the final dimensions of the reactor, upflow velocity, thickness of the sludge blanket and number of influent pipes can be determined.


One major part of the design process will be writing code to model designs of the reactor.  Since the UASB reactor can have many design approaches, it is important to create flexible code that can test different positions and determine the required parameters.  The team will be writing this code within the design manual and testing it rigorously to get the best design solution.

Because AguaClara is moving from Fusion 360 to Onshape, UASB also plans to create an updated CAD model of the UASB reactor on OnShape. If this cannot be accomplished the semester, it will be accomplished next semester. Two members of the team have volunteered to be trained on OnShape within the upcoming months. The team will also consult with AIDE to see if there is a simple way to move the design from Fusion. [**CEO: There is supposedly an easy way to move some designs from Fusion to Onshape...I don't know exactly what it is but I know it's possible...**]-Adressed CJMS

The final goal of the team in the fall 2018 semester is to begin prepping for fabrication.  This includes locating and ordering materials, making fabrication and safety plans, and learning fabrication techniques such as plastic welding.  With this groundwork laid, the team can begin fabrication easily and have a full plan on how to proceed.

Our full task map is included below:
<div style = “text-align:center”>

![Task Map](https://github.com/AguaClara/UASB/blob/master/Images/task_map_F18.jpg?raw=true)

[The task map above looks good, but using a flowchart instead of a photo might be better. Addressed IC]
# Lab Experiments

## Tapioca Tests
The major research focus the fall semester of 2018 was running a series of “tapioca tests” to get a better idea on how influent wastewater will travel through a sludge blanket in the current design for the UASB reactor. Because it would be costly and wasteful to use an actual sludge blanket during the early testing stages, the team first chose to use tapioca to model a sludge blanket. Tapioca has similar material properties to sludge, is inexpensive, and readily available.

### Experimental Apparatus

A scaled-down model UASB reactor was fabricated over the summer using a PVC pipe. Geometric similarity was maintained. A flat PVC sheet was then welded on the  bottom of the pipe segment, thus creating a usable UASB prototype. An effluent line was drilled in at about 70% of the way to the top of the reactor. A pipe attached to this opening allows excess water to exit the reactor. An image of this model reactor (hereby christened Bethany) is shown below.

![the prototype UASB reactor](https://github.com/AguaClara/UASB/blob/master/Images/UASB_prototype.png?raw=true)

### Set Up

Place the small-scale UASB reactor on the lab bench. Use brackets to secure a 5/8 inch pipe so that it is positioned perpendicular to the bottom of the reactor and it extends to about .5 cm above the bottom of the small-scale reactor. Attach the influent pipe to a 600 RMP. Attach a red dye pump to the influent line of water.

### Experimental Procedure

1. Prepare tapioca by mixing equal parts tapioca and water.
2. Wait ten minutes for tapioca pearls to expand in water.
3. Pour tapioca into Bethany until it is ¾ full.
4. Use leveler to ensure that the influent pipe is perpendicular to the bottom of the reactor.
6. Inject a plug of red dye to the influent water.  
7. Use ProCoda to pump water into Bethany through the influent pipe.
8. Observe the flow of red dye through the tapioca layer and the movement of the tapioca blanket.
9. Repeat steps 1 through 8 using different flow rates and length of flow rate pulse.
10. Clean up.

### Cleaning Procedure
1. Use strainer to separate water and tapioca.
2. Refrigerate leftover tapioca.
3. Dump water down the drain.
4. Rinse out the small-scale UASB reactor.

## ProCoDa Method File

The ProCoDa file used for the Tapicoa tests has three states:

![Setp](https://github.com/AguaClara/UASB/blob/master/Images/statel.PNG?raw=true)

* Off: Full system off, shuts down both pumps
* On: Pump runs at set flowrate in pulses separated by pulses at the set time
* Pause: System turns off during set time and then turns on

The set points are listed below:

![Setp](https://github.com/AguaClara/UASB/blob/master/Images/setp.PNG?raw=true)

* ON: Turns system on
* OFF: Turns system off
* Flow rate: Desired flow rate of system, in $ml/s$
* Tubing size: Integer corresponding to tubing size, found on [AguaClara Confluence](https://confluence.cornell.edu/display/AGUACLARA/Auto+Tutorial+for+Peristaltic+Pumps)
* Pump speed: calculates desired pump speed (in rpm) using ProCoDa function
* Run time: The time the pump should run at the calculated speed.  For the experiments this was 3 seconds.
* Pause time: The time the system remains in the pause state before running.  For the experiments, this was 30 seconds.

For our the initial experiments, red dye was loaded into the system manually by running the pump until a set amount of dye was visible in the tubing, then injected through running the water pump.  In future quantitative tests this will be controlled through ProCoDa as well using the second pump.

## Results

During tests, the team uses ProCoDa to pump water through an influent pipe down the center of the small-scale reactor. The influent pipe extends to about a half of a centimeter above the reactor’s bottom. Once influent water hits the bottom of the reactor, it travels upwards through the layer of tapioca. Then, when the the water level in the reactor reaches the height of the effluent tube, water exits the reactor

The behavior of the mini-reactor during tapioca tests has been somewhat on par with that of a functional UASB reactor. In the team’s initial tests with a 100 RPM pump, there was no observable fluidization of the the tapioca blanket; however, the transition to a 600 RPM pump and subsequent increase of influent flow rate resulted in the partial fluidization of the tapioca. The layer of tapioca did not lift entirely off the bottom of the reactor, but there was noticeable stretching of the tapioca layer as influent wastewater traveled through it, and the sludge blanket did indeed stretch uniformly.

![Marbles](https://github.com/AguaClara/UASB/blob/master/Images/marble_reactor.jpeg?raw=true)

[**CEO: do you have data for this section? if you have measurements of expansion they could be useful here to compare with values from the literature you might expect** ]

## Analysis
In a properly functioning UASB reactor, the wastewater will spread out evenly as it travels through the sludge blanket, so that it has the maximal possible surface contact with the granules in the sludge blanket. This has not happened in the tests yet. The team added red dye to influent water in order to follow the path of water through the model reactor.

![Preliminary Dye Tests](https://github.com/AguaClara/UASB/blob/master/Images/UASB_Red_Dye_Tapioca_Test.PNG?raw=true)
######Above, the tapioca is not an even shade of pink because the dye has not evenly distributed itself due to preferential pathways
The reactor has been slightly lifted off the lab bench so a camera can be placed below and record the water movement at the opening of the influent tube. In doing so, the team observed the formation of preferential pathways through the tapioca layer. Preferential pathways occur when incoming wastewater forms a tunnel through the sludge blanket and shoots through the tunnel instead of distributing evenly throughout the sludge blanket. As a result of preferential pathways, wastewater only gets contact with a very small portion of the surface area of the sludge blanket and hydraulic retention time is decreased, so the wastewater is not adequately cleaned. The testing showed the formation of preferential pathways along the walls of the reactor and along the influent tube, which can be seen in the tapioca — only portions of which made contact with the dye.

[**CEO: add a caption to the figure to better show why this image is included. As it is now, it simply shows what the experiment looked like but without explanation of what the reader should be getting from it** -Adressed CJMS]

[RESOLVED-AG-Can you provide some diagrams to illustrate the results you have? And when comparing the properly functioning UASB reactor and the result you have, can you also explain more about it and the possible reasons? You can also separate results from analysis.]

## Design Modifications
Firstly, modifications were made to the influent system. Instead of one large opening for wastewater to flow out the influent pipe, the team has capped this opening and drilled 4 holes near the bottom of the point, guessing that influent wastewater will now be forced to spread out, thereby decreasing the likelihood of preferential paths from forming.

![Modified Influent Pipe](https://github.com/AguaClara/UASB/blob/master/Images/Modified_Influent_Pipe_Drawing.JPG?raw=true)

In order to begin collecting quantitative data, the team set up a photometer. The photometer will be used in testing to determine how water is flowing through the sludge blanket. A plug of red dye will be injected to the influent pipe in the UASB. Then, the photometer will measure the concentration of red dye coming out of the model UASB reactor in the effluent tube. If the reactor is functioning properly, the red dye will flow evenly through the model sludge blanket, so all the dye will come out of the effluent tube at the same time, which will be indicated by a spike of red dye concentration coming out of the effluent tube. The photometer will be used to measure whether or not the red dye concentration in the effluent tube is changing as expected for a functional UASB.    [**CEO: mention briefly how the photometer will be used** -addressed NB]

The decision to use a photometer to collect quantitative data made tapioca an unsuitable sludge blanket because tapioca gives off a residue in water, which makes it too cloudy for the photometer to measure red dye concentration. Chia seeds were chosen as a replacement to model the sludge blanket since they do not degrade as quickly as tapioca does.

In order to prepare the model sludge blanket from chia seeds, the team placed the chia seeds in water and waited approximately 20 minutes for the seeds to expand. The chia seeds were somewhat buoyant in water. Some of the chia seeds sank to the bottom of the container and others stuck together on the water's surface. When the team placed the expanded chia seeds inside the model UASB reactor and began to run water through the model UASB reactor, it became clear that chia seeds are not an effective model for the sludge blanket. Firstly, chia seeds are to sticky; the seeds stick to each other, which prevents water from flowing through them, and they stick to the walls and sides of the reactor. Secondly, the chia seeds were prone to flowing out of the effluent tube, which caused frequent clogging and would render photometer readings meaningless.

![Chia Seed Tests](https://github.com/AguaClara/UASB/blob/master/Images/The%20UASB%20Apocalypse.jpg?raw=true)

Upon realizing that chia seeds were not usable for modeling the sludge blanket, the team decided that glass beads would be a possible alternative. Due to time constraints, the team was unable to order new materials for the sludge blanket model, but there were glass marbles in the lab, which the team decided to test as a model sludge blanket.

![Marbes](https://github.com/AguaClara/UASB/blob/master/Images/marble_reactor.jpeg?raw=true)

The glass marbles were about 1 cm in diameter. The glass marbles did not work as a model for sludge granules because they were too heavy for the influent water to lift them. While the glass marbles were not useful for modeling the sludge blanket, they did give the team the opportunity to use the photometer to measure the read dye concentration of water in the model UASB effluent.

Next semester, the team plans to purchase glass beads that share a similar size and density to that of sludge granules. The team also plans to run tests with actual sludge from a local brewery.


## Gates Grant
UASB has written and submitted a grant proposal for the Gates Grand Challenges Round 22 for Innovation for WASH in Urban Settings. In the proposal, the team suggested a system for wastewater treatment in developing urban settings by initially separating domestic wastewater into its two components: blackwater (water from flush toilets) and greywater (water from sinks, laundry, etc.). Then the blackwater would be treated via our UASB reactor.

An eighteen-month plan for the implementation of an UASB reactor in Honduras was developed, along with an estimated budget. If chosen, UASB would receive $100,000 for Phase I and up to one million dollars if also selected for Phase II.
The schematic below summarizes the idea proposed in the Gates Proposal.
![Schematic for System Idea](https://github.com/AguaClara/UASB/blob/master/Images/gates%20grant%20schematic.png?raw=true)

The proposal can be read [here](https://github.com/AguaClara/UASB/blob/master/README.md).

# Future Work

While quite a lot was accomplished this semester, UASB discovered that there are still a lot of elements of the UASB reactor that need to be researched and finalized within a short amount of time; therefore, the team structure will be changing next semester. In final discussions, the team decided that the main priority for next semester is the design and fabrication team, and not the fluids research.  While this research was still valuable for increasing the teams knowledge of how upflow reactors work, the main focus of the team should be creating a working prototype to test in the wastewater treatment plant.  As such, the team recommends that the main UASB team completely focus on design, and if there is room for another team created, we will recruit a full research team to continue the research work done this semester.

### Design Team Goals

The main task for the fabrication team will be to finish design of the UASB system, create a CAD model in OnShape, and begin fabrication so the system can be implemented.  This will primarily involve writing flexible design code that incorporates many parts of the UASB system together and runs calculations for all of them.  As such, it would be desirable to recruit students with design experience, fluids experience, and fabrication experience to this team.  

### Research Team Goals

The main task for the research team is to continue the testing done this semester. This includes reducing preferential pathways, working on influent design, and integrating the tipping bucket system worked on during the summer into the design. This would also involve helping the fabrication team with elements they think should be tested out in lab before being implemented fully into the actual reactor.

### Key Contacts

Due to a shift in leadership, the team decided to list some key contacts for the UASB project so all members will know who to reach out to.  They are summarized in the table below.

| Name                | Role                                                              | Email                             |
| ------------------- | ----------------------------------------------------------------- | --------------------------------- |
| Dr. Ruth Richardson | Faculty Advisor                                                   | water.ruth@gmail.com              |
| Ed Gottlieb         | Wastewater plant operator, primary contact at Wastewater facility | EGottlieb@cityofithaca.org        |
| Robert Cleeton      | Contact at Anheuser-Bush, source for anaerobic granules           | robert.cleeton@anheuser-busch.com |



# EPA Funding Assurance
This publication [article] was developed under Assistance Agreement No. SU-83926801 awarded by the U.S. Environmental Protection Agency to Cornell University. It has not been formally reviewed by EPA. The views expressed in this document are solely those of [name of recipient or names of authors] and do not necessarily reflect those of the Agency. EPA does not endorse any products or commercial services mentioned in this publication.