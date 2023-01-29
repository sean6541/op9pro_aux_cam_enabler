# OnePlus 9 Pro Aux Cameras Enabler

Magisk module that unlocks all cameras for use by third party apps on the OnePlus 9 Pro.

## How It Works

Using a `post-fs-data.sh` script, the module copies the `/odm/etc/camera/CameraHWConfiguration.config` file to it's (the modules) directory and then uses `sed` to replace the line `SystemCamera = 0;  0;  1;  1;  1;  1` with `SystemCamera = 0;  0;  0;  0;  0;  1`. This un-sets all the cameras as system cameras, which means that third party apps can access and use them. It then uses `mount --bind` to bind-mount the edited copy of `CameraHWConfiguration.config` to the original (necessary because Magisk doesn't support overriding files in the `odm` partition) and then `chcon` to set the SELinux context.

**Notice: This module will ONLY work on the OnePlus 9 Pro. It will not work on ANY other device. If you have a OnePlus 9 (non-pro), use this module instead: _link here_**
