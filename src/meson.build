mkconfig_data = configuration_data()

mkconfig_data.set('PACKAGE_NAME',      gmake_fullname)
mkconfig_data.set('PACKAGE',           meson.project_name())
mkconfig_data.set('PACKAGE_VERSION',   meson.project_version())
mkconfig_data.set('PACKAGE_URL',       gmake_url)
mkconfig_data.set('PACKAGE_BUGREPORT', gmake_bugreport)
mkconfig_data.set('PACKAGE_TARNAME',   meson.project_name())

configure_file(input:         'mkconfig.h.in',
               output:        'mkconfig.h',
               configuration:  mkconfig_data)


configure_file(input: 'config.h.meson',
               output: 'config.h',
               configuration: cdata)

make_src = files('ar.c',
                 'arscan.c',
                 'commands.c',
                 'commands.h',
                 'debug.h',
                 'default.c',
                 'dep.h',
                 'dir.c',
                 'expand.c',
                 'file.c',
                 'filedef.h',
                 'function.c',
                 'getopt.c',
                 'getopt.h',
                 'getopt1.c',
                 'gettext.h',
                 'guile.c',
                 'hash.c',
                 'hash.h',
                 'implicit.c',
                 'job.c',
                 'job.h',
                 'load.c',
                 'loadapi.c',
                 'main.c',
                 'makeint.h',
                 'misc.c',
                 'os.h',
                 'output.c',
                 'output.h',
                 'read.c',
                 'remake.c',
                 'rule.c',
                 'rule.h',
                 'shuffle.h',
                 'shuffle.c',
                 'signame.c',
                 'strcache.c',
                 'variable.c',
                 'variable.h',
                 'version.c',
                 'vpath.c',
                 'remote-stub.c',
                 'posixos.c')

make_bin = executable('gmake', make_src,
          include_directories: incdir)