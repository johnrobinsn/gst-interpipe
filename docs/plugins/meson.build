# Copy the file provided in input: to a file in the build directory with
# the name output: in the current directory.

types = configure_file(input : 'gst-interpipe.types',
  output : 'gst-interpipe.types',
  copy : true)

version_conf = configuration_data()
version_conf.set('PACKAGE_VERSION', meson.project_version())
version_conf.set('GST_API_VERSION', apiversion)
version_conf.set('PACKAGE_NAME', 'GstInterpipe')
version_conf.set('PACKAGE_URL', pkg_interpipes_url)
configure_file(input : 'gst-interpipe-docs.xml.in',
  output : 'gst-interpipe-docs.xml',
  configuration: version_conf)

# Compiles and installs gtkdoc documentation into prefix/share/gtk-doc/html.
gnome.gtkdoc('gst-interpipes',
  main_xml : '@0@/gst-interpipe-docs.xml'.format(meson.current_build_dir()),
  src_dir : ['@0@/gst/interpipe/'.format(meson.source_root()), meson.current_build_dir()],
  gobject_typesfile : types,
  content_files : [version_entities],
  dependencies : [gst_app_dep],
  install : true)
