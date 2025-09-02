project('Servo', 'c', 'cpp',
  default_options : [
    'buildtype=minsize',
    'b_lto=true',
    'cpp_rtti=false',
    'cpp_eh_=none',
    'c_std=gnu11',
    'cpp_std=gnu++11',
    'b_staticpic=false',
  ],
)

assert(meson.is_cross_build(), 'Arduino projects can only be built in a cross build environment.')

compile_args = [
  '-DARDUINO_ARCH_AVR',
]

add_project_arguments(compile_args, language: 'cpp') # Servo define

servo_inc_dir = [
  'src',
]

servo_lib = static_library(meson.project_name(),
  include_directories: servo_inc_dir,
  sources: [ 
    'src/avr/Servo.cpp',
  ],
  dependencies : [
    subproject('arduinocore-avr').get_variable('arduinocore_dep'),
    subproject('arduinocore-avr').get_variable('arduinocore_main_dep'),
  ],
)

servo_dep = declare_dependency(
  compile_args: compile_args, 
  link_with: servo_lib,
  include_directories: servo_inc_dir,
)
