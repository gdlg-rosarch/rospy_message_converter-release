# Script generated with Bloom
pkgdesc="ROS - Converts between Python dictionaries and JSON to rospy messages."
url='http://ros.org/wiki/rospy_message_converter'

pkgname='ros-kinetic-rospy-message-converter'
pkgver='0.4.0_2'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('ros-kinetic-catkin'
'ros-kinetic-message-generation'
'ros-kinetic-rostest'
'ros-kinetic-std-msgs'
)

depends=('ros-kinetic-message-runtime'
'ros-kinetic-roslib'
'ros-kinetic-rospy'
'ros-kinetic-std-msgs'
)

conflicts=()
replaces=()

_dir=rospy_message_converter
source=()
md5sums=()

prepare() {
    cp -R $startdir/rospy_message_converter $srcdir/rospy_message_converter
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

