include $(TOPDIR)/rules.mk

PKG_NAME:=luci-app-banmac-nft
PKG_VERSION:=20231012
PKG_RELEASE:=2


include $(INCLUDE_DIR)/package.mk

define Package/luci-app-banmac-nft
 	SECTION:=luci
	CATEGORY:=LuCI
	SUBMENU:=3. Applications
	TITLE:=LuCI Support for Ban Client
	PKGARCH:=all
endef

define Build/Compile
endef

define Package/luci-app-banmac-nft/install
	$(INSTALL_DIR) $(1)/usr/lib/lua/luci
	cp -pR ./luasrc/* $(1)/usr/lib/lua/luci
	$(INSTALL_DIR) $(1)/usr/banmac
	$(INSTALL_BIN) ./files/banmac/* $(1)/usr/banmac
	$(INSTALL_DIR) $(1)/etc
	$(INSTALL_CONF) ./files/banmaclog $(1)/etc/banmaclog
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/banmac.conf $(1)/etc/config/banmac
endef

$(eval $(call BuildPackage,luci-app-banmac-nft))
