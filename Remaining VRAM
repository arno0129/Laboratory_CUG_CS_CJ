# Procedure: Check GPU Memory Before Using the Server

Before running deep learning tasks on the server, it is important to check the available GPU memory to ensure sufficient resources. Follow the steps below:

## 1. Log in to the server

```bash
ssh username@server_ip
```

## 2. Check GPU status

Use the `nvidia-smi` command:

```bash
nvidia-smi
```

### Example output

```
+-----------------------------------------------------------------------------------------+
| NVIDIA-SMI 580.82.07              Driver Version: 580.82.07      CUDA Version: 13.0     |
+-----------------------------------------+------------------------+----------------------+
| GPU  Name                 Persistence-M | Bus-Id          Disp.A | Volatile Uncorr. ECC |
| Fan  Temp   Perf          Pwr:Usage/Cap |           Memory-Usage | GPU-Util  Compute M. |
|                                         |                        |               MIG M. |
|=========================================+========================+======================|
|   0  NVIDIA GeForce RTX 4090 D      Off |   00000000:2A:00.0 Off |                  Off |
| 30%   32C    P8             18W /  425W |   15MiB / 49140MiB |      0%      Default |
+-----------------------------------------------------------------------------------------+
```

## 3. Key fields to check

* **Memory-Usage**: used memory / total memory

  * Example: `15MiB / 49140MiB` means only 15MB is in use, almost all memory is available.
* **GPU-Util**: GPU utilization rate

  * Example: `0%` means the GPU is idle.

## 4. Decide if you can use the GPU

* If **available memory** > memory required for your task, you can safely run it.
* If GPU memory usage is already high, contact the responsible user or switch to another GPU.

## 5. Useful commands

* **Monitor GPU status in real time**

  ```bash
  watch -n 1 nvidia-smi
  ```
* **Check processes using the GPU**

  ```bash
  nvidia-smi pmon -c 1
  ```

---
