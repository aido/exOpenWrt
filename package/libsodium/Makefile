#
# Copyright (C) 2011-2013 Entware
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libsodium
PKG_VERSION:=0.4.2
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://download.libsodium.org/libsodium/releases/
PKG_MD5SUM:=9d25f083c957c690c01e0bf4a89cea25

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libsodium
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=library for network communication, encryption, decryption, etc
	URL:=https://github.com/jedisct1/libsodium
	MAINTAINER:=Black Roland https://forum.openwrt.org/profile.php?id=82621
endef

define Package/libsodium/description
	A high-speed software library for network communication, encryption,
	decryption, signatures, etc.
endef

TARGET_CFLAGS += \
	-std=gnu99 \

CONFIGURE_ARGS += \
	--disable-ssp \
	--disable-asm \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/sodium
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/sodium/*.h $(1)/usr/include/sodium
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsodium.{a,la,so*} $(1)/usr/lib/
endef

define Package/libsodium/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libsodium.so* $(1)/usr/lib
endef

$(eval $(call BuildPackage,libsodium))
