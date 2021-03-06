# Changes in mirtCAT 0.5

BUGFIX

- fix stem location bug, and add better aspect ratio

- the `summary(mod, sort=FALSE)` argument returned a NULL object instead of the unsorted response.
  This has been patched and is now tested for

# Changes in mirtCAT 0.4.2

- `forced_choice` argument for shinyGUI input to state whether respones for each item are 
  required (for CATs, this should always be TRUE)

- respones in GUI now are blank by default

- in `preCAT` list input change `nitems` to `min_items` and `max_items` for better control. Also 
  include a `response_variance` logical to terminate the preCAT stage when variability in the 
  the response options occurs (so that ML estimation becomes plausible)

- include Sympson-Hetter method of item exposure control

- major re-write of shiny inputs. Now the questions, answers, and options are all supplied through
  a `data.frame` object for better clarity, and all shiny inputs regarding the questions, image 
  locations, etc, are specified in this object
  
- `mirt_object` input renamed to `mo` for short

- the `local_pattern` input now accepts a matrix of response patterns for running simulation 
  designs. Returns a list of person objects instead of a single object
  
- `generate_pattern()` now supports multiple Theta inputs specifically for simulation designs

- `start_item` input now accepts character value inputs (in addition to explicit numeric inputs)
  corresponding to the `criteria` argument. This allows the first item to be selected using the 
  (adaptive) selection criteria

- added `generate.mirt_object()` function to build the required `mirt_object` input given
  population parameters
  
- new `cl` argument in `mirtCAT()` for passing a parallel cluster object defined from the 
  parallel package. Used to run simulation designs with parallel architecture for better speed
  
- by default, the demographics page is no longer generated in the GUI  

# Changes in mirtCAT 0.3

- `item_answers` can now be a list input, indicating that more than one correct answer is
  possible for a given item

- allow the first page and demographics page to be skipped by passing empty list arguments 

- added 'fixed' method to keep latent trait estimates at fixed values (useful for preCAT)

- Fisher information matrix added for remaining multidimensional models supported by `mirt`,
  including custom item types

- add 'Arule' and 'APrule' for minimum trace criteria of asymtotic covariance matrix

# Changes in mirtCAT 0.2

- temporary files can now be saved while the GUI is running, and restored at a later time

- more estimation options can be passed to `fscores()` via the ... argument

- sensitive objects are now removed from the package namespace when the `mirtCAT()` finishes 
  unsuccessfully 

- categories are always returned with based 1 for first response in the GUI

- add content balancing option

- various bug fixes, and update documentation

- new `findNextItem()` input for users to locate the next item to administer (likely for custom
  CAT interfaces that do not use the Shiny package). Can be updated with the `updateDesign()` 
  function
  
- moved 'Next' button in the web interface to the left panel box so that it will always remain in 
  the same location
  
- support CSS customization

- switch multidimensional selection criteria to use analytical expressions rather than numerical.
  Several multivariate Fisher information matrix computation currently not supported analytically,
  but will be steadily added.
  
- add classification capabilities to `design` list input