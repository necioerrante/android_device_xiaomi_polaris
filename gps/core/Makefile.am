AM_CFLAGS = -I./ \
            -I../utils \
            -I../gnss \
            -I../location \
            -I./data-items \
            -I./data-items/common \
            -I./observer \
            $(LOCPLA_CFLAGS) \
            $(GPSUTILS_CFLAGS) \
            -I$(WORKSPACE)/gps-noship/flp \
            -D__func__=__PRETTY_FUNCTION__ \
            -fno-short-enums \
            -std=c++11

libloc_core_la_h_sources = \
           LocApiBase.h \
           LocAdapterBase.h \
           ContextBase.h \
           LocDualContext.h \
           LBSProxyBase.h \
           UlpProxyBase.h \
           loc_core_log.h \
           LocAdapterProxyBase.h \
           data-items/DataItemId.h \
           data-items/IDataItemCore.h \
           data-items/DataItemConcreteTypesBase.h \
           observer/IDataItemObserver.h \
           observer/IDataItemSubscription.h \
           observer/IFrameworkActionReq.h \
           observer/IOsObserver.h \
           SystemStatusOsObserver.h \
           SystemStatus.h

libloc_core_la_c_sources = \
           LocApiBase.cpp \
           LocAdapterBase.cpp \
           ContextBase.cpp \
           LocDualContext.cpp \
           loc_core_log.cpp \
           data-items/DataItemsFactoryProxy.cpp \
           data-items/common/ClientIndex.cpp \
           data-items/common/DataItemIndex.cpp \
           data-items/common/IndexFactory.cpp \
           SystemStatusOsObserver.cpp \
           SystemStatus.cpp

library_includedir = $(pkgincludedir)/core

library_include_HEADERS = $(libloc_core_la_h_sources)

libloc_core_la_SOURCES = $(libloc_core_la_c_sources)

if USE_GLIB
libloc_core_la_CFLAGS = -DUSE_GLIB $(AM_CFLAGS) @GLIB_CFLAGS@
libloc_core_la_LDFLAGS = -lstdc++ -Wl,-z,defs -lpthread @GLIB_LIBS@ -shared -version-info 1:0:0
libloc_core_la_CPPFLAGS = -DUSE_GLIB $(AM_CFLAGS) $(AM_CPPFLAGS) @GLIB_CFLAGS@
else
libloc_core_la_CFLAGS = $(AM_CFLAGS)
libloc_core_la_LDFLAGS = -Wl,-z,defs -lpthread -shared -version-info 1:0:0
libloc_core_la_CPPFLAGS = $(AM_CFLAGS) $(AM_CPPFLAGS)
endif

libloc_core_la_LIBADD = -lstdc++ -ldl $(LOCPLA_LIBS) $(GPSUTILS_LIBS)

#Create and Install libraries
lib_LTLIBRARIES = libloc_core.la
