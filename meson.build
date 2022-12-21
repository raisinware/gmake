project('gmake', 'c',
        version: '4.4',
        license: 'GPL-3.0-or-later',
default_options: 'c_std=c99')
incdir = include_directories('lib')

gmake_fullname  = 'GNU Make (meson port)'
gmake_bugreport = 'bug-make@gnu.org'
gmake_url       = 'https://github.com/raisinware/gmake'

add_project_arguments('-D_DEFAULT_SOURCE', language : 'c')
add_project_arguments('-D_GNU_SOURCE', language : 'c')
add_project_arguments('-D_BSD_SOURCE', language : 'c')


cc = meson.get_compiler('c')
cdata = configuration_data()
check_headers = [
  'dirent.h',
  'fcntl.h',
  'inttypes.h',
  'limits.h',
  'locale.h',
  'memory.h',
  'minix/config.h',
  'ndir.h',
  'spawn.h',
  'stdint.h',
  'stdio.h',
  'stdlib.h',
  'strings.h',
  'string.h',
  'sys/dir.h',
  'sys/file.h',
  'sys/ndir.h',
  'sys/param.h',
  'sys/resource.h',
  'sys/select.h',
  'sys/stat.h',
  'sys/timeb.h',
  'sys/time.h',
  'sys/types.h',
  'sys/wait.h',
  'unistd.h',
  'vfork.h',
  'wchar.h',
]

foreach h: check_headers
  if cc.has_header(h)
    cdata.set('HAVE_' + h.underscorify().to_upper(), 1)
  endif
endforeach

check_functions = [
  ['HAVE_ATEXIT', 'atexit', '#include<stdlib.h>'],
# check token ['HAVE_CASE_INSENSITIVE_FS'], not a function
  ['HAVE_CLOCK_GETTIME', 'clock_gettime', '#include<time.h>'],
# check token ['HAVE_DECL_BSD_SIGNAL']
# check token ['HAVE_DECL_DLERROR']
# check token ['HAVE_DECL_DLOPEN']
# check token ['HAVE_DECL_DLSYM']
# check token ['HAVE_DECL_GETLOADAVG']
# check token ['HAVE_DECL_SYS_SIGLIST']
# check token ['HAVE_DECL__SYS_SIGLIST']
# check token ['HAVE_DECL___SYS_SIGLIST']
# check token ['HAVE_DOS_PATHS'], not a function
  ['HAVE_DUP', 'dup', '#include<unistd.h>'],
  ['HAVE_DUP2', 'dup2', '#include<unistd.h>'],
  ['HAVE_FDOPEN', 'fdopen', '#include<stdio.h>'],
  ['HAVE_FORK', 'fork', '#include<unistd.h>'],
  ['HAVE_GETCWD', 'getcwd', '#include<unistd.h>'],
  ['HAVE_GETGROUPS', 'getgroups', '#include<grp.h>'],
  ['HAVE_GETRLIMIT', 'getrlimit', '#include<sys/resource.h>'],
  ['HAVE_GETTIMEOFDAY', 'gettimeofday', '#include<sys/time.h>'],
# check token ['HAVE_GUILE'], not a function
# check token ['HAVE_INTMAX_T'], not a function
  ['HAVE_ISATTY', 'isatty', '#include<unistd.h>'],
# check token ['HAVE_LONG_LONG_INT'], not a function
  ['HAVE_LSTAT', 'lstat', '#include<sys/stat.h>'],
  ['HAVE_MEMPCPY', 'mempcpy', '#include<string.h>'],
  ['HAVE_MEMRCHR', 'memrchr', '#include<string.h>'],
  ['HAVE_MKFIFO', 'mkfifo', '#include<sys/stat.h>'],
  ['HAVE_MKSTEMP', 'mkstemp', '#include<stdlib.h>'],
  ['HAVE_MKTEMP', 'mktemp', '#include<stdlib.h>'],
  ['HAVE_PIPE', 'pipe', '#include<unistd.h>'],
  ['HAVE_POSIX_SPAWN', 'posix_spawn', '#include<spawn.h>'],
  ['HAVE_POSIX_SPAWNATTR_SETSIGMASK', 'posix_spawnattr_setsigmask', '#include<signal.h>\n#include<spawn.h>'],
  ['HAVE_PSELECT', 'pselect', '#include<sys/select.h>'],
  ['HAVE_READLINK', 'readlink', '#include<unistd.h>'],
  ['HAVE_REALPATH', 'realpath', '#include<stdlib.h>'],
# check token ['HAVE_SA_RESTART'], not a function
  ['HAVE_SETEGID', 'setegid', '#include<unistd.h>'],
  ['HAVE_SETEUID', 'seteuid', '#include<unistd.h>'],
  ['HAVE_SETLINEBUF', 'setlinebuf', '#include<stdio.h>'],
  ['HAVE_SETREGID', 'setregid', '#include<unistd.h>'],
  ['HAVE_SETREUID', 'setreuid', '#include<unistd.h>'],
  ['HAVE_SETRLIMIT', 'setrlimit', '#include<sys/resource.h>'],
  ['HAVE_SETVBUF', 'setvbuf', '#include<unistd.h>'],
  ['HAVE_SIGACTION', 'sigaction', '#include<signal.h>'],
  ['HAVE_SIGSETMASK', 'sigsetmask', '#include<signal.h>'],
  ['HAVE_STPCPY', 'stpcpy', '#include<string.h>'],
  ['HAVE_STRCASECMP', 'strcasecmp', '#include<strings.h>'],
  ['HAVE_STRCMPI', 'strcmpi', '#include<string.h>'],
  ['HAVE_STRCOLL', 'strcoll', '#include<string.h>'],
  ['HAVE_STRDUP', 'strdup', '#include<string.h>'],
  ['HAVE_STRERROR', 'strerror', '#include<string.h>'],
  ['HAVE_STRICMP', 'stricmp', '#include<string.h>'],
  ['HAVE_STRNCASECMP', 'strncasecmp', '#include<strings.h>'],
  ['HAVE_STRNCMPI', 'strncmpi', '#include<string.h>'],
  ['HAVE_STRNDUP', 'strndup', '#include<string.h>'],
  ['HAVE_STRNICMP', 'strnicmp', '#include<string.h>'],
  ['HAVE_STRSIGNAL', 'strsignal', '#include<signal.h>'],
  ['HAVE_STRTOLL', 'strtoll', '#include<stdlib.h>'],
# check token ['HAVE_STRUCT_DIRENT_D_TYPE'], not a function
  ['HAVE_TTYNAME', 'setreuid', '#include<unistd.h>'],
# check token ['HAVE_UINTMAX_T'], not a function
  ['HAVE_UMASK', 'umask', '#include<sys/stat.h>'],
# check token ['HAVE_UNION_WAIT'], not a function
# check token ['HAVE_UNSIGNED_LONG_LONG_INT'], not a function
  ['HAVE_VFORK', 'vfork', '#include<unistd.h>'],
  ['HAVE_WAIT3', 'wait3', '#include<sys/wait.h>'],
  ['HAVE_WAITPID', 'waitpid', '#include<sys/wait.h>'],
# check token ['HAVE_WORKING_FORK'], not a function
# check token ['HAVE_WORKING_VFORK'], not a function
]

foreach f: check_functions
  if cc.has_function(f.get(1), prefix: f.get(2))
    cdata.set(f.get(0), 1)
  endif
endforeach

cdata.set_quoted('LIBDIR',    '/usr/local/lib')
cdata.set_quoted('LOCALEDIR', '/usr/local/share/locale')
cdata.set_quoted('SCCS_GET',  'false')

subdir('src')