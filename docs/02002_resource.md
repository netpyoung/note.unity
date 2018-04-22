resource
===========

# sound
## bgm :
* bgm_*.mp3
* Load Type : Compressed In Memory
* Preload Audio Data : false
* Compression Format : Vorbis / mp3
* Quality : 100
* Sample Rate Setting : Preserve Sample Rate

## effect :
* se_*.wave
* Load Type : Decompress On Load
* Preload Audio Data : false
* Compression Format : PCM
* Quality : 100
* Sample Rate Setting : Preserve Sample Rate


# Texture
* if need to compression : https://developers.google.com/speed/webp/docs/using
* sega tech : http://techblog.sega.jp/entry/2017/02/27/100000



## import setting
* ProjectSettings -> Graphic -> Always Included Shader  :  UI/DefaultETC1

### Android
* Texture Type : Sprite (2D and UI)
* Non Power of 2 : ToNearest
* Pixels Per Unit : 100 // default
* Filter Mode : Bilinear
* Max Size : 2048
* Resize Algorithm : Mitchell
* Compression : Normal Quality


* Max Size : 2048
* format : RGB Compressed ETC 4 bits
* Compressor Quality : Normal
* Compress using ETC1(split alpha channel) : True (if alpha)


### iOS
* http://www.webtech.co.jp/clearpvrtc/
* Texture Type : Sprite (2D and UI)
* Non Power of 2 : ToNearest

* Max Size : 2048
* format : RGB Compressed PVRTC 4 bits | RGBA Compressed PVRTC 4 bits (if alpha)
* Compressor Quality : Normal

## https://docs.unity3d.com/2017.1/Documentation/Manual/SpriteAtlas.html