include $(TOPDIR)/rules.mk

PKG_NAME:=iozone3
PKG_VERSION:=506
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)_$(PKG_VERSION).tar
PKG_SOURCE_URL:=https://www.iozone.org/src/current/
PKG_HASH:=114ce5c071873b9a2c7ba6e73d05d5ef7e66564392acbfcdc0b3261db10fcbe7
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)_$(PKG_VERSION)

PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk

define Package/iozone
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=A filesystem benchmark tool
  URL:=http://iozone.org
endef

define Package/iozone/description
 IOzone is a filesystem benchmark tool that can measure
 a variety of file operations.
endef

define Build/Compile
	$(MAKE) -j1 -C $(PKG_BUILD_DIR)/src/current linux-arm \
		CC="$(TARGET_CC)" \
		CFLAGS="$(TARGET_CFLAGS) $(TARGET_CPPFLAGS) $(FPIC)"
endef

define Package/iozone/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/current/iozone $(1)/usr/bin/
endef

$(eval $(call BuildPackage,iozone))
