export GODOT_VERSION_STATUS=custom
export BUILD_NAME=mybuild123

scons target=template_debug module_mono_enabled=yes

godot --headless --generate-mono-glue modules/mono/glue

./modules/mono/build_scripts/build_assemblies.py --godot-output-dir=./bin --push-nupkgs-local ~/MyLocalNugetSource
