=========================================
Dataset characteristics
=========================================	
day.csv have the following fields:
	
	- instant: record index
	- dteday : date
	- season : season (1:spring, 2:summer, 3:fall, 4:winter)
	- yr : year (0: 2018, 1:2019)
	- mnth : month ( 1 to 12)
	- holiday : weather day is a holiday or not (extracted from http://dchr.dc.gov/page/holiday-schedule)
	- weekday : day of the week
	- workingday : if day is neither weekend nor holiday is 1, otherwise is 0.
	+ weathersit : 
		- 1: Clear, Few clouds, Partly cloudy, Partly cloudy
		- 2: Mist + Cloudy, Mist + Broken clouds, Mist + Few clouds, Mist
		- 3: Light Snow, Light Rain + Thunderstorm + Scattered clouds, Light Rain + Scattered clouds
		- 4: Heavy Rain + Ice Pallets + Thunderstorm + Mist, Snow + Fog
	- temp : temperature in Celsius
	- atemp: feeling temperature in Celsius
	- hum: humidity
	- windspeed: wind speed
	- casual: count of casual users
	- registered: count of registered users
	- cnt: count of total rental bikes including both casual and registered
	
=========================================
License
=========================================
Use of this dataset in publications must be cited to the following publication:

[1] Fanaee-T, Hadi, and Gama, Joao, "Event labeling combining ensemble detectors and background knowledge", Progress in Artificial Intelligence (2013): pp. 1-15, Springer Berlin Heidelberg, doi:10.1007/s13748-013-0040-3.

@article{
	year={2013},
	issn={2192-6352},
	journal={Progress in Artificial Intelligence},
	doi={10.1007/s13748-013-0040-3},
	title={Event labeling combining ensemble detectors and background knowledge},
	url={http://dx.doi.org/10.1007/s13748-013-0040-3},
	publisher={Springer Berlin Heidelberg},
	keywords={Event labeling; Event detection; Ensemble learning; Background knowledge},
	author={Fanaee-T, Hadi and Gama, Joao},
	pages={1-15}
}

=========================================
Contact
=========================================
	
For further information about this dataset please contact Hadi Fanaee-T (hadi.fanaee@fe.up.pt)


--- junos/lib/librepd/Makefile  (revision 1228660)  
+++ junos/lib/librepd/Makefile  (working copy)
@@ -29,8 +34,8 @@
        repd_statesync.c \
        repd_ui.c \
        repd_util.c \
-
-.if ${TARGET_OS} == "${UBUNTU_OS}"
+
+.if ${TARGET_OS} == "${LINUX_OS}"
 CFLAGS += \
        -I${RELSRCTOP_JUNOS}/lib/librepd/hiredis
 SRCS += \
@@ -61,22 +66,34 @@
        -I${SRCTOP}/pfe-shared/include/jnx \
        -I${INC_libsdb} \
        -I${SRCTOP}/junos/lib/libstatesync-pub-sub/h/jnx \
-
+       -I${TOPDIR}/usp/lib/libssam

 .if ${NGSTATS_PERF:Uno:tl} != "yes"
-CFLAGS += -O0 -fno-strict-aliasing -fno-inline
+CFLAGS += -O0 -fno-strict-aliasing
 .endif

 CFLAGS.linux += \
        -Wno-unused-const-variable
+CFLAGS.evo += \
+       -Wno-unused-but-set-variable \
+       -Wno-cast-qual \
+       -Wno-declaration-after-statement \
+       -Wno-switch-unreachable \
+       -Wno-missing-prototypes \
+       -Wno-shadow \
+       -Wno-implicit-function-declaration \
+       -Wno-error=nested-externs

+.if ${TARGET_OS} != "${LINUX_OS}"
 DPLIBS += \
+        ${LIBSSAM} \
+        ${LIBSRX-HAPEER}
+.endif
+DPLIBS += \
        ${LIBDDL-ACCESS} \
        ${LIBIPCCONN} \
        ${LIBRPD} \
        ${LIBSDB} \
-       ${LIBSSAM} \
-       ${LIBSRX-HAPEER} \
        ${LIBJUNOS-SDK} \
        ${LIBISC} \
        ${LIBJIPC} \
                               
