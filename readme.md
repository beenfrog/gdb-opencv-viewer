## Description
View OpenCV Mat in GDB, Code from: [Visualize in memory OpenCV image or matrix from GDB pretty printers](https://sourceware.org/ml/gdb/2013-04/msg00104.html)

## How to use
* Required packages: opencv, python wrapper for opencv (cv2), python, numpy
* Clone this repository
```
git clone git@github.com:beenfrog/gdb-opencv-viewer.git
```
* Add the follow lines in ~/.gdbinit. The alias command is optional.
```
source /FULL-PATH-OF-THE-FILE/cvplot.py
alias view = plot
alias imshow = plot
```
* Usage
```
plot m, the m is an object of cv2::Mat
view m, if you set alias view = plot
imshow m, if you set alias imshow = plot
```

## Demo
* debug and view image in gdb:
```
cd gdb-opencv-viewer
mkdir Debug && cd Debug
cmake -DCMAKE_BUILD_TYPE=Debug .. && make
gdb ./viewer
break 22
run
plot img_color
plot img_gray
```
* NOTE: There may be some bugs with the imshow in python under GNU/Linux, which make you unable to close the image by click the "close" button on the dialog, but you can just click the image and press any key to close the image dialog.

## Others
It is easy to print the C++ STL elements such as vector, map with [GDB evaluators/views/utilities](http://www.yolinux.com/TUTORIALS/src/dbinit_stl_views-1.03.txt)

* Install
```
wget http://www.yolinux.com/TUTORIALS/src/dbinit_stl_views-1.03.txt
cat dbinit_stl_views-1.03.txt >> ~/.gdbinit
```

* Demo (continue from the previous demo)
```
pvector vec
pmap str_int_map char* int
...
see more from the raw file: dbinit_stl_views-1.03.txt
```


## Similar Projects to Show Image in GDB
* [gdb-imshow](https://github.com/renatoGarcia/gdb-imshow)
* [GDB-ImageWatch](https://github.com/cuekoo/GDB-ImageWatch)
* [matrix-viewer](https://github.com/crep4ever/matrix-viewer)
* [gdb-imagewatch](https://github.com/csantosbh/gdb-imagewatch)