include $(TOPDIR)/rules.mk

PKG_NAME:=glorytun
PKG_VERSION:=1.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/vriksterr/glorytun.git
PKG_SOURCE_VERSION:=master
# for reproducible builds, pin a commit instead:
# PKG_SOURCE_VERSION:=<full 40-char commit sha>
PKG_MIRROR_HASH:=skip

PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/glorytun
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+kmod-tun +libsodium +librt
	TITLE:=Glorytun
	URL:=https://github.com/vriksterr/glorytun.git
	SUBMENU:=VPN
endef

define Package/glorytun/description
	Glorytun is a vpn designed to improve your internet connectivity:
	- Fast and highly secure.
	- Multipath and active failover.
	- Traffic shaping.
	- Path MTU discovery without ICMP.
endef

define Package/glorytun/conffiles
/etc/config/glorytun
endef

define Package/glorytun/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/glorytun $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) init $(1)/etc/init.d/glorytun
	$(INSTALL_DIR) $(1)/etc/config
	touch $(1)/etc/config/glorytun
endef

$(eval $(call BuildPackage,glorytun-vrxtr))
