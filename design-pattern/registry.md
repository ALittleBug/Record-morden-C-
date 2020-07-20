* registry pattern
  * refer [static registration link](https://dxuuu.xyz/cpp-static-registration.html)
* Dynamically register Plugin macro [link](https://tegra-sw-opengrok.nvidia.com/source/xref/rel-32_l4t/deepstream/sdk/src/utils/nvdsinfer/trt_include/NvInferRuntimeCommon.h#1347)
* Explicit depend on nvinfer_plugin0[link]( https://tegra-sw-opengrok.nvidia.com/source/xref/rel-32_l4t/deepstream/sdk/Rules.mk#144)
	1. Static Variable only initialized once even it's just a local variable in a member function [used in TRT inferPlugin](https://github.com/NVIDIA/TensorRT/blob/release/7.1/plugin/InferPlugin.cpp#L69)  [stack overflow reference](https://stackoverflow.com/questions/6223355/static-variables-in-member-functions)
	2. unique_ptr for polymorphism (for
	mRegistry.push(std::move(pluginCreator)); [link](https://github.com/NVIDIA/TensorRT/blob/release/7.0/plugin/InferPlugin.cpp#L92)

 [if-i-need-polymorphism-should-i-use-raw-pointers-instead-of-unique-ptr](https://stackoverflow.com/questions/22106912/if-i-need-polymorphism-should-i-use-raw-pointers-instead-of-unique-ptr) and  [used in TRT](https://github.com/NVIDIA/TensorRT/blob/release/7.0/plugin/InferPlugin.cpp#L92)
