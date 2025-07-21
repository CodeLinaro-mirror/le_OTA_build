ACLOCAL_AMFLAGS = -I m4

AM_CPPFLAGS := \
              -I. \
              -I$(WORKSPACE)/system/core/include

if SELINUX_ENABLE
AM_CPPFLAGS += $(LIBSELINUX_CFLAGS)
AM_CPPFLAGS += -DSELINUX_IS_ENABLE
endif

c_sources := fs_config.c
bin_PROGRAMS := fs_config

fs_config_SOURCES := $(c_sources)
fs_config_CPPFLAGS := $(AM_CPPFLAGS)

fs_config_LDFLAGS := -lcutils
fs_config_LDADD := -lcutils

if SELINUX_ENABLE
fs_config_LDFLAGS += -lselinux
fs_config_LDADD += -lselinux
endif

