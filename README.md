Add run permissions to exec_permissions.sh and it will add the execute permission to all the .sh files in the directory. Then you can run the .sh download scripts from the command line

Notes on rclone: rclone is pretty versatile, and easy to use. 

If your download stops half way, you can simply re-run it as rclone will not redownload any files that match and are the same size, this means even if one file is only half downloaded, simply re-running the command will fix it as well as not re download everything you already have in the target directory!

the typical rclone command pattern is:

rclone copy "url in the server, Note 1" "local directory path to download to, Note 2" --http-url "http://${USERNAME}:${PASSWORD}@dl.ash2txt.org/" --progress --multi-thread-streams=8 --transfers=8


Note 1: an example is ":http:/full-scrolls/Scroll1.volpkg/volumes/20230205180739" 
in dl.ash2txt.org you can simply copy the url in the browser.
![url from browser](<Example_dlash2text_url.png>)

Note 2: this can either be an absolute path, typically copied from a file explorer, or from the 
command line, but it can also be a relative path from where the rclone is being run.
An example is putting "./scroll1" and rclone will make that directory in its location and copy the files there

The user name and password are the ones provided to you after  agreeing to the data lisence
the last couple --flags are progress, so you can see how the download is progressing in the terminal,
and --multi-thread-streams=8 --transfers=8 which allow rclone to download multiple files at once if it can.

This repo is using python subprocesses to run the rclone commands to add some additonal logic to make downloads easier and more customizable, while maintaining portability across operating systems which would be lost is .sh or .bat etc scripts were used.

Refrences/Data Contributions
EduceLabs scanned and provided the foundational data we are working with

@Spelufo on discord generously open sourced the pherc_0332_53.csv and scroll_1_54_mask.csv volume grid masks, as well as developing the code to create the volume grids.

@james darby on discord developed the code and masked the .tifs for scroll 1 & 2