
# Huffman Coding :

Replacing characters with bit such that most common ones use fewer bits and rare ones use more

### Importance:
- Saves storage space. 
-  Speeds up data transfer (less data to send). 
- Forms the basis of many compression formats like ZIP, PNG, JPEG
- Is optimal among all prefix-free coding methods

### Applications: 
- File compression: ZIP, GZIP, TAR. 
- Image compression: PNG uses Huffman coding. 
- Multimedia compression: JPEG, MP3. 
- Network transmission: Compress messages before sending. 
- Text compression: Reducing storage of large text files

### Key Features: 
- Variable-length codes (unlike fixed 8-bit ASCII)
- Prefix-free property: No code is the prefix of another code. 
- Optimality: Produces the minimum possible average code length for given symbol frequencies.

### Algorithm Steps:
 1. Count frequency of each symbol
 2. Create leaf node for each symbol with it's frequency
 3. Build a priority queue, sorted by frequency
 4. Combine least two values such that `least_val_1 + least_val_2 = new_node `
 5. Repeat steps 2 and 3 until only one root node remains 
 6. Assign codes : `left branch = 0, right branch =1`
 7. Encode data using new codes for each symbol



## Mathematical Derivation

$$
\text{Average Code length: L = }\sum_{{i=1}}^n  p_{i} \times l_{i}
$$
**Goal**: Minimize L subject to the Kraft–McMillan inequality: 
$$
\sum_{i=1}^n 2^{-l_{i}} \leq 1
$$

$Index$
$Symbols : s_{1},s_{2}....s_{n}$
$Probabilities : p_{1},p_{2}....p_{n}$ 
$Code lengths : l_{1},l_{2}....l_{n}$




---

# Run Length Encoding

lossless data compression technique that stores sequences of the same data value (called "runs") as a single value and count instead of repeating the value multiple times.

Example: Instead of storing `ABABABAB`, we compress it down to `AB4 ("AB" repeated 4 times)`

**Effective When:** 
- Data has lots of repeating values
- **Example:** Simple graphics, monochrome images, text with repeated characters, fax machine data, bitmap images with large uniform areas

**Ineffective When:** 
- Data has little or no repetitions (can make file larger)
- **Example:** Encrypted Data ->  `0101011001... (each bit is dependent and has 50% chance of being either 0 or 1)`

### Advantages and Disadvantages

|            **Advantages**            |                   **Disadvantages**                    |
| :----------------------------------: | :----------------------------------------------------: |
| Both encoding and decoding are easy  |  Inefficient for high entropy data (less repetitions)  |
|    No data loss after compression    |       May increase file size, depending on data        |
| Works well on data with many repeats | Not suitable for complex images (high color variation) |

### Applications: 
- TIFF, PCX image formats
- PDF compression
- Simple game textures

### Algorithm Steps:
1. Identify runs
2. Store as `(symbol, count)` pairs
3. Represent in compressed form


> [!NOTE] Note
> if $\text{ avg run length} > 2, \text{RLE saves space}$
>if $\text{ avg run length} = 2, \text{Neither helps nor hurts}$
>if  $\text{ avg run length} < 2, \text{RLE expands data}$


## Example

### #Question Encode `AAAABBAABBBB` with RLE

Solution: `(A,4),(B,2),(A,2), (B,4)`

Original data size : $12 \times 1 = 12 bits$

Compressed data : $4 \times 2 = 8 bits$

> [!NOTE]
> Assuming 1 bit for symbol and 1 bit for count
> $\text{number of runs} \times (\text{size of symbol} + \text{size of count})$

Compression Ratio : $\frac{{8}}{12} \implies 34\%$



# Comparison Between Simple Lossless and RLE


| **Aspect**          | ***Simple Lossless Encoding**                                               | **Run-Length Encoding**                                              |
| ------------------- | --------------------------------------------------------------------------- | -------------------------------------------------------------------- |
| **Definition**      | Compression + reconstruction of original data<br>(no data loss)             | Compresses data by storing `(symbol, it's frequency)` as "runs"      |
| **Principle**       | Statical Models or Dictionaries to store frequent strings with shorter code | Stores consecutive identical symbols in `(symbol, run-length)` pairs |
| **Best-used**       | When certain symbols occur more frequently                                  | When data has long runs of identical symbols                         |
| **Limitations**     | Unexploitable redundancy when symbol probabilities are same                 | Inefficient if run length is short, may even increase size           |
| **Time Complexity** | Huffman coding : $O(nlog2(n))$                                              | $O(n)$                                                               |
| **Applications**    | zip files, png, text compression                                            | bitmap images (with uniform color areas), monochrome faxes           |
| Lossless property   | Always lossless                                                             | Always lossless                                                      |

---

# Arithmetic Encoding:

**Arithmetic coding** is a form of **entropy encoding** used for **lossless data compression**. It represents an entire message as a single fractional number, typically between 0 and 1. This number is determined by the probabilities of the symbols in the message.

### Applications

Arithmetic coding is particularly effective for compressing data where the symbol probabilities are not uniform. It's used in various compression standards, including:

- **JPEG 2000** for image compression.
- **H.264/MPEG-4 AVC** for video compression.
- **The Opus codec** for audio compression.
- **Fax machines** and other document compression systems.

### Key Features:

- **High Compression Efficiency**: It often achieves compression ratios that are very close to the theoretical limit defined by the **Shannon entropy** of the data. This is because it can assign non-integer bit lengths to symbols, unlike Huffman coding which is restricted to integer bit lengths.

- **Adaptability**: It can use an **adaptive model**, meaning it can learn and update the probabilities of symbols as it processes the data.

- **Context-Dependent Coding**: It can easily incorporate **contextual information**. For example, the probability of a symbol can depend on the symbols that came before it, allowing for better compression.

## Mathematical Derivation:

$$
l^n = l^{n-1} + ( u^{n -1 } - l^{n-1})F_{x}(x_{n} - 1)
$$
$$
u^n = l^{n-1} + ( u^{n -1 } - l^{n-1})F_{x}(x_{n})
$$

Usually, by default,

$$
l_{0} = 0
$$
$$
u_{0} = 1
$$

$$
Symbols: s_{1}, s_{2}...s_{n}
$$
$$
Probabilities: p_{1}, p_{2}\dots p_{3}
$$

$$
F_{1}(p_{1}), F_{2}(p_{1} + p_{2}), F_{n}(p_{1} + p_{2} + \dots p_{n})
$$

### #Question $S = (1,2,3)$ , $P = (0.5,0.3,0.2)$, $w='1332'$ 

Solution: 
$$
\begin{equation}
\begin{gathered}
l_{0} = 0 \\
u_{0} = 0 \\

F_0 = p_{1} = 0.5 \\
F_{1} = p_{1} + p_{2} \implies 0.5 + 0.3 = 8 \\
F_{2} = p_{1} + p_{2} + p_{3} \implies 0.5 + 0.2 + 0.3 = 1.0 \\
\\
\text{By calculations using the above formula: } \\
l_{1}
 = 0 , u_{1} = 0.5
\end{gathered}
\end{equation}
$$

