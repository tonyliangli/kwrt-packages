# Copyright (C) 2018-2020 Lienol <lawlienol@gmail.com>
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

LUCI_TITLE:=LuCI support for V2ray Server
LUCI_DEPENDS:=+luci-compat +unzip
LUCI_PKGARCH:=all

PKG_NAME:=luci-app-v2ray-server
PKG_VERSION:=13
PKG_RELEASE:=10

include $(TOPDIR)/feeds/luci/luci.mk

# call BuildPackage - OpenWrt buildroot signature
