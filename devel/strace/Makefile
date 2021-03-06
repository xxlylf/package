#
# Copyright (C) 2006-2012 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
include $(BUILD_DIR)/kernel.mk

PKG_NAME:=strace

PKG_VERSION:=4.10
PKG_RELEASE:=1
PKG_MD5SUM:=107a5be455493861189e9b57a3a51912

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=@SF/$(PKG_NAME)

PKG_LICENSE:=BSD-3c
PKG_LICENSE_FILES:=COPYRIGHT

PKG_MAINTAINER:=Felix Fietkau <nbd@openwrt.org>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(BUILD_DIR)/package.mk

HOST_CFLAGS += -I$(LINUX_DIR)/user_headers/include

CONFIGURE_VARS+= \
	LDFLAGS_FOR_BUILD="$(HOST_LDFLAGS)" \
	CPPFLAGS_FOR_BUILD="$(HOST_CPPFLAGS)" \
	CFLAGS_FOR_BUILD="$(HOST_CFLAGS)" \
	CC_FOR_BUILD="$(HOST_CC)"

define Package/strace
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=System call tracer
  URL:=http://strace.sourceforge.net/
endef

define Package/strace/description
A useful diagnostic, instructional, and debugging tool. Allows you to track what
system calls a program makes while it is running.
endef

MAKE_FLAGS := \
	CCOPT="$(TARGET_CFLAGS)"

define Package/strace/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/strace $(1)/usr/bin/
endef

$(eval $(call BuildPackage,strace))
