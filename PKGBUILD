# Script generated with Bloom
pkgdesc="ROS - Core rocon apps for use with the appmanager and rocon concert."
url='http://wiki.ros.org/rocon_apps'

pkgname='ros-kinetic-rocon-apps'
pkgver='0.9.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
)

depends=('ros-kinetic-gateway-msgs'
'ros-kinetic-rocon-app-manager-msgs'
'ros-kinetic-roslib'
'ros-kinetic-rospy'
'ros-kinetic-rospy-tutorials'
'ros-kinetic-topic-tools'
)

conflicts=()
replaces=()

_dir=rocon_apps
source=()
md5sums=()

prepare() {
    cp -R $startdir/rocon_apps $srcdir/rocon_apps
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

