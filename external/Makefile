override MAKEOPTS:=

all: $(INTERNAL_GRIB2_PATH)/lib/libz.a $(INTERNAL_GRIB2_PATH)/lib/libpng.a $(INTERNAL_GRIB2_PATH)/lib/libjasper.a

$(INTERNAL_GRIB2_PATH)/lib/libz.a:
	(cd zlib-1.2.11; ./configure --prefix=$(INTERNAL_GRIB2_PATH) --static && make && make install)

$(INTERNAL_GRIB2_PATH)/lib/libpng.a: $(INTERNAL_GRIB2_PATH)/lib/libz.a
	(cd libpng-1.6.37; ./configure --prefix=$(INTERNAL_GRIB2_PATH) --disable-shared --with-zlib-prefix=$(INTERNAL_GRIB2_PATH) && make && make install)

$(INTERNAL_GRIB2_PATH)/lib/libjasper.a:
	(cd jasper-1.900.1; ./configure --prefix=$(INTERNAL_GRIB2_PATH) && make && make install)

clean:
	(cd zlib-1.2.11; $(MAKE) clean)
	(cd libpng-1.6.37; $(MAKE) clean)
	(cd jasper-1.900.1; $(MAKE) clean)
	(rm -rf $(INTERNAL_GRIB2_PATH))
