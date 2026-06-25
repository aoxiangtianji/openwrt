include $(TOPDIR)/rules.mk

PKG_NAME:=mieru
PKG_VERSION:=3.34.0
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/enfein/mieru/archive/refs/tags/v$(PKG_VERSION)
PKG_HASH:=ee5824d8ab9dc6e5e4e7fe69e8a818a6938cae6e0e316bae6c0b0ca60122ec98

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Your Name <your.email@example.com>

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/enfein/mieru/v3
GO_PKG_BUILD_PKG:=github.com/enfein/mieru/v3/cmd/mieru
GO_PKG_LDFLAGS:=-s -w

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/mieru
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=A flexible and lightweight proxy server/client
  URL:=https://github.com/enfein/mieru
  DEPENDS:=$(GO_ARCH_DEPENDS) +ca-bundle
endef

define Package/mieru/description
  Mieru is a flexible and lightweight proxy server and client.
  It helps you bypass network restrictions.
endef

define Package/mieru/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mieru $(1)/usr/bin/mieru

	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/mieru.config $(1)/etc/config/mieru

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/mieru.init $(1)/etc/init.d/mieru
endef

$(eval $(call GoBinPackage,mieru))
$(eval $(call BuildPackage,mieru))
