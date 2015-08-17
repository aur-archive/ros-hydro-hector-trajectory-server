# Script generated with import_catkin_packages.py
# For more information: https://github.com/bchretien/arch-ros-stacks
pkgdesc="ROS - hector_trajectory_server keeps track of tf trajectories extracted from tf data and makes this data accessible via a service and topic."
url='http://ros.org/wiki/hector_trajectory_server'

pkgname='ros-hydro-hector-trajectory-server'
pkgver='0.3.2'
_pkgver_patch=0
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(ros-hydro-roscpp
  ros-hydro-catkin
  ros-hydro-nav-msgs
  ros-hydro-tf
  ros-hydro-hector-map-tools
  ros-hydro-hector-nav-msgs)
makedepends=('cmake' 'git' 'ros-build-tools'
  ${ros_makedepends[@]})

ros_depends=(ros-hydro-tf
  ros-hydro-roscpp
  ros-hydro-hector-map-tools
  ros-hydro-hector-nav-msgs
  ros-hydro-nav-msgs)
depends=(${ros_depends[@]})

_tag=release/hydro/hector_trajectory_server/${pkgver}-${_pkgver_patch}
_dir=hector_trajectory_server
source=("${_dir}"::"git+https://github.com/tu-darmstadt-ros-pkg-gbp/hector_slam-release.git"#tag=${_tag})
md5sums=('SKIP')

build() {
  # Use ROS environment variables
  /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/hydro/setup.bash ] && source /opt/ros/hydro/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/hydro \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}
