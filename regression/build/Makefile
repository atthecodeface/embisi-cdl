CDL_ROOT ?= set_cdl_root
include ${CDL_ROOT}/lib/cdl/cdl_templates.mk
BUILD_ROOT ?= /home/gavin/Git/cdl/regression/build
SRC_ROOT ?= /home/gavin/Git/cdl/regression
SIM   ?= ${BUILD_ROOT}/sim
PYSIM ?= ${BUILD_ROOT}/py_engine.so
all: sim
SUBMAKE=${MAKE} CDL_ROOT=${CDL_ROOT}

$(eval $(call toplevel_init_template))

$(eval $(call cdl_makefile_template,${SRC_ROOT},${BUILD_ROOT}/cdl_regression,))
-include ${BUILD_ROOT}/cdl_regression/Makefile
$(eval $(call sim_add_cdl_library,${BUILD_ROOT}/cdl_regression,cdl_regression))
${BUILD_ROOT}/cdl_regression/Makefile: ${SRC_ROOT}/library_desc.py

$(eval $(call sim_init_object_file_template,${BUILD_ROOT},obj_init,cdl_regression))
$(eval $(call command_line_sim_template,${SIM},${BUILD_ROOT},${BUILD_ROOT}/obj_init.o))
$(eval $(call python_library_template,${PYSIM},${BUILD_ROOT},${BUILD_ROOT}/obj_init.o))

$(eval $(call toplevel_clean_template))
