# Chemistry repo for humid air discharge simulations

## Started with the following files, made by Behnaz:
- 98air_2water_chemistry_old.txt: This contains the humid air chemistry with 2% water vapour in the gas composition.
- Dry_air_chemistry_old.txt: This is the file without any water molecule reactions

## Reaction data I added
- 98air_2water_chemistry_RONS_Norberg.txt: This contains the humis air chemistry as above. But I added the reactions from Table 1 of the following paper: https://iopscience.iop.org/article/10.1088/0963-0252/24/3/035026. However, I could not find the cross-section data for reactions R1, R2, R9, R14, R15. I think I need to find them using the LXCAT database. 
- *Immediate next step*: Obtain the cross-section data for the reactions(including the missing reactions, with help from others), run the data through bolsig- to get the rate constants

## To do/ to ponder:
- I see two reaction sets that can be made:
	- RONS with dry air.
	- RONS in humid air chemistry.
- Based on the above point, we need to "complete" two different chemistry sets:
	- A fully contained humid air chemistry.
	- and further, a fully contained RONS chemistry added to it.
- Are the reactions we add, sufficient to obtain/predict/model the physics we want to?
	- We can check that in the following way:
		- Make a chemistry set, perform a simulation with the conditions of interest.
		- Look at some observables/verifiables and compare them with stuff in literature.
		- Perform some back of the envelop calculations/tests that can be used to argue that the reaction set is sufficient (if not complete).
- *Note*: One of the important RONS is H2O2. But H2O2 cannot form in dry air due to the absence of water molecules. So we cannot have H2O2 related reactions in Dry air chemistry.
- Some reactions are temperature dependent, but we take them to be constant for 300K, so they need to be extended to be a function of temperature change.
- (WHAT ELSE?)

