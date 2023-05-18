

# FileInfo和DirectoryInfo的属性列表

| 属性                        | 说明                                 |
| --------------------------- | ------------------------------------ |
| CreationTime                | 创建文件或文件夹的时间               |
| DirectoryName(用于FileInfo) | 包含文件夹的完整路径                 |
| Parent(用于DirectoryInfo)   | 指定子目录的父目录                   |
| Exists                      | 文件或文件夹是否存在                 |
| Extension                   | 文件的扩展名，对于文件夹，它返回空白 |
| FullName                    | 文件或文件夹的完整路径名             |
| LastAccessTime              | 最后一次访问文件或文件夹的时间       |
| LastWriteTime               | 最后一个修改文件或文件夹的时间       |
| Name                        | 文件或文件夹的名称                   |
| Root（仅用于DirectoryInfo） | 路径的根部分                         |
| Length（仅用于FileInfo）    | 返回文件的大小（以字节为单位）       |

# FileInfo和DirectoryInfo的方法列表

| 方法                 | 说明                                                         |
| -------------------- | ------------------------------------------------------------ |
| Create()             | 创建给定名称的文件夹或者空文件，对于FileInfo,该方法会返回一个流 对象，以便于写入文件 |
| Delete()             | 删除文件或文件夹。对于文件夹有一个可以递归的Delete选项       |
| MoveTo()             | 移动或重命名文件或文件夹                                     |
| CopyTo()             | (只用于FileInfo)复制文件，文件夹没有复制方法，如果想要复制完整的 目录树，需要单独复制每个文件和文件夹 |
| GetDirectories()     | (只适用于DirectoryInfo)返回DirectoryInfo对象数组，该数组 表示文件夹中包含的所有文件夹 |
| GetFiles()           | (只适用于DirectoryInfo)返回FileInfo对象数组，该数组表示 文件夹中所有的文件 |
| GetFileSystemInfos() | (只适用于DirectoryInfo)返回FileInfo和DirectoryInfo对象， 它把文件夹中包含的所有对象表示为一个FileSystemInfo引用数组 |
|                      |                                                              |
|                      |                                                              |

