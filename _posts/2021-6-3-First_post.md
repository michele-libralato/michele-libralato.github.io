---
layout: post
title: WUFIplus batch mode
category: OT
tags: WUFI, HMT, BES
---

For some reason WUFIplus manual instructions to activete batch mode don't work on every system. With this workaround it worked:

1. Add WUFIplus path to environment variables (path)
2. Open the project folder in a cmd prompt
3. Enter 'wufiplus "C" "R" "filename1.mwp" "filename2.mwp"' where filename1.mwp and filename2.mwp are the previously prepared project files. More files could be added after these two.

I suggest adding WUFIplus path to Windows environment variables instead of using WUFIplus full path because it may not work on all systems.
