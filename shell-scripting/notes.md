

refer the website for tutorial
https://www.tutorialspoint.com/unix/unix-file-operators.htm

The below snippet tests if the command exits
````
command_exist(){
 command -v "$@" > /dev/null 2> &1
}
````
2>&1 redirect the stderr to stdout(not sure yet). refer the link below
https://stackoverflow.com/questions/818255/in-the-shell-what-does-21-mean


