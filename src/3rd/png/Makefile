ROOT := ../../../

include $(TOP)$(ROOT)config/global.mk

LIBNAME := png

HB_BUILD_WARN := no
HB_BUILD_MODE := c

C_SOURCES := \
   png.c \
   pngerror.c \
   pngget.c \
   pngmem.c \
   pngpread.c \
   pngread.c \
   pngrio.c \
   pngrtran.c \
   pngrutil.c \
   pngset.c \
   pngtrans.c \
   pngwio.c \
   pngwrite.c \
   pngwtran.c \
   pngwutil.c \

ifeq ($(filter $(HB_COMPILER),poccarm xcc tcc),)

   # Detect libpng

   HB_HAS_PNG :=
   HB_HAS_PNG_LOCAL :=

   # libpng12-dev{deb}
   # libpng-devel{rpm}
   # libpng{homebrew}
   # libpng{pacman}
   # mingw-w64-i686-libpng{msys2&mingw}
   # mingw-w64-x86_64-libpng{msys2&mingw64}

   _DET_DSP_NAME := libpng
   _DET_VAR_INC_ := HB_INC_PNG
   _DET_VAR_HAS_ := HB_HAS_PNG
   _DET_FLT_PLAT :=
   _DET_FLT_COMP :=
   _DET_INC_DEFP := /usr/local/opt/png/include /usr/include /usr/local/include /boot/develop/headers/3rdparty
   _DET_INC_LOCL := src/3rd/png
   _DET_INC_HEAD := /png.h
   include $(TOP)$(ROOT)config/detfun.mk

   ifneq ($(HB_HAS_PNG_LOCAL),)

      ifneq ($(HB_HAS_ZLIB),)

         HB_CFLAGS += $(foreach d,$(HB_HAS_ZLIB),-I$(d))
         HB_CFLAGS_DYN := -DPNG_BUILD_DLL

         # requirement for wce and for win/msvc with -sdl option
         HB_CFLAGS += -DPNG_NO_STDIO

         ifneq ($(filter $(HB_COMPILER),pocc pocc64 poccarm),)
            HB_CFLAGS += -DPNG_ALLOCATED
         endif

         include $(TOP)$(ROOT)config/lib.mk
      else
         HB_SKIP_REASON := $(_DET_RES_TEXT)
         include $(TOP)$(ROOT)config/none.mk
      endif
   else
      HB_SKIP_REASON := local copy unused
      include $(TOP)$(ROOT)config/none.mk
   endif
else
   HB_SKIP_REASON := compiler not supported
   include $(TOP)$(ROOT)config/none.mk
endif

# URL    https://download.sourceforge.net/libpng/libpng-1.6.34.tar.xz
# DIFF   png.diff
#
# MAP    LICENSE
# MAP    png.c
# MAP    pngconf.h
# MAP    scripts/pnglibconf.h.prebuilt  pnglibconf.h
# MAP    pngerror.c
# MAP    pngget.c
# MAP    png.h
# MAP    pngmem.c
# MAP    pngpread.c
# MAP    pngpriv.h
# MAP    pngread.c
# MAP    pngrio.c
# MAP    pngrtran.c
# MAP    pngrutil.c
# MAP    pngset.c
# MAP    pngtrans.c
# MAP    pngwio.c
# MAP    pngwrite.c
# MAP    pngwtran.c
# MAP    pngwutil.c
# MAP    pnginfo.h
# MAP    pngstruct.h
# MAP    pngdebug.h
