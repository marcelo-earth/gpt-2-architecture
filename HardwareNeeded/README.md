# RAM vs VRAM

CPU uses RAM to store temporary data. The minimum amount recomended should be 16GB.

**VRAM (Video Random Access Memory)** is used to store the data that is being processed by the GPU.

**HBM (High Bandwidth Memory)** is used to store the data that is being processed by the GPU. This is the one that is most used on Machine Learning. It's also more expensive than VRAM.

Of course if you need to make the model being executed in a small machine, you can use quantization (reducing the precision of the model). This is something I already tried on low-power devices actually.
