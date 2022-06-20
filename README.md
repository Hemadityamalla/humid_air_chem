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



## Reactions list
(I decided to take the following cross-sections for the following gases:)
N2 & O2 : Phelps

H2O: Itikawa
| Reaction                          | Type                       | Rate (SI units, unless specified)            | Reference                     |
|-----------------------------------|----------------------------|----------------------------------------------|-------------------------------|
| e + N2 -> e + e + N2+             | Ionization                 | f($\epsilon$)                                | Phelps DB                     |
| e + O2 -> e + e + O2+             | Ionization                 | f($\epsilon$)                                | Phelps DB                     |
| e + O2 + O2 -> O2- + O2           | 3-body attachment          | f($\epsilon$)                                | Phelps DB                     |
| e + O2 -> O + O-                  | Attachment                 | f($\epsilon$)                                | Phelps DB                     |
| e + O2 -> e + O2_a                | Excitation                 | f($\epsilon$)                                | Phelps DB                     |
| e + N2 -> e + N_2D + N            | e- impact dissociation     | f($\epsilon$)                                | Phelps DB                     |
| e + N2 -> e + N2_C3               | Excitation                 | f($\epsilon$)                                | Phelps DB                     |
| e + N2 -> e + N2_B3               | Excitation                 | f($\epsilon$)                                | Phelps DB                     |
| e + O2+ -> O + O                  | e- impact dissociation     | 2.0e-13*(300/Te)^1.0                         | Pancheshnyi PRE 2005          |
| O2 + O2- -> e + O2 + O2           | Electron detachment        | 1.24e-17*exp(-(179/(8.8+E/N))^2), E/N in Td  | Panchesnyi 2013               |
| N2 + O2- -> e + O2 + N2           | Electron detachment        | 1.24e-17*exp(-(179/(8.8+E/N))^2), E/N in Td  | Panchesnyi 2013               |
| N2 + O-  -> e + N2O               | Electron detachment        | 1.16e-18*exp(-(48.9/(1.1+E/N))^2), E/N in Td | Panchesnyi 2013               |
| O2 + O- -> O2- + O                | Negative ion conv.         | 6.96e-17*exp(-(198/(5.6+E/N))^2), E/N in Td  | Panchesnyi 2013               |
| O2 + O- + O2 -> O3- + O2          | Negative ion conv.         | 1.1e-42*exp(-(E/N/65)^2), E/N in Td          | Panchesnyi 2013               |
| N2 + O- + O2 -> O3- + N2          | Negative ion conv.         | 1.1e-42*exp(-(E/N/65)^2), E/N in Td          | Panchesnyi 2013               |
| N2+ + N2 + O2 -> N4+ + O2         | Positive ion conv.         | 5e-41*(300/T)^3                              | Aleksandrov and Bazelyan 1999 |
| N2+ + N2 + N2 -> N4+ + N2         | Positive ion conv.         | 5e-41*(300/T)^3                              | Aleksandrov and Bazelyan 1999 |
| N4+ + O2 -> N2 + N2 + O2+         | Positive ion conv.         | 2.5e-16*(300/T)^3                            | Aleksandrov and Bazelyan 1999 |
| O2+ + O2 + O2 -> O4+ + O2         | Positive ion conv.         | 2.4e-42*(300/T)^3                            | Aleksandrov and Bazelyan 1999 |
| O2+ + O2 + N2 -> O4+ + N2         | Positive ion conv.         | 2.4e-42*(300/T)^3                            | Aleksandrov and Bazelyan 1999 |
| O2+ + N2 + N2 -> N2O2+ + N2       | Positive ion conv.         | 9.0e-43                                      | Pancheshnyi PRE 2005          |
| N2O2+ + N2 -> O2+ + N2 + N2       | Positive ion conv.         | 4.3e-16                                      | Pancheshnyi PRE 2005          |
| N2O2+ + O2 -> O4+ + N2            | Positive ion conv.         | 1e-15                                        | Pancheshnyi PRE 2005          |
| e + O4+ -> O2 + O2                | e- recombination           | 1.4e-12*(300/Te)^0.5                         | Kossyi 1992                   |
| N2+ + O- -> N + N + O             | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N2+ + O3- -> N + N + O3           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N2+ + O2- -> N + N + O2           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O2+ + O- -> O + O + O             | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O2+ + O3- -> O + O + O3           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O2+ + O2- -> O + O + O2           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O4+ + O- -> O2 + O2 + O           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O4+ + O2- -> O2 + O2 + O2         | Recombination              | 1e-13                                        | Kossyi 1992                   |
| O4+ + O3- -> O2 + O2 + O3         | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N4+ + O- -> N2 + N2 + O           | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N4+ + O2- -> N2 + N2 + O2         | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N4+ + O3- -> N2 + N2 + O3         | Recombination              | 1e-13                                        | Kossyi 1992                   |
| N2_C3 + N2 -> N2                  | Excitation/Quenching       | 0.13e-16                                     | Pancheshnyi PRE 2005          |
| N2_C3 + O2 -> N2 + O + O          | Excitation/Quenching       | 3e-16                                        | Pancheshnyi PRE 2005          |
| N2_C3 -> N2_B3                    | Excitation/Quenching       | 2.381e7                                      | Pancheshnyi PRE 2005          |
| N2_B3 + O2 -> N2 + O + O          | Excitation/Quenching       | 3e-16                                        | Kossyi 1992                   |
| N2_B3 + N2 -> N2                  | Excitation/Quenching       | 5e-17                                        | Pancheshnyi PRE 2005          |
| N2_B3 -> N2                       | Excitation/Quenching       | 1.5e5                                        | Pancheshnyi PRE 2005          |
| O + O2 + O2 -> O3 + O2            | Neutral reaction (O3 Gen.) | 6.2e-46*(300/Tg)^1.2                         | Kossyi 1992                   |
| O + O2 + N2 -> O3 + N2            | Neutral reaction (O3 Gen.) | 6.2e-46*(300/Tg)^1.2                         | Kossyi 1992                   |
| N_2D + O2 -> NO + O_1D            | Neutral reaction (NO Gen.) | 6.0e-18*(300/Tg)^0.5                         | Kossyi 1992                   |
| N_2D + O2 -> NO + O               | Neutral reaction (NO Gen.) | 1.5e-18*(300/Tg)^0.5                         | Kossyi 1992                   |
| O2- + O -> O3 + e                 | Detachment                 | 1.5e-16                                      | Capitelli Book                |
| O2- + N -> NO2 + e                | Detachment                 | 5e-16                                        | Capitelli Book                |
| e + H2O -> e + e + H2O2+          | Ionization                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> e + e + OH+            | Ionization                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> e + e + O+             | Ionization                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> e + e + H2+ + O        | Ionization                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> e + e + H+ + OH        | Ionization                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> H + OH-                | Attachment                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> H2 + O-                | Attachment                 | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O -> OH + H-                | Attachment                 | f($\epsilon$)                                | Itikawa DB                    |
| Approx 22 water cluster reactions | Water Clustering           | Constant or Tg dependent                     | Galimberti 1979               |
| e + H9O4+ -> H + 4H2O             | e- recombination           | 6.5e-12*(300/Te)^0.5                         | Kossyi 1992                   |
| e + O2 -> O_D + O + e             | e- impact dissociation     | f($\epsilon$)                                | Phelps DB                     |
| O- + O2_a -> O2 + e               | Excitation/Quenching       | 3e-16                                        | Ref 28 from Norberg           |
| e + H2O -> H + OH + e             | Dissociation               | f($\epsilon$)                                | Itikawa DB                    |
| e + H2O+ -> H + OH                | e- impact dissociation     | 3.81e-13*(300/Te)^-0.5                       | REf 35 from Norberg           |
| O2- + H2O+ -> O2 + OH + H         |                            | 1e-13                                        |                               |
| Many other reactions to be added  |                            |                                              |                               |

