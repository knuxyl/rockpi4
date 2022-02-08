# rockpi4
Scripts for setting up Rock Pi 4




These scripts might only apply to Manjaro, especially the build prefix for mesa




Compiler options (take off -flto to disable link-time optimizations. this breaks a lot of builds)


export CFLAGS='-march=armv8-a -mcpu=cortex-a72.cortex-a53 -O3 -funsafe-math-optimizations -flto

export CXXFLAGS='-march=armv8-a -mcpu=cortex-a72.cortex-a53 -O3 -funsafe-math-optimizations -flto




Building Mesa


git clone --recursive https://gitlab.freedesktop.org/mesa/mesa

cd mesa

mkdir build

meson --prefix==/usr/ -Dplatforms=x11,wayland -Dgallium-drivers=panfrost -Dvulkan-drivers=panfrost -Dllvm=false

ninja -C build/

sudo ninja -C build/ install
