# Procedure: Check GPU Memory Before Using the Server

Before running deep learning tasks on the server, it is important to check the available GPU memory to ensure sufficient resources. Follow the steps below:

## 1. Check GPU status

Use the `nvidia-smi` command:

```bash
nvidia-smi
```

### Example output

```
Wed Sep 24 09:56:00 2025       
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 570.153.02             Driver Version: 570.153.02     CUDA Version: 12.8     |
|-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 4090        Off |   00000000:D8:00.0 Off |                  Off |
| 31%   35C    P8             24W /  450W |      69MiB /  24564MiB |      0%      Default |
|                                         |                        |                  N/A |
+-----------------------------------------+------------------------+----------------------+
                                                                                         
+-----------------------------------------------------------------------------------------+
| Processes:                                                                              |
|  GPU   GI   CI              PID   Type   Process name                        GPU Memory |
|        ID   ID                                                               Usage      |
|=========================================================================================|
|    0   N/A  N/A           34698      G   /usr/lib/xorg/Xorg                       58MiB |
+-----------------------------------------------------------------------------------------+
```

## 2. Key fields to check

* **Memory-Usage**: used memory / total memory

  * Example: `69MiB /  24564MiB` means only 69MB is in use, almost all memory is available.
* **GPU-Util**: GPU utilization rate

  * Example: `0%` means the GPU is idle.

## 3. Decide if you can use the GPU

* If **available memory** > memory required for your task, you can safely run it.
* If GPU memory usage is already high, contact the responsible user or switch to another GPU.

## 4. Useful commands

* **Monitor GPU status in real time**

  ```bash
  watch -n 1 nvidia-smi
  ```
* **Check processes using the GPU**

  ```bash
  nvidia-smi pmon -c 1
  ```

---
