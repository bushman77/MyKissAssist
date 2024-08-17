# MyKissAssist
# build/install wine-proton from https://github.com/ValveSoftware/Proton however your distro does this :P

export WINEPREFIX=~/.wine-eq
export WINEARCH=win64
winecfg # just to generate the directories, then exit
winetricks corefonts dxvk # Launcher & eqgame.exe work out-of-the-box
winetricks settings # you're looking for videomemorysize=2048

# at this point you can choose to "wine regedit" and navigate to the Direct3D key and adjust the video memory size but I doubt it has any real impact, this is just my OCD

cd ~/.wine-eq/drive_c/EverQuest # your install dir may vary
wine LaunchPad.exe # load, login, set window size, etc then exit

# I've noticed that adjusting the game settings from the Launcher doesn't stick. Meaning my eqclient.ini can be manually changed and if I open the Launcher Game Settings it will overwrite. So we'll manually update
nano eqclient.ini

MipMapping=FALSE # unnecessary with modern gear
LoadSocialAnimations=FALSE # personal pref, I'm cooking a laptop so I take cuts where I can get them
UseD3DTextureCompression=FALSE # DX11 changes depreciated this client feature
TextureCache=FALSE # DX11 changes depreciated this client feature

## hot topic is VertexShaders TRUE|FALSE, I'm not exactly sure. I have it as TRUE so I'm open to debate on this with the DX11/64bit client
## if I don't have Allow Pixel Shaders 2.0 enable in game, it's a slideshow in PoK or Kunark tree graphics
## some models (Coldain/Lizardman to name two) are just blank/white and overly bright asf

12th Gen Intel i7-1280P (20) @ 4.700GHz
AMD ATI Radeon RX 6950 XT
64Gb RAM DDR4 @ 3200
