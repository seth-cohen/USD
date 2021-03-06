set(PXR_PREFIX pxr/usdImaging)
set(PXR_PACKAGE usdviewq)

if (NOT PXR_BUILD_USDVIEW)
    return()
endif()

pxr_python_bin(testusdview
    DEPENDENCIES
        usdviewq
)

if (NOT PXR_HEADLESS_TEST_MODE)
    pxr_install_test_dir(
        SRC testenv/testUsdviewAlive
        DEST testusdviewAlive
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments1
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments2
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments3
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments4
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments5
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments6
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewFileArguments
        DEST testusdviewFileArguments7
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewWrapper
        DEST testusdviewWrapper1
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewWrapper
        DEST testusdviewWrapper2
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewWrapper
        DEST testusdviewWrapper3
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewWrapper
        DEST testusdviewWrapper4
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewWrapper
        DEST testusdviewWrapper5
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewPrimPathBar
        DEST testusdviewPrimPathBar
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewPrimSearch
        DEST testusdviewPrimSearch
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewPropertySearch
        DEST testusdviewPropertySearch
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewMetadatatabSelect
        DEST testusdviewMetadatatabSelect
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewTimeSamples
        DEST testusdviewTimeSamples
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewNavigationKeys
        DEST testusdviewNavigationKeys
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewReloadReopen
        DEST testusdviewReloadReopen
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewNoPlugins
        DEST testusdviewNoPlugins
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewInterpreterNoRender
        DEST testusdviewInterpreterNoRender
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewLoadPlugins
        DEST testusdviewLoadPlugins_alive
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewLoadPlugins
        DEST testusdviewLoadPlugins_multipleContainers
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewLoadPlugins
        DEST testusdviewLoadPlugins_missingContainer
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewLoadPlugins
        DEST testusdviewLoadPlugins_duplicateCommand
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewLoadPlugins
        DEST testusdviewLoadPlugins_chained
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewUpAxis
        DEST testusdviewUpAxis_zUp
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewUpAxis
        DEST testusdviewUpAxis_yUp
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewDeactivate
        DEST testusdviewDeactivate
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewSkinning
        DEST testusdviewSkinning
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewPrimTreeExpansion
        DEST testusdviewPrimTreeExpansion
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewInfGeom
        DEST testusdviewInfGeom
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewShaderEdits
        DEST testusdviewShaderEdits
    )

    pxr_install_test_dir(
        SRC testenv/testUsdviewPrimvarEdits
        DEST testusdviewPrimvarEdits
    )

    pxr_register_test(testusdviewAlive                                               
        PRE_COMMAND "${PYTHON_EXECUTABLE} testUsdviewAliveSetup.py"
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testAlive.py test.usda"   
        EXPECTED_RETURN_CODE 0                                                       
    )

    pxr_register_test(testusdviewFileArguments1
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testValidFileArg.py test.usda" 
        EXPECTED_RETURN_CODE 0                                                       
    )

    pxr_register_test(testusdviewFileArguments2
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testValidFileArg.py test.usd" 
        EXPECTED_RETURN_CODE 0                                                       
    )

    pxr_register_test(testusdviewFileArguments3
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testValidFileArg.py test.usdc" 
        EXPECTED_RETURN_CODE 0                                                       
    )

    pxr_register_test(testusdviewFileArguments4
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testInvalidFileArg.py test.py" 
        STDERR_REDIRECT py_test_out
        DIFF_COMPARE py_test_out 
        EXPECTED_RETURN_CODE 1                                                       
    )

    pxr_register_test(testusdviewFileArguments5
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testInvalidFileArg.py invalidSyntax.usda" 
        CLEAN_OUTPUT "(?:[A-Za-z]:)?/(?!refSphere2).*/"
        STDERR_REDIRECT invalidSyntax_test_out
        DIFF_COMPARE invalidSyntax_test_out 
        EXPECTED_RETURN_CODE 1 
    )

    pxr_register_test(testusdviewFileArguments6
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testInvalidFileArg.py test.txt" 
        STDERR_REDIRECT txt_test_out
        DIFF_COMPARE txt_test_out 
        EXPECTED_RETURN_CODE 1                                                       
    )

    pxr_register_test(testusdviewFileArguments7
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testInvalidFileArg.py missing" 
        STDERR_REDIRECT missing_test_out
        DIFF_COMPARE missing_test_out 
        EXPECTED_RETURN_CODE 1                                                       
    )

    pxr_register_test(testusdviewWrapper1
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testCallback.py"
        EXPECTED_RETURN_CODE 2
    )

    pxr_register_test(testusdviewWrapper2
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testCallback_Invalid_1.py test.usda"
        EXPECTED_RETURN_CODE 1
    )

    pxr_register_test(testusdviewWrapper3
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testCallback_Invalid_2.py test.usda"
        EXPECTED_RETURN_CODE 1
    )

    pxr_register_test(testusdviewWrapper4
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testCallback_Invalid_3.py test.usda"
        EXPECTED_RETURN_CODE 1
    )

    pxr_register_test(testusdviewWrapper5
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview test.usda"
        EXPECTED_RETURN_CODE 2
    )

    pxr_register_test(testusdviewPrimPathBar
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewPrimPathBar.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewPrimSearch
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewPrimSearch.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewPropertySearch
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewPropertySearch.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewMetadatatabSelect
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewMetadatatabSelect.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewTimeSamples
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewTimeSamples.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewNavigationKeys
        RUN_SERIAL
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewNavigationKeys.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewReloadReopen
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewReloadReopen.py test.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewNoPlugins
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewNoPlugins.py --noplugins test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewInterpreterNoRender
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewInterpreterNoRender.py --norender test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewLoadPlugins_alive
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewLoadPlugins_alive.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewLoadPlugins_multipleContainers
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewLoadPlugins_multipleContainers.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewLoadPlugins_missingContainer
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewLoadPlugins_missingContainer.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewLoadPlugins_duplicateCommand
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewLoadPlugins_duplicateCommand.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewLoadPlugins_chained
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewLoadPlugins_chained.py test.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewUpAxis_zUp
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewUpAxis_zUp.py testZUp.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewUpAxis_yUp
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewUpAxis_yUp.py testYUp.usda"
        EXPECTED_RETURN_CODE 0
    )

    pxr_register_test(testusdviewDeactivate
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewDeactivate.py test.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewSkinning
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewSkinning.py arm.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewPrimTreeExpansion
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewPrimTreeExpansion.py test.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewInfGeom
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewInfGeom.py infGeom.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewShaderEdits
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewShaderEdits.py test.usda"
        EXPECTED_RETURN_CODE 0
    )
    
    pxr_register_test(testusdviewPrimvarEdits
        PYTHON
        COMMAND "${CMAKE_INSTALL_PREFIX}/bin/testusdview --testScript testUsdviewPrimvarEdits.py primvars.usda"
        EXPECTED_RETURN_CODE 0
    )

endif()
