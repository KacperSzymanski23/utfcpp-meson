src_include = include_directories('../source')

cpp = meson.get_compiler('cpp')
if cpp.get_id() == 'msvc'
    warn_args = ['/W4']
    no_exceptions_arg = []
else
    warn_args = ['-Wall', '-Wextra', '-Wpedantic', '-Wconversion', '-Wsign-conversion']
    no_exceptions_arg = ['-fno-exceptions']
endif

common_args = warn_args

negative = executable(
    'negative',
    'negative.cpp',
    include_directories: src_include,
    cpp_args: [common_args, '-std=c++98'],
)

apitests = executable(
    'apitests',
    'apitests.cpp',
    include_directories: src_include,
    cpp_args: [common_args, '-std=c++98'],
)

noexceptionstests = executable(
    'noexceptionstests',
    'noexceptionstests.cpp',
    include_directories: src_include,
    cpp_args: [common_args + no_exceptions_arg, '-std=c++98'],
)

cpp11 = executable(
    'cpp11',
    'test_cpp11.cpp',
    include_directories: src_include,
    cpp_args: [common_args, '-std=c++11'],
)

cpp17 = executable(
    'cpp17',
    'test_cpp17.cpp',
    include_directories: src_include,
    cpp_args: [common_args, '-std=c++17'],
)

cpp20 = executable(
    'cpp20',
    'test_cpp20.cpp',
    include_directories: src_include,
    cpp_args: [common_args, '-std=c++20'],
)

test_data_file = join_paths(meson.project_source_root(), 'tests', 'test_data', 'utf8_invalid.txt')

test('negative_test', negative, args: [test_data_file])
test('cpp11_test', cpp11)
test('cpp17_test', cpp17)
test('cpp20_test', cpp20)
test('api_test', apitests)
test('noexceptions_test', noexceptionstests)