

include $(TOPDIR)/rules.mk

PKG_VERSION:=1.0.3-20240822
PKG_RELEASE:=5

LUCI_TITLE:=LuCI support for ChineseSubFinder
LUCI_PKGARCH:=all
LUCI_DEPENDS:=+lsblk +docker +dockerd +luci-lib-taskd

define Package/luci-app-chinesesubfinder/conffiles
/etc/config/chinesesubfinder
endef

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
