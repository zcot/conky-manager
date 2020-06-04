project('conky-manager2', ['c','vala'])

sources = [
        'src/AboutWindow.vala',
        'src/GeneratePreviewWindow.vala',
        'src/Main.vala',
        'src/MainWindow.vala',
        'src/SettingsWindow.vala',
        'src/DonationWindow.vala',
        'src/EditThemeWindow.vala',
        'src/Utility.vala',
        'src/EditWidgetWindow.vala',
        'src/XidHelper.vala'
]

dependencies = [
    dependency('glib-2.0'),
    dependency('gobject-2.0'),
    dependency('gtk+-3.0'),
    dependency('gee-0.8'),
    dependency('json-glib-1.0')
]

executable('conky-manager2', sources, dependencies: dependencies)
