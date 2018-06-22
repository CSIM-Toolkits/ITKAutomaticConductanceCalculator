itk_module_test()

set(AutomaticConductanceCalculatorTests
  itkMinimalStandardRandomVariateGeneratorTest.cxx
  itkNormalDistributionImageSourceTest.cxx
  itkAutomaticConductanceImageCalculatorTest.cxx
  )

CreateTestDriver(AutomaticConductanceCalculator "${AutomaticConductanceCalculator-Test_LIBRARIES}" "${AutomaticConductanceCalculatorTests}")

itk_add_test(NAME itkMinimalStandardRandomVariateGeneratorTest
  COMMAND AutomaticConductanceCalculatorTestDriver itkMinimalStandardRandomVariateGeneratorTest
  )

itk_add_test(NAME itkAutomaticConductanceImageCalculatorTest
  COMMAND AutomaticConductanceCalculatorTestDriver
    --compare
    ${ITK_TEST_OUTPUT_DIR}/itkAutomaticConductanceImageCalculatorTestOutput.mha
    DATA{Baseline/itkAutomaticConductanceImageCalculatorTestOutput.mha}
  itkAutomaticConductanceImageCalculatorTest
    ${ITK_TEST_OUTPUT_DIR}/itkAutomaticConductanceImageCalculatorTestOutput.mha
  )

itk_add_test(NAME itkNormalDistributionImageSourceTest
  COMMAND AutomaticConductanceCalculatorTestDriver --without-threads
  --compare
    ${ITK_TEST_OUTPUT_DIR}/itkNormalDistributionImageSourceTestOutput.mha
    DATA{Baseline/itkNormalDistributionImageSourceTestOutput.mha}
  itkNormalDistributionImageSourceTest
    ${ITK_TEST_OUTPUT_DIR}/itkNormalDistributionImageSourceTestOutput.mha
  )
