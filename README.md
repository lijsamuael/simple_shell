access - check real user's permissions for a file   => int access(const char *pathname, int mode); => access() checks whether the calling process can access the file pathname. If pathname is a symbolic link, it is dereferenced.

chdir, fchdir - change working directory   => int fchdir(int fd);   =>  chdir() changes the current working directory of the calling process to the directory specified in path.

close - close a file descriptor   =>  int close(int fd);   =>  close() closes a file descriptor, so that it no longer refers to any file and may be reused.

closedir - close a directory   =>  int closedir(DIR *dirp);   =>  The closedir() function closes the directory stream associated with dirp. A successful call to closedir() also closes the underlying file descriptor associated with dirp. The directory stream descriptor dirp is not available after this call.

execve - execute program   =>   int execve(const char *filename, char *const argv[]  =>  execve() executes the program pointed to by filename. filename must be either a binary executable, or a script starting with a line of the form:

exit - cause normal process termination   =>  void exit(int status);    =>  The exit() function causes normal process termination and the value of status & 0377 is returned to the parent (see wait(2)).

_exit, _Exit - terminate the calling process   =>  void _exit(int status);   =>  The function _exit() terminates the calling process "immediately". Any open file descriptors belonging to the process are closed; any children of the process are inherited by process 1, init, and the process's parent is sent a SIGCHLD signal.

fflush - flush a stream   =>  int fflush(FILE *stream);   =>  For output streams, fflush() forces a write of all user-space buffered data for the given output or update stream via the stream's underlying write function. For input streams, fflush() discards any buffered data that has been fetched from the underlying file, but has not been consumed by the application. The open status of the stream is unaffected.

fork - create a child process   =>  pid_t fork(void   =>  fork() creates a new process by duplicating the calling process. The new process, referred to as the child, is an exact duplicate of the calling process, referred to as the parent,

malloc, free, calloc, realloc - allocate and free dynamic memory   =>  void *malloc(size_t size); void free(void *ptr);void *calloc(size_t nmemb, size_t size);void *realloc(void *ptr, size_t size);
getcwd, getwd, get_current_dir_name - get current working directory   =>  char *getcwd(char *buf, size_t size);   =>  These functions return a null-terminated string containing an absolute pathname that is the current working directory of the calling process. The pathname is returned as the function result and via the argument buf, if present.
getline, getdelim - delimited string input   =>  ssize_t getline(char **lineptr, size_t *n, FILE *stream);   =>   getline() reads an entire line from stream, storing the address of the buffer containing the text into *lineptr. The buffer is null-terminated and includes the newline character, if one was found.
getpid, getppid - get process identification   =>  pid_t getpid(void);  pid_t getppid(void);   =>  getpid() returns the process ID of the calling process. (This is often used by routines that generate unique temporary filenames.)

isatty - test whether a file descriptor refers to a terminal   =>  int isatty(int fd);   =>   The isatty() function tests whether fd is an open file descriptor referring to a terminal.

kill - terminate a process   =>  kill [-s signal|-p] [--] pid...  kill -l [signal]   =>  The command kill sends the specified signal to the specified process or process group. If no signal is specified, the TERM signal is sent. The TERM signal will kill processes which do not catch this signal. For other processes, it may be necessary to use the KILL (9) signal, since this signal cannot be caught.

open - open a file    =>  int open(const char *path, int oflag, ... );   =>  The open() function shall establish the connection between a file and a file descriptor. It shall create an open file description that refers to a file and a file descriptor that refers to that open file description. The file descriptor is used by other I/O functions to refer to that file. The path argument points to a pathname naming the file.

opendir, fdopendir - open a directory   =>  DIR *opendir(const char *name);   =>  The opendir() function opens a directory stream corresponding to the directory name, and returns a pointer to the directory stream. The stream is positioned at the first entry in the directory.

perror - print a system error message   =>  void perror(const char *s);   =>  The routine perror() produces a message on the standard error output, describing the last error encountered during a call to a system or library function. First (if s is not NULL and *s is not a null byte ('\0')) the argument string s is printed, followed by a colon and a blank. Then the message and a new-line.

read - read from a file descriptor   =>  ssize_t read(int fd, void *buf, size_t count);  =>  read() attempts to read up to count bytes from file descriptor fd into the buffer starting at buf. On files that support seeking, the read operation commences at the current file offset, and the file offset is incremented by the number of bytes read. If the current file offset is at or past the end of file, no bytes are read, and read() returns zero.

readdir, readdir_r - read a directory   =>  struct dirent *readdir(DIR *dirp);  int readdir_r(DIR *dirp, struct dirent *entry, struct dirent **result)   =>  The readdir() function returns a pointer to a dirent structure representing the next directory entry in the directory stream pointed to by dirp. It returns NULL on reaching the end of the directory stream or if an error occurred.

signal - ANSI C signal handling   =>  sighandler_t signal(int signum, sighandler_t handler);   =>     typedef void (*sighandler_t)(int);   =>  signal() sets the disposition of the signal signum to handler, which is either SIG_IGN, SIG_DFL, or the address of a programmer-defined function (a "signal handler").

stat - display file or file system status   =>  stat [OPTION]... FILE...   =>  

lstat - get symbolic link status   =>  int lstat(const char *restrict path, struct stat *restrict buf);   =>  The lstat() function shall be equivalent to stat(), except when path refers to a symbolic link. In that case lstat() shall return information about the link, while stat() shall return information about the file the link references.

fstat- get file status    =>  int fstat(int fd, struct stat *buf);   =>  fstat() is identical to stat(), except that the file to be stat-ed is specified by the file descriptor fd.

strtok, strtok_r - extract tokens from strings   =>  char *strtok(char *str, const char *delim);   =>  The strtok() function parses a string into a sequence of tokens. On the first call to strtok() the string to be parsed should be specified in str. In each subsequent call that should parse the same string, str should be NULL.

wait waitid - wait for process to change state   =>  pid_t wait(int *status);   =>  The wait() system call suspends execution of the calling process until one of its children terminates. The call wait(&status) is equivalent to:

waitpid,   =>  pid_t waitpid(pid_t pid, int *status, int options);  =>  The waitpid() system call suspends execution of the calling process until a child specified by pid argument has changed state. By default, waitpid() waits only for terminated children, but this behavior is modifiable via the options argument, as described below.   =>  waitpid(-1, &status, 0);

wait3   =>  pid_t wait3(int *status, int options, struct rusage *rusage);  =>  In other words, wait3() waits of any child, while wait4() can be used to select a specific child, or children, on which to wait. See wait(2) for further details.

wait4 - wait for process to change state, BSD style   =>  pid_t wait4(pid_t pid, int *status, int options, struct rusage *rusage);

write - write to a file descriptor   =>  ssize_t write(int fd, const void *buf, size_t count);   =>  write() writes up to count bytes from the buffer starting at buf to the file referred to by the file descriptor fd.

