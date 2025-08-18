include $(TOPDIR)/rules.mk

PKG_NAME:=googletest
PKG_VERSION:=1.17.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/google/googletest/archive/refs/tags/
PKG_SOURCE_URL_FILE:=v$(PKG_VERSION).tar.gz
PKG_HASH:=65fab701d9829d38cb77c14acdc431d2108bfdbf8979e40eb8ae567edf10b27c

PKG_BUILD_PARALLEL:=1
CMAKE_INSTALL:=1
PKG_CPE_ID:=cpe:/a:google:google_test

PKG_MAINTAINER:=Jungo Lin <jungolin.tw@gmail.com>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(INCLUDE_DIR)/host-build.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/googletest
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=GoogleTest (gtest)
  URL:=https://github.com/google/googletest
endef

define Package/googletest/description
  GoogleTest (gtest) is a C++ testing framework.
endef

# Option for static/shared
define Package/googletest/config
  config GTEST_STATIC
    bool "Build static library"
    default y
endef

# CMake options
CMAKE_OPTIONS += -DBUILD_GMOCK=ON
CMAKE_OPTIONS += -DBUILD_GTEST=ON
CMAKE_OPTIONS += -DINSTALL_GTEST=ON
CMAKE_OPTIONS += -DBUILD_SHARED_LIBS=$(if $(CONFIG_GTEST_STATIC),OFF,ON)

$(eval $(call BuildPackage,googletest))
$(eval $(call HostBuild))

