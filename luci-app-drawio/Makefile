

include $(TOPDIR)/rules.mk

PKG_VERSION:=1.0.0-20240822
PKG_RELEASE:=5

LUCI_TITLE:=LuCI support for DrawIO
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+lsblk +docker +dockerd +luci-lib-taskd +luci-lib-docker +docker-compose

define Package/luci-app-drawio/conffiles
/etc/config/drawio
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
