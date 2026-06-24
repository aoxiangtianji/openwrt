include $(TOPDIR)/rules.mk

PKG_NAME:=haut-auth
PKG_VERSION:=0.2.2
PKG_RELEASE:=1

# Clone the source repo (repo root is a Cargo project).
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/aoxiangtianji/haut-auth-service.git
PKG_SOURCE_VERSION:=v$(PKG_VERSION)
PKG_MIRROR_HASH:=skip

PKG_BUILD_DEPENDS:=rust/host
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-package.mk

define Package/haut-auth
  SECTION:=net
  CATEGORY:=Network
  TITLE:=HAUT Campus Network Auth Service (Rust)
  URL:=https://github.com/aoxiangtianji/haut-auth-service
  DEPENDS:=$(RUST_ARCH_DEPENDS)
endef

define Package/haut-auth/description
  Srun campus-network auto-authentication daemon for Henan University of
  Technology, written in Rust for a small memory footprint. No Python or
  TLS stack required (the portal is plaintext HTTP).
endef

# The source repo root is a Cargo project.
define Build/Prepare
	$(call Build/Prepare/Default)
endef

define Package/haut-auth/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/bin/haut-auth $(1)/usr/bin/haut-auth
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/etc/config/haut-auth $(1)/etc/config/haut-auth
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/etc/init.d/haut-auth $(1)/etc/init.d/haut-auth
endef

$(eval $(call RustBinPackage,haut-auth))
$(eval $(call BuildPackage,haut-auth))
