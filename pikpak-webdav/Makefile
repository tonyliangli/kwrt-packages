include $(TOPDIR)/rules.mk

PKG_NAME:=pikpak-webdav
PKG_VERSION:=0.0.3
PKG_RELEASE:=5

PKG_LICENSE:=MIT
PKG_MAINTAINER:=ykxVK8yL5L

PKG_LIBC:=musl
ifeq ($(ARCH),arm)
  PKG_LIBC:=musleabi

  ARM_CPU_FEATURES:=$(word 2,$(subst +,$(space),$(call qstrip,$(CONFIG_CPU_TYPE))))
  ifneq ($(filter $(ARM_CPU_FEATURES),vfp vfpv2),)
    PKG_LIBC:=musleabihf
  endif
endif

PKG_ARCH=$(ARCH)
ifeq ($(ARCH),i386)
  PKG_ARCH:=i686
endif

PKG_SOURCE:=pikpak-webdav-v$(PKG_VERSION).$(PKG_ARCH)-unknown-linux-$(PKG_LIBC).tar.gz
PKG_SOURCE_URL:=https://github.com/ykxVK8yL5L/pikpak-webdav/releases/download/v$(PKG_VERSION)/
PKG_HASH:=skip

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
	SECTION:=multimedia
	CATEGORY:=Multimedia
	TITLE:=WebDAV server for Pikpak
	URL:=https://github.com/ykxVK8yL5L/pikpak-webdav
endef

define Package/$(PKG_NAME)/description
WebDAV server for Pikpak.
endef

define Package/$(PKG_NAME)/conffiles
/etc/config/pikpak-webdav
endef

define Download/sha256sum
	FILE:=$(PKG_SOURCE).sha256
	URL_FILE:=$(FILE)
	URL:=$(PKG_SOURCE_URL)
	HASH:=skip
endef
$(eval $(call Download,sha256sum))

define Build/Prepare
	mv $(DL_DIR)/$(PKG_SOURCE).sha256 .
	cp $(DL_DIR)/$(PKG_SOURCE) .
	shasum -a 256 -c $(PKG_SOURCE).sha256
	rm $(PKG_SOURCE).sha256 $(PKG_SOURCE)

	tar -C $(PKG_BUILD_DIR)/ -zxf $(DL_DIR)/$(PKG_SOURCE)
endef

define Build/Compile
	echo "$(PKG_NAME) using precompiled binary."
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/pikpak-webdav $(1)/usr/bin/pikpak-webdav
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/pikpak-webdav.init $(1)/etc/init.d/pikpak-webdav
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/pikpak-webdav.config $(1)/etc/config/pikpak-webdav
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
