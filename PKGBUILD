# Script generated with Bloom
pkgdesc="ROS - The public interface and retaskable interface for a robot."
url='http://www.ros.org/wiki/rocon_app_manager'

pkgname='ros-kinetic-rocon-app-manager'
pkgver='0.9.1_1'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('python2-catkin_pkg'
'ros-kinetic-catkin'
'ros-kinetic-roslint'
'ros-kinetic-rostest'
)

depends=('ros-kinetic-capabilities'
'ros-kinetic-gateway-msgs'
'ros-kinetic-rocon-app-manager-msgs'
'ros-kinetic-rocon-app-utilities'
'ros-kinetic-rocon-apps'
'ros-kinetic-rocon-console'
'ros-kinetic-rocon-gateway'
'ros-kinetic-rocon-gateway-utils'
'ros-kinetic-rocon-hub'
'ros-kinetic-rocon-interactions'
'ros-kinetic-rocon-master-info'
'ros-kinetic-rocon-python-comms'
'ros-kinetic-rocon-python-utils'
'ros-kinetic-rocon-std-msgs'
'ros-kinetic-rocon-uri'
'ros-kinetic-roslib'
'ros-kinetic-rosmaster'
'ros-kinetic-rospy'
'ros-kinetic-std-msgs'
)

conflicts=()
replaces=()

_dir=rocon_app_manager
source=()
md5sums=()

prepare() {
    cp -R $startdir/rocon_app_manager $srcdir/rocon_app_manager
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

