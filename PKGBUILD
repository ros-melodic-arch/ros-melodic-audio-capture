# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - Transports audio from a source to a destination."
url='https://wiki.ros.org/audio_capture'

pkgname='ros-melodic-audio-capture'
pkgver='0.3.8'
_pkgver_patch=0
arch=('i686' 'x86_64' 'aarch64' 'armv7h' 'armv6h')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-melodic-roscpp
  ros-melodic-audio-common-msgs
  ros-melodic-catkin)
makedepends=('cmake' 'ros-build-tools'
  ${ros_makedepends[@]}
  gstreamer
  gst-plugins-base)

ros_depends=(ros-melodic-roscpp
  ros-melodic-audio-common-msgs)
depends=(${ros_depends[@]}
  gst-plugins-good
  gstreamer
  gst-plugins-base
  gst-plugins-ugly)

_dir="audio_common-${pkgver}/audio_capture"
source=("${pkgname}-${pkgver}.tar.gz"::"https://github.com/ros-drivers/audio_common/archive/${pkgver}.tar.gz")
sha256sums=('f0c552e06e211998981c7204d479b7c5130503812fbba28324d1cb52b3454d21')

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
        -DPYTHON_EXECUTABLE=/usr/bin/python3 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
