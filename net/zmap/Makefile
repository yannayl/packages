#
# Copyright (C) 2006-2017 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=zmap
PKG_VERSION:=2.1.1
PKG_RELEASE:=1
PKG_MAINTAINER:=Yannay Livneh <yannayl@gmail.com>

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/zmap/$(PKG_NAME)/tar.gz/v$(PKG_VERSION)?
PKG_HASH:=29627520c81101de01b0213434adb218a9f1210bfd3f2dcfdfc1f975dbce6399
PKG_LICENSE:=APACHE-2.0
PKG_LICENSE_FILES:=COPYING
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

# gengetopt flex byacc
ZMAP_DEPENDS:=+libgmp +libpcap +libunistring +libjson-c 

define Package/zmap/default
  SUBMENU:=ZMAP Internet Scanner
  SECTION:=net
  CATEGORY:=Network
  URL:=http://zmap.io/
endef

define Package/zmap
  $(call Package/zmap/default)
  DEPENDS:=$(ZMAP_DEPENDS)
  TITLE:=Fast Internet Scanner
endef

define Package/zmap/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/zmap $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/ztee $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/zblacklist $(1)/usr/sbin
endef

$(eval $(call BuildPackage,zmap))
