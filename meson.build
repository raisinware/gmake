project('gmake', 'c')

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
# check token ['HAVE_ATEXIT']
# check token ['HAVE_CASE_INSENSITIVE_FS']
  ['HAVE_CLOCK_GETTIME', 'clock_gettime', '#include<time.h>'],
# check token ['HAVE_DECL_BSD_SIGNAL']
# check token ['HAVE_DECL_DLERROR']
# check token ['HAVE_DECL_DLOPEN']
# check token ['HAVE_DECL_DLSYM']
# check token ['HAVE_DECL_GETLOADAVG']
# check token ['HAVE_DECL_SYS_SIGLIST']
# check token ['HAVE_DECL__SYS_SIGLIST']
# check token ['HAVE_DECL___SYS_SIGLIST']
# check token ['HAVE_DOS_PATHS']
# check token ['HAVE_DUP']
  ['HAVE_DUP2', 'dup2', '#include<unistd.h>'],
# check token ['HAVE_FDOPEN']
  ['HAVE_FORK', 'fork', '#include<unistd.h>'],
# check token ['HAVE_GETCWD']
  ['HAVE_GETGROUPS', 'getgroups', '#include<grp.h>'],
# check token ['HAVE_GETRLIMIT']
  ['HAVE_GETTIMEOFDAY', 'gettimeofday', '#include<sys/time.h>'],
# check token ['HAVE_GUILE']
# check token ['HAVE_INTMAX_T']
# check token ['HAVE_ISATTY']
# check token ['HAVE_LONG_LONG_INT']
  ['HAVE_LSTAT', 'lstat', '#include<sys/stat.h>'],
# check token ['HAVE_MEMPCPY']
  ['HAVE_MEMRCHR', 'memrchr', '#include<string.h>'],
  ['HAVE_MKFIFO', 'mkfifo', '#include<sys/stat.h>'],
# check token ['HAVE_MKSTEMP']
# check token ['HAVE_MKTEMP']
  ['HAVE_PIPE', 'pipe', '#include<unistd.h>'],
# check token ['HAVE_POSIX_SPAWN']
# check token ['HAVE_POSIX_SPAWNATTR_SETSIGMASK']
# check token ['HAVE_PSELECT']
  ['HAVE_READLINK', 'readlink', '#include<unistd.h>'],
# check token ['HAVE_REALPATH']
# check token ['HAVE_SA_RESTART']
  ['HAVE_SETEGID', 'setegid', '#include<unistd.h>'],
  ['HAVE_SETEUID', 'seteuid', '#include<unistd.h>'],
# check token ['HAVE_SETLINEBUF']
  ['HAVE_SETREGID', 'setregid', '#include<unistd.h>'],
  ['HAVE_SETREUID', 'setreuid', '#include<unistd.h>'],
# check token ['HAVE_SETRLIMIT']
  ['HAVE_SETVBUF', 'setvbuf', '#include<unistd.h>'],
  ['HAVE_SIGACTION', 'sigaction', '#include<signal.h>'],
# check token ['HAVE_SIGSETMASK']
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
# check token ['HAVE_STRUCT_DIRENT_D_TYPE']
# check token ['HAVE_TTYNAME']
# check token ['HAVE_UINTMAX_T']
# check token ['HAVE_UMASK']
# check token ['HAVE_UNION_WAIT']
# check token ['HAVE_UNSIGNED_LONG_LONG_INT']
  ['HAVE_VFORK', 'vfork', '#include<unistd.h>'],
  ['HAVE_WAIT3', 'wait3', '#include<sys/wait.h>'],
  ['HAVE_WAITPID', 'waitpid', '#include<sys/wait.h>'],
# check token ['HAVE_WORKING_FORK']
# check token ['HAVE_WORKING_VFORK']
]

foreach f: check_functions
  if cc.has_function(f.get(1), prefix: f.get(2))
    cdata.set(f.get(0), 1)
  endif
endforeach

subdir('src')