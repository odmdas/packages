include $(TOPDIR)/rules.mk

PKG_NAME:=ctop
PKG_VERSION:=0.7.3
PKG_RELEASE:=1

PKG_SOURCE:=v$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://github.com/bcicen/ctop/archive
PKG_HASH:=3b083b55a7cda7782e370bf03412dbf51ca4a94c1d56325ff70a1545d7a30adc

PKG_MAINTAINER:=Javier Marcet <javier@marcet.info>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1

GO_PKG:=github.com/bcicen/ctop

include $(INCLUDE_DIR)/package.mk
include ../../lang/golang/golang-package.mk

define Package/ctop
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Top-like interface for container metrics
  URL:=https://ctop.sh/
  DEPENDS:=$(GO_ARCH_DEPENDS) @!mips @!mipsel
endef

define Package/ctop/description
  Top-like interface for container metrics
endef

MAKE_PATH:=$(GO_PKG_WORK_DIR_NAME)/build/src/$(GO_PKG)
MAKE_VARS += \
	GOPATH=$(GO_PKG_BUILD_DIR) \
	GOCACHE=$(GO_PKG_CACHE_DIR) \
	GOTMPDIR=$(GO_PKG_TMP_DIR) \
	GOROOT_FINAL=$(GO_TARGET_ROOT) \
	CC=$(TARGET_CC) \
	CXX=$(TARGET_CXX) \
	$(call GoPackage/Environment)
MAKE_FLAGS += \
	COMMIT=$(PKG_SOURCE_VERSION)

define Package/ctop/install
	$(INSTALL_DIR) $(1)/usr/sbin/
	$(INSTALL_BIN) $(GO_PKG_BUILD_BIN_DIR)/ctop $(1)/usr/sbin/
endef

$(eval $(call BuildPackage,ctop))
