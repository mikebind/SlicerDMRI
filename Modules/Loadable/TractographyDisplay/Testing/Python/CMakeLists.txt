include(SlicerMacroBuildScriptedModule)


# Test fiducials in the neurosurgical planning tutorial
slicerMacroBuildScriptedModule(
  NAME NsgPlanTracto.py
  SCRIPTS NsgPlanTracto.py
  RESOURCES ""
  )

# work around runner bug https://issues.slicer.org/view.php?id=4242
set(DMRI_UNITTEST_LIB_PATHS "--additional-module-paths;${CMAKE_BINARY_DIR}/${Slicer_QTSCRIPTEDMODULES_LIB_DIR}/Release;${CMAKE_BINARY_DIR}/${Slicer_QTLOADABLEMODULES_LIB_DIR}/Release;${CMAKE_BINARY_DIR}/${Slicer_CLIMODULES_LIB_DIR}/Release")

slicer_add_python_unittest(SCRIPT NsgPlanTracto.py
	SLICER_ARGS ${DMRI_UNITTEST_LIB_PATHS})
slicer_add_python_unittest(SCRIPT DTINotReproducibleIssue3977.py
	SLICER_ARGS ${DMRI_UNITTEST_LIB_PATHS})
slicer_add_python_unittest(SCRIPT fiber_visibility_crash2438.py
	SLICER_ARGS ${DMRI_UNITTEST_LIB_PATHS})
slicer_add_python_unittest(SCRIPT test_tractography_display.py
	SLICER_ARGS ${DMRI_UNITTEST_LIB_PATHS})
slicer_add_python_unittest(SCRIPT SlicerMRBTest.py
	SLICER_ARGS ${DMRI_UNITTEST_LIB_PATHS})
