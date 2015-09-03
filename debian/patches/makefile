Description: Remove CFLAG and LDFlags for hardening, remove installman 
to stop installation of gzipped manpages, added directory install for
SBIN_DIR
Author: Dave Hibberd <d@vehibberd.com>
---
This patch header follows DEP-3: http://dep.debian.net/deps/dep3/

--- a/Makefile.in
+++ b/Makefile.in
@@ -3,8 +3,8 @@
 CC = gcc
 LD = gcc
 # CFLAGS = -O2 -g -s -Wstrict-prototypes
-CFLAGS = -O2 -g -Wno-unused-result -Wstrict-prototypes
-LDFLAGS =
+#CFLAGS = -O2 -g -Wno-unused-result -Wstrict-prototypes
+#LDFLAGS =
 LIBS = -lax25 -lax25io
 
 include Makefile.include
@@ -24,7 +24,7 @@
 .c.o:
 	$(CC) $(CFLAGS) -c $<
 
-install: installbin installman installhelp installconf
+install: installbin installhelp installconf
 	install -m 755    -D -d	$(VAR_DIR)
 	install -m 755    -D -d	$(VAR_DIR)/node
 	install -m 644    -p etc/loggedin	$(VAR_DIR)/node
@@ -33,6 +33,7 @@
 	install -m 644    -p etc/gateways	 $(VAR_DIR)/flex
 	
 installbin: all
+	install -m 755    -D -d $(SBIN_DIR)
 	install -m 755 	-s -p	uronode		$(SBIN_DIR)
 	install -m 755  -s -p	nodeusers	$(SBIN_DIR)
 	install -m 755  -s -p	axdigi		$(SBIN_DIR)
@@ -53,16 +54,7 @@
 	install -m 600    -p etc/uronode.routes   $(ETC_DIR)
 	install -m 600    -p etc/flexd.conf  $(ETC_DIR)
 
-installman:
-	install -m 755	  -D -d $(MAN_DIR)/man1 $(MAN_DIR)/man5 $(MAN_DIR)/man8
-	install -m 644    -p man/nodeusers.1.gz  $(MAN_DIR)/man1
-	install -m 644    -p man/uronode.conf.5.gz  $(MAN_DIR)/man5
-	install -m 644    -p man/uronode.perms.5.gz $(MAN_DIR)/man5
-	install -m 644    -p man/flexd.conf.5.gz $(MAN_DIR)/man5
-	install -m 644    -p man/uronode.8.gz       $(MAN_DIR)/man8
-	install -m 644	  -p man/axdigi.8.gz	 $(MAN_DIR)/man8
-
-upgrade: installman
+upgrade:
 	install -m 755 -p uronode       $(SBIN_DIR)
 	install -m 755 -p nodeusers     $(SBIN_DIR)
 	install -m 755 -p flexd		$(SBIN_DIR)
