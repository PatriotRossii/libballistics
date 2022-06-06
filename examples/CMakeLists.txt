project(examples)

set(example_dirs
	basic
)

set(example_sources)
foreach (example_dir ${example_dirs})
    file(GLOB sources ${example_dir}/*.c)
    list(APPEND example_sources ${sources})
endforeach ()

foreach (example_source ${example_sources})
    # Create the basename for the example
    get_filename_component(example_name ${example_source} NAME)
    string(REPLACE ".c" "" example_name ${example_name})

	add_executable(${example_name} ${example_source})
	target_link_libraries(${example_name} ballistics)
endforeach ()