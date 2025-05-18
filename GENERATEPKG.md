rm -rf ~/.nuget/packages/godot.net.sdk
rm -rf .mono/ .godot/ bin/ obj/

export GODOT_VERSION_STATUS=custom
export BUILD_NAME=mybuild123

scons platform=macos arch=arm64 generate_bundle=yes module_mono_enabled=yes
scons target=template_debug module_mono_enabled=yes generate_bundle=yes

godot --headless --generate-mono-glue modules/mono/glue

./modules/mono/build_scripts/build_assemblies.py --godot-output-dir=./bin --push-nupkgs-local ~/MyLocalNugetSource
