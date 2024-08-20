We enable `ADB` by using `USB Debugging` in the developer settings on Android Devices. With the help of `adb` cli tool, we can access the file system of Android Devices.

## 4.1 Copy Directories

1. **Phone → PC:**
    
    ```bash
    # Linux:
      # To current directory:
        adb pull -a -p "/sdcard/Path/to/Folder" .
    
      # To specific directory:
        adb pull -a -p "/sdcard/Path/to/Folder" "/path/to/folder"
    
    
    # Windows:
      # To current directory:
        adb pull -a -p "/sdcard/Path/to/Folder" .
    
      # To specific directory:
        adb pull -a -p "/sdcard/Path/to/Folder" "D:\Path\to\Folder"
    ```
    
      
    
2. **PC → Phone:**
    
    ```bash
    # Linux:
      # From current directory:
        adb push -a -p "../<current folder>" "/sdcard/path/to/folder"
    
      # From specific directory:
        adb push -a -p "/path/to/folder" "/sdcard/path/to/folder" 
    
    
    # Windows:
      # To current directory:
        adb push -a -p "..\<current folder>" "/sdcard/Path/to/Folder"
    
      # From specific directory:
        adb push -a -p "D:\Path\to\Folder" "/sdcard/Path/to/Folder" 
    ```