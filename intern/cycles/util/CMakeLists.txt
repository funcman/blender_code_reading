
set(INC
	.
	../../glew-mx
)

set(INC_SYS
	${GLEW_INCLUDE_DIR}
)

set(SRC
	util_aligned_malloc.cpp
	util_cache.cpp
	util_logging.cpp
	util_md5.cpp
	util_path.cpp
	util_string.cpp
	util_simd.cpp
	util_system.cpp
	util_task.cpp
	util_time.cpp
	util_transform.cpp
)

if(NOT CYCLES_STANDALONE_REPOSITORY)
	add_definitions(-DWITH_GLEW_MX)
endif()

if(WITH_CYCLES_STANDALONE AND WITH_CYCLES_STANDALONE_GUI)
	list(APPEND SRC
		util_view.cpp
	)
endif()

set(SRC_HEADERS
	util_algorithm.h
	util_aligned_malloc.h
	util_args.h
	util_atomic.h
	util_boundbox.h
	util_cache.h
	util_debug.h
	util_foreach.h
	util_function.h
	util_half.h
	util_hash.h
	util_image.h
	util_list.h
	util_logging.h
	util_map.h
	util_math.h
	util_math_fast.h
	util_md5.h
	util_opengl.h
	util_optimization.h
	util_param.h
	util_path.h
	util_progress.h
	util_set.h
	util_simd.h
	util_sseb.h
	util_ssef.h
	util_ssei.h
	util_stats.h
	util_string.h
	util_system.h
	util_task.h
	util_thread.h
	util_time.h
	util_transform.h
	util_types.h
	util_vector.h
	util_view.h
	util_xml.h
)

if(WITH_CYCLES_DEBUG)
	list(APPEND SRC
		util_guarded_allocator.cpp
	)
	list(APPEND SRC_HEADERS
		util_guarded_allocator.h
	)
endif()

include_directories(${INC})
include_directories(SYSTEM ${INC_SYS})

add_definitions(${GL_DEFINITIONS})

add_library(cycles_util ${SRC} ${SRC_HEADERS})
