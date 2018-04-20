# Script generated with Bloom
pkgdesc="ROS - The rocon_app_utilities package"
url='http://wiki.ros.org/rocon_app_utilities'

pkgname='ros-kinetic-rocon-app-utilities'
pkgver='0.9.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python2-catkin_pkg'
'ros-kinetic-catkin'
'ros-kinetic-roslint'
)

depends=('python2-rospkg'
'ros-kinetic-rocon-console'
'ros-kinetic-rocon-python-utils'
'ros-kinetic-rocon-uri'
'ros-kinetic-roslaunch'
)

conflicts=()
replaces=()

_dir=rocon_app_utilities
source=()
md5sums=()

prepare() {
    cp -R $startdir/rocon_app_utilities $srcdir/rocon_app_utilities
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/kinetic/setup.bash ] && source /opt/ros/kinetic/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/kinetic \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

