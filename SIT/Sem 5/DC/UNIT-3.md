# ZIP VS GZIP


| Aspect                | ZIP                                                                            | GZIP                                                                 |
| --------------------- | ------------------------------------------------------------------------------ | -------------------------------------------------------------------- |
| Full Form             | Zone Information Protocol                                                      | GNU ZIP                                                              |
| Primary Purpose       | File archiving + compression <br>(multiple files and folders in one container) | File/stream compression only (single file at a time)                 |
| Extension             | `.zip`                                                                         | `.gz, tar.gz`                                                        |
| Compression Algorithm | Mostly Deflate (LZ77 + Huffman)                                                | Always Deflate (LZ77 + Huffman)                                      |
| Multi-file Support    | Yes                                                                            | No (tar is used over gzipped file)                                   |
| Structure             | Local file headers + compressed data + central directory (index of files)      | Header (metadata) + compressed block + trailer (CRC + original size) |
| Metadata              | Stores filename, timestamps, permissions, directory hierarchy                  | Stores filename, timestamp, compression method, checksum             |
| Encryption Support    | Yes                                                                            | No                                                                   |
| Compression Ratio     | Moderate to good                                                               | Slightly better for large files                                      |
| Platforms             | Cross-Platform                                                                 | Pre-Dominantly Linux, used in web servers and networking             |
| Error Checking        | Optional per file<br>CRC-32                                                    | Always checksum is done<br>CRC-                                      |

# JBIG


| Aspect                | Details                                                                |
| --------------------- | ---------------------------------------------------------------------- |
| Full-Form             | Joint Bi-level Image Experts Group                                     |
| Compression Algorithm | Context based arithmetic encoding                                      |
| Lossless              | yes                                                                    |
| Image Type            | Bi-level (black and white)                                             |
| Key Idea              | Predict the value of next pixel using the values of surrounding pixels |
| Compression Ratio     | Very high for texts, faxes                                             |
| Progressive           | Image appears gradually as more data arrives                           |
| Limitation            | Works for only bi-level images (no grayscale)                          |
| Application           | Fax transmission, Scanned Documents storage                            |
| Data structure        | Header + Arithmetic Coded Data + Optional Templates                    |
|                       |                                                                        |
# GIF


| Aspect               | Details                                                         |
| -------------------- | --------------------------------------------------------------- |
| Full-Form            | Graphics Interchange Format                                     |
| Compression Algorith | ZW (Lempel–Ziv–Welch) – dictionary-based, lossless              |
| Color Model          | Color-Lookup-Table (Indexed Color)                              |
| Color Depth          | 256 colors / frame (8 bits)                                     |
| Transparency         | Yes (1 bit)                                                     |
| Progressive          | Yes                                                             |
| Animated             | Yes (multi-frame-images, support by frame delay and loop count) |
| Compression Ratio    | High: Flat colored images<br>Low: Phtotographic images          |
| Compression Size     | Smaller for flat images<br>larger for jpeg or webp              |
| Applications         | Simple animations, logos                                        |

### Advantages :
- Wide support across platforms
- Animation Capability
- Transparency support
- Lossless compression for pixel data

### Disadvantages:
- Not suitable for higher resolution pictures or large modern animations
- limited to 256 colors -> bad for high-res images
- no full alpha transparency

### Header 
The Header is six bytes in size and is used only to identify the file as type GIF. 

### Trailer
The Trailer is a single byte of data that occurs as the last character in the file. This byte value is always 3Bh and indicates the end of the GIF data stream. A trailer must appear in every GIF file.

# BZIP2 vs UNIX Compress


| Aspect                | BZIP2                                                                                               | UNIX Compress                                       |
| --------------------- | --------------------------------------------------------------------------------------------------- | --------------------------------------------------- |
| File Extension        | `.bz2`                                                                                              | `.Z`                                                |
| Compression Algorithm | Burrows–Wheeler Transform (BWT) + Move- to-Front (MTF) + Run-Length Encoding (RLE) + Huffman coding | LZW (Lempel–Ziv–Welch) dictionary-based compression |
| Multi-file Support    | No (use over tar)                                                                                   | No (use over tar)                                   |
| Error Checking        | CRC-32 per Block                                                                                    | No strong Error Checking                            |
| Metadata              | Block Size, CRC check, compression setting                                                          | file name, size                                     |
| Encryption Support    | No                                                                                                  | No                                                  |
| Compression Ratio     | Very High                                                                                           | Moderate, worse than modern methods                 |
| Compression Speed     | Slower than ZIP/GZIP                                                                                | Fast, but inefficient                               |
| Applications          | Used in Linux distributions, software packages, archival storage                                    | Historical Unix file compression, rarely used today |

