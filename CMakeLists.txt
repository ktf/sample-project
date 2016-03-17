cmake_minimum_required(VERSION 3.5)

set(MODULES foo bar)
set(CoreBucket_LINK_DEPENDENCIES boost)
set(SimulationBucket_LINK_DEPENDENCIES geant4)

foreach(MODULE ${MODULES})
  add_subdirectory(${MODULE})
  get_property(MODULE_SOURCES
               DIRECTORY ${MODULE} 
               PROPERTY SOURCES)
  get_property(MODULE_BUCKET
               DIRECTORY ${MODULE} 
               PROPERTY BUCKET)
  message("Sources for ${MODULE} : ${MODULE_SOURCES}")
  message("Dependencies for ${MODULE} : ${${MODULE_BUCKET}_LINK_DEPENDENCIES}")
endforeach()
