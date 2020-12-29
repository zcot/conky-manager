prefix=/usr
bindir=$(prefix)/bin
sharedir=$(prefix)/share
localedir=$(sharedir)/locale
launcherdir=$(sharedir)/applications
mandir=$(sharedir)/man
man1dir=$(mandir)/man1
CFLAGS=--std=c99
app_name=conky-manager2
app_fullname="Conky Manager"

all:
	#build binaries
	valac -X -D'GETTEXT_PACKAGE="${app_name}"' --Xcc="-lm" -X -Wl,-rpath,/usr/share/${app_name}/libs "Main.vala" "MainWindow.vala" "EditWidgetWindow.vala" "EditThemeWindow.vala" "SettingsWindow.vala" "DonationWindow.vala" "GeneratePreviewWindow.vala" "AboutWindow.vala" "Utility.vala" -o ${app_name} --pkg glib-2.0 --pkg gio-unix-2.0 --pkg posix --pkg gtk+-3.0 --pkg gee-0.8 --pkg json-glib-1.0 
	
	#update translation template
	xgettext --language=C --keyword=_ --copyright-holder='Tony George (teejee2008@gmail.com)' --package-name='${app_name}' --package-version='2.0' --msgid-bugs-address='teejee2008@gmail.com' --escape --sort-output -o ../${app_name}.pot *.vala

clean:
	rm -rf *.o ${app_name}
	
install:
	mkdir -p $(DESTDIR)$(bindir)
	mkdir -p $(DESTDIR)$(sharedir)
	mkdir -p $(DESTDIR)$(launcherdir)
	mkdir -p $(DESTDIR)$(sharedir)/${app_name}
	mkdir -p $(DESTDIR)$(sharedir)/pixmaps
	mkdir -p $(DESTDIR)$(sharedir)/appdata
	
	#binary
	install -m 0755 ${app_name} "$(DESTDIR)$(bindir)"
	install -m 0755 ${app_name}-uninstall "$(DESTDIR)$(bindir)"
	
	#launcher
	install -m 0755 ${app_name}.desktop "$(DESTDIR)$(launcherdir)"
	
	#app icon
	install -m 0755 share/pixmaps/${app_name}.png "$(DESTDIR)$(sharedir)/pixmaps"
	
	#appdata.xml
	install -m 0755 ${app_name}.appdata.xml "$(DESTDIR)$(sharedir)/appdata"
	
	#shared files
	cp -dpr --no-preserve=ownership -t "$(DESTDIR)$(sharedir)/${app_name}" ./share/${app_name}/*
	chmod --recursive 0755 $(DESTDIR)$(sharedir)/${app_name}/*
	
	#translations
	mkdir -p "$(DESTDIR)$(localedir)/cs_CZ/LC_MESSAGES"
	msgfmt --check --verbose -o "$(DESTDIR)$(localedir)/cs_CZ/LC_MESSAGES/${app_name}.mo" ../po/${app_name}-cs.po
	
	mkdir -p "$(DESTDIR)$(localedir)/de_DE/LC_MESSAGES"
	msgfmt --check --verbose -o "$(DESTDIR)$(localedir)/de_DE/LC_MESSAGES/${app_name}.mo" ../po/${app_name}-de.po
	
	mkdir -p "$(DESTDIR)$(localedir)/hr_HR/LC_MESSAGES"
	msgfmt --check --verbose -o "$(DESTDIR)$(localedir)/hr_HR/LC_MESSAGES/${app_name}.mo" ../po/${app_name}-hr.po
	
	mkdir -p "$(DESTDIR)$(localedir)/nl_NL/LC_MESSAGES"
	msgfmt --check --verbose -o "$(DESTDIR)$(localedir)/nl_NL/LC_MESSAGES/${app_name}.mo" ../po/${app_name}-nl.po
	
	mkdir -p "$(DESTDIR)$(localedir)/pt_BR/LC_MESSAGES"
	msgfmt --check --verbose -o "$(DESTDIR)$(localedir)/pt_BR/LC_MESSAGES/${app_name}.mo" ../po/${app_name}-pt_BR.po

uninstall:
	#binary
	rm -f "$(DESTDIR)$(bindir)/${app_name}"
	rm -f "$(DESTDIR)$(bindir)/${app_name}-uninstall"
	
	#launcher
	rm -f "$(DESTDIR)$(launcherdir)/${app_name}.desktop"
	
	#app icon
	rm -f "$(DESTDIR)$(sharedir)/pixmaps/${app_name}.png"

	#appdata.xml
	rm -f "$(DESTDIR)$(sharedir)/appdata/${app_name}.appdata.xml"
	
	#shared files
	rm -rf "$(DESTDIR)$(sharedir)/${app_name}"

    #translations
	rm -f $(DESTDIR)$(localedir)/*/LC_MESSAGES/${app_name}.mo
