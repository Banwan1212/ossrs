# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=srs
PKG_VERSION:=5.0
PKG_RELEASE:=1

PKG_SOURCE:=srs-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/ossrs/srs/tar.gz/v$(PKG_VERSION)
PKG_HASH:=skip

PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk

define Package/srs
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=SRS - Simple Realtime Server
  URL:=https://ossrs.net/
endef

define Package/srs/description
  SRS is a simple, high efficiency and real-time video server.
endef

define Build/Prepare
  mkdir -p $(PKG_BUILD_DIR)
  $(call Download,PKG)
  $(TAR) -xzvf $(DL_DIR)/$(PKG_SOURCE) -C $(PKG_BUILD_DIR) --strip-components 1
endef

define Build/Configure
  $(PKG_BUILD_DIR)/configure
endef

define Build/Compile
  $(MAKE) -C $(PKG_BUILD_DIR)
endef

define Package/srs/install
  $(INSTALL_DIR) $(1)/usr/bin
  $(INSTALL_BIN) $(PKG_BUILD_DIR)/objs/srs $(1)/usr/bin/
endef

$(eval $(call BuildPackage,srs))
