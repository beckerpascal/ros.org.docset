# ros.org.docset
This repository contains a docset for the Robot Operating System (ROS). It can be used with Zeal or Dash

# Usage

Here is explained how you can add the ROS docset to your docsets

## Feed URL

[https://raw.githubusercontent.com/famalgosner/ros.org.docset/master/ROS.xml](https://raw.githubusercontent.com/famalgosner/ros.org.docset/master/ROS.xml)

## Zeal

Start Zeal and open the Docsets setting (Tools --> Docsets...).  
After all docsets have been updated, click the button *Add feed*.  
Add this Feed URL and the docset will be downloaded. Future updates will be installed automatically.

## Dash

Start Dash and open the preferences.  
Navigate to  *Downloads* and click on the Plus-Symbol on the bottom.  
Add the Feed URL and you are ready to go.

# Included documentations

- actionlib  
- geometry
- geometry2
- image_common
- ros
- ros_comm  
- ros_control  
- roscpp_core  
- vision_opencv

# Credits

Credits go to
- all contributors of ROS and its documentations
- Ved Vyas for doxytag2zealdb

# Build your own docset

There is some nice documentation for building your own docset on the official page here [Dash - Docset Generation Guide](https://kapeli.com/docsets)

To build a docset containing ROS packages you can follow these steps.

1. Check out all repositories you want to add into a folder
2. Run `doxygen Doxyfile` inside the folder. The Doxyfile can be found in this repository. Place in the same folder next to all the ros packages
3. Change into `html` directory
4. Run `make`
5. Now doxygen builds some things and will end with an error as some OSX dependencies are missing. But everything else is fine
6. Run `python -m doxytag2zealdb --tag ../ROS.tag --db ROS.docset/Contents/Resources/docSet.dsidx --include-parent-scopes --include-function-signatures`
  - This will create and fill the SQLite3 database based on the tags created by doxygen
7. Optional: You can add a *logo.png* by copying some logo to the root directory of the docset.
7. Copy the `ROS.docset` folder to the documentation browser library. With Zeal and Linux it is `~/.local/share/Zeal/Zeal/docsets`
8. You are done :-)
