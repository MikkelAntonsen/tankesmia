
https://pytorch.org/audio/main/tutorials/nvdec_tutorial.html

https://pytorch.org/audio/main/build.ffmpeg.html#enabling-hw-decoder

Got to a point where I couldn't install nvcc which is needed for FFmpeg-n4.4.2 which is needed for 

```
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libcuinj64-11.5 : Depends: libnvidia-compute-495 (>= 495) but it is not going to be installed or
                            libnvidia-compute-495-server (>= 495) but it is not installable or
                            libcuda.so.1 (>= 495) or
                            libcuda-11.5-1
 libnvidia-ml-dev : Depends: libnvidia-compute-495 (>= 495) but it is not going to be installed or
                             libnvidia-compute-495-server (>= 495) but it is not installable or
                             libnvidia-ml.so.1 (>= 495)
 nvidia-cuda-dev : Depends: libnvidia-compute-495 (>= 495) but it is not going to be installed or
                            libnvidia-compute-495-server (>= 495) but it is not installable or
                            libcuda.so.1 (>= 495) or
                            libcuda-11.5-1
                   Recommends: libnvcuvid1 but it is not installable

```


Ended up using the following configure because 1) string interpolation for ccap didn't work as excepted in fish 2) nvenc is fucked for some reason.

Had to fuck around and add cuda/bin to LD_LIBRARY_PATH and PATH to get ./configure command to recognize nvcc, but in the end it it could have been the ccap string interpolation that was the problem, as the check for nvcc does a small compile

```
./configure \                                                                                                                                                                                                                               (base) 
                                             --prefix="$prefix" \
                                             --extra-cflags='-I/usr/local/cuda/include' \
                                             --extra-ldflags='-L/usr/local/cuda/lib64' \
                                             --nvccflags="-gencode arch=compute_86,code=sm_86 -O2" \
                                             --disable-doc \
                                             --enable-decoder=aac \
                                             --enable-decoder=h264 \
                                             --enable-decoder=h264_cuvid \
                                             --enable-decoder=rawvideo \
                                             --enable-indev=lavfi \
                                             --enable-encoder=libx264 \
                                             --enable-encoder=h264_nvenc \
                                             --enable-demuxer=mov \
                                             --enable-muxer=mp4 \
                                             --enable-filter=scale \
                                             --enable-filter=testsrc2 \
                                             --enable-protocol=file \
                                             --enable-protocol=https \
                                             --enable-gnutls \
                                             --enable-shared \
                                             --enable-gpl \
                                             --enable-nonfree \
                                             --enable-cuda-nvcc \
                                             --enable-libx264 \
                                             --enable-cuvid \
                                             --enable-nvdec

```



Success! Next up, how do this in pants?