
<h1>Compressing Files </h1>

* **Compression** makes files smaller; **decompression** restores them.
* Compressed files must be **decompressed** to use.
* **Re-compressing** compressed files doesn’t reduce size further.


* **Two compression types:**

    * **Lossless:** no data loss (text, logs).
    * **Lossy:** Small data loss (used in images/audio to reduce size).


<h2>Common Linux Compression Tools</h2>

* **gzip / gunzip** → uses Lempel-Ziv algorithm (`.gz`)
* **bzip2 / bunzip2** → uses Burrows-Wheeler algorithm (`.bz2`), smaller files but slower
* **xz / unxz** → uses LZMA (`.xz`), best compression with good speed
 
 Example

```bash
gzip longfile.txt        # Compress → creates longfile.txt.gz
gunzip longfile.txt.gz   # Decompress → restores original file
gzip -l longfile.txt.gz  # gzip Size Check

# Compression formats:
# gzip  → .gz
# bzip2 → .bz2
# xz    → .xz
```




![alt text](image/compressing.png)
