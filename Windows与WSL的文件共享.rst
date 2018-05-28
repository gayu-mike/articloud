Windows 与 WSL 的文件共享
========================

WSL(Windows Subsystem for Linux) 的出现使得在 Windows 中使用 Linux 工具成为可能，
这对开发者来说是非常吸引的。 虽然 WSL 被设计成相对独立的系统，完全可以只把开发任务放在
WSL 而让 Windows 来担当别的任务。但几乎不可避免的，这样的情况会经常出现：
**同样一个代码片段，我们既想在 Windows 中访问，也想在 WSL 中访问。**

如果需要这样做，首先请牢记下面的警告：

.. warn::
    可以从 WSL 访问 Windows 的文件。
    不要从 Windows 访问 WSL 文件。

对于这条警告，更准确地来说是：
**不要使用任何 Windows 的工具、应用、脚本、控制台等来创建、修改、打开 WSL
中的文件。**
WSL 中的文件是指：
    ``%localappdata%\CanonicalGroupLimited.UbuntuonWindows_[...]\LocalState\rootfs``

    （也就是 ``c:\users\<username>\appdata\local\[...]`` ）下的所有文件。
    （相当于 Linux 的 ``/`` 目录）

这是因为，不同的操作系统其文件的元数据（权限、所有者、时间戳等）不同，
一个操作系统不能识别另一个操作系统的文件，也就是 Windows/Linux 本来就
无法正确打开对方的文件。

而 WSL 在 Linux 文件系统的基础上，特地增加了 NTFS 拓展，并为同一机器中的 Windows
文件提供“伪元数据”，因此能正确地增删改查 Linux/Windows 两种系统的文件。

最佳实践
---------

在 Windows 和 WSL 之间工作并且共享文件，最佳方案是“软链接”

.. code-block:: console

    ln -s "/mnt/c/Users/<username>/Projects" /home/<username>/projects

如果你想取消这个软链接，请使用 ``rm linked_dir`` 而不要用 ``rm linked_dir/`` ，
后者会删除目录本身而非软链接。

.. warn::
    再一次提醒，千万别弄反，因为仅仅是在 Windows 中打开 WSL 文件都有可能最终
    导致 WSL 文件系统损坏。 
