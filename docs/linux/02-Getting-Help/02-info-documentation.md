
<h1>Info Documentation</h1>

- The info command also provides documentation on operating system commands and features. 
- To display the info documentation of a command : `info command`

Example : 

```bash
info ls 
```

<Details> 

```bash
Next: dir invocation,  Up: Directory listing

10.1 `ls': List directory contents                                     
==================================  

    The `ls' program lists information about files (of any type, including directories).  Options and file arguments can be intermixed arbitrarily, as usual. 

    For non-option command-line arguments that are directories, by    
default `ls' lists the contents of directories, not recursively, and   
omitting files with names beginning with `.'.  For other non-option    
arguments, by default `ls' lists just the file name.  If no non-option 
argument is specified, `ls' operates on the current directory, acting  
as if it had been invoked with a single argument of `.'.                        
                                                                       
    By default, the output is sorted alphabetically, according to the  
locale settings in effect.(1) If standard output is a terminal, the    
output is in columns (sorted vertically) and control characters are    
output as question marks; otherwise, the output is listed one per line 
and control characters are output as-is.

-----Info: (coreutils)ls invocation, 57 lines --Top-----------------------------
Welcome to Info version 6.5.  Type H for help, h for tutorial.   
```
</Details>

---

This documentation is broken up into nodes,

```bash
* Menu:                           

* Which files are listed::                     
* What information is listed::                 
* Sorting the output::                          
* Details about version sort::                   
* General output formatting::                    
* Formatting file timestamps::                    
* Formatting the file names::                                                   
                                         
   ---------- Footnotes ----------                                              
          
 (1) If you use a non-POSIX locale (e.g., by setting `LC_ALL' to 
`en_US'), then `ls' may produce output that is sorted differently than
you're accustomed to.  In that case, set the `LC_ALL' environment     
variable to `C'.       
```