# Lecture 3 Timing Plan: Array & Tensor Operations
**Total Duration: 50 minutes**

---

## 📋 Overview
This timing plan covers the essential content from `Lecture_3_Array_and_Tensor_Operations.ipynb` with buffer time for questions and demos.

---

## ⏱️ Detailed Timeline

### **0-3 min: Introduction & Setup** ✅
- **Content**: Title slide, learning objectives
- **Demo**: Verify PyTorch installation (cell with version checks)
- **Key point**: Show device detection (CPU/CUDA/MPS)
- **Transition**: "Before we dive in, let's understand what we're working with..."

---

### **3-8 min: Tensor Terminology & Motivation** (5 min)
- **Content**: 
  - Show tensor terminology diagram (vector/matrix/tensor)
  - Explain naming conventions (NumPy arrays vs PyTorch tensors)
- **Demo**: 
  - Quick example with Python nested lists (cell showing vector/matrix/tensor examples)
  - Show the error when trying `matrix_example[0, 1, 1]`
- **Key point**: "This is why we need NumPy and PyTorch!"

---

### **8-13 min: Why Not Python Lists?** ⚡ (5 min)
- **Content**: Performance comparison
- **Demo**: 
  - Run the 1 million element squaring benchmark
  - Emphasize 20-100x speedup
- **Key talking points**:
  - Vectorization/parallelism
  - GPU acceleration preview
- **Engagement**: Ask "Who wants to wait 100x longer for results?"

---

### **13-15 min: NumPy vs PyTorch Comparison** (2 min)
- **Content**: Show comparison table quickly
- **Key point**: "NumPy for general computing, PyTorch for deep learning"
- **Don't read the table**: Just highlight 3-4 key differences
  - NumPy = CPU, PyTorch = GPU
  - PyTorch has autograd
  - Very similar syntax

---

### **15-25 min: Section 1 - Creating Arrays & Tensors** 📊 (10 min)

#### **15-17 min: From Python Lists + Shapes** (2 min)
- **Demo**: Create from lists (`np.array()`, `torch.tensor()`)
- **Content**: Quick explanation of `.shape`, `.size`, `.numel()`
- **Key point**: "Always check your shapes!"

#### **17-19 min: Zeros, Ones, Ranges** (2 min)
- **Demo**: Show `np.zeros()`, `np.ones()`, `np.arange()`
- **Side-by-side**: NumPy and PyTorch syntax
- **Key point**: "Nearly identical APIs"

#### **19-21 min: Linspace & Empty** (2 min)
- **Demo**: `np.linspace(0, 1, 5)` - explain evenly spaced
- **Demo**: `np.empty()` - show uninitialized values, explain performance use case
- **Warning**: "Don't expect zeros from empty()!"

#### **21-23 min: Data Types Overview** (2 min)
- **Content**: Show dtype table quickly (don't go deep)
- **Key points**: 
  - Memory size matters (float32 vs float64)
  - NumPy defaults to float64, PyTorch to float32
- **Demo**: Quick type conversion example (`.astype()`, `.float()`)
- **Note**: "Full dtype details are in the notebook for self-study"

#### **23-25 min: Type Conversion** (2 min)
- **Demo**: Show conversion methods
  - NumPy: `.astype(np.float32)`
  - PyTorch: `.float()`, `.double()`, `.half()`
- **Skip**: NumPy ⟷ PyTorch conversion (marked for self-study)

---

### **25-30 min: Section 2 - Reshaping** 🔄 (5 min)
- **Demo**: 
  - `np.arange(12).reshape(3, 4)`
  - Show the `-1` trick for inferring dimensions
- **Real example**: Image flattening demo
  - Show `(100, 256, 256)` → `(100, 65536)`
  - "This is how you prep images for ML models"
- **Practice moment**: Ask class what shape `(24,)` becomes when reshaped to `(4, -1)`

---

### **30-36 min: Section 3 - Indexing & Slicing** 🎯 (6 min)

#### **30-33 min: Basic Indexing** (3 min)
- **Demo**: Show 1D and 2D indexing examples
  - `arr[5]`, `arr[3:7]`, `arr[::2]`
  - `arr[2:5, 1:4]` for 2D
- **Key point**: "Works exactly like Python lists, but multi-dimensional!"
- **Interactive**: "What does `arr[::-1]` do?"

#### **33-36 min: Fancy Indexing** (3 min)
- **Demo**: Integer array indexing `arr[[2, 7, 9]]`
- **Demo**: Boolean masking `arr[arr > 5]`
- **Wow moment**: Modify with boolean mask `arr[arr < 3] = 100`
- **Key point**: "This is incredibly powerful for data filtering!"

---

### **36-38 min: Section 5 - Special Matrices** 🎲 (2 min)
- **Demo**: Quick tour
  - Identity: `np.eye(5)`
  - Diagonal: `np.diag([1, 2, 3])`
  - Random: `np.random.randn(2, 2)` and seed setting
- **Note**: "Broadcasting section is in the notebook for self-study"
- **Speed through**: Don't run all examples, just show 2-3

---

### **38-42 min: Section 6 - Matrix Operations** 🔢 (4 min)
- **Demo**:
  - Transpose: `arr.T`
  - Matrix multiplication: `A @ B` (emphasize the `@` operator)
  - Element-wise: `A * B`
- **Key point**: "@ for matrix multiply, * for element-wise"
- **Quick mention**: `np.linalg` for advanced operations (inv, det, eig)

---

### **42-45 min: Section 7 - Reduction Operations** 📉 (3 min)
- **Demo**:
  - `arr.sum()`, `arr.mean()`, `arr.min()`, `arr.max()`
  - **Critical**: Show axis/dim parameter
    - `arr.sum(axis=0)` vs `arr.sum(axis=1)`
- **Visual**: Use the `(10, 5)` array example to show row vs column reduction
- **Key point**: "axis=0 collapses rows, axis=1 collapses columns"

---

### **45-48 min: Section 9 - GPU Acceleration** 🚀 (3 min)
- **Content**: Why PyTorch matters
- **Demo** (if GPU available):
  - Check `torch.cuda.is_available()`
  - Show `.to('cuda')` or `.to('mps')`
  - Explain device concept
- **Key point**: "This is where PyTorch shines - 1000x+ speedup possible!"
- **Note**: "NumPy stays on CPU"

---

### **48-50 min: Summary & Final Performance Demo** 🎬 (2 min)
- **Quick recap**:
  - NumPy for scientific computing (CPU)
  - PyTorch for ML/DL (GPU + autograd)
  - Nearly identical syntax
  - 10-1000x faster than Python lists
- **Optional**: Run final big performance comparison if time allows
- **Closing**: Point to notebook sections marked "read after lecture"
  - Broadcasting
  - Full dtype details
  - NumPy ⟷ PyTorch conversion with memory sharing

---

## 📝 Content to SKIP (Self-Study)
✂️ These sections are marked "Please read after the lecture":
1. **Full data types section** (just show summary table)
2. **NumPy ⟷ PyTorch conversion details** (memory sharing)
3. **Broadcasting** (entire section 4)
4. **Element-wise operations section 8** (redundant with earlier content)
5. **Additional math operations** (students can explore)
6. **Final performance comparison** (if time is short)

---

## 🎯 Key Teaching Tips

### **Pacing Strategies**
- ⏩ **Speed up**: Comparison tables, dtype details
- ⏸️ **Slow down**: Indexing/slicing, reshaping with -1, axis/dim in reductions
- 💬 **Interactive moments**: 
  - "What shape will this become?"
  - "Who can guess what this does?"
  - "Why would we use empty() instead of zeros()?"

### **Demo Execution Tips**
1. **Run cells in advance** during break to avoid waiting for timeit
2. **Have backup outputs** in case demos fail
3. **Use shorter arrays** for demos (easier to see on screen)
4. **Always show before/after shapes** when reshaping

### **Common Student Questions** (Budget 30 sec each)
- "Why two libraries?" → Different use cases
- "When do I use which?" → NumPy for data science, PyTorch for ML
- "What's the difference between .size and len()?" → size=total, len=first dim
- "Why does PyTorch default to float32?" → GPU efficiency

### **Backup Slides/Content** (If Running Fast)
- More fancy indexing examples
- Live coding: solve a small problem
- Show the image dataset flattening example in detail
- Quick preview of autograd (teaser for next lecture)

### **Time Savers** (If Running Behind)
- Skip linspace (less common)
- Combine zeros/ones/arange into one demo
- Skip empty() entirely
- Reduce special matrices to just identity and random
- Skip GPU section if no GPU available

---

## 🎓 Learning Objectives Checklist

By end of lecture, students should be able to:
- ✅ Create NumPy arrays and PyTorch tensors
- ✅ Understand shape and size operations
- ✅ Reshape arrays with `-1` inference
- ✅ Use basic and fancy indexing
- ✅ Perform matrix operations (`@` vs `*`)
- ✅ Apply reduction operations with axis/dim
- ✅ Explain why NumPy/PyTorch are faster than Python lists

---

## 📊 Time Buffer Analysis

| Segment | Planned | Actual Range | Buffer |
|---------|---------|--------------|--------|
| Intro | 3 min | 2-4 min | ±1 min |
| Motivation | 10 min | 8-12 min | ±2 min |
| Creating arrays | 10 min | 8-13 min | ±3 min |
| Reshaping | 5 min | 4-7 min | ±2 min |
| Indexing | 6 min | 5-8 min | ±2 min |
| Special/Matrix/Reduction | 9 min | 7-12 min | ±3 min |
| GPU & Summary | 5 min | 3-7 min | ±2 min |
| **Questions throughout** | ~2 min | 2-5 min | ±3 min |

**Total buffer: ±5 minutes** (allows flexibility for questions and pacing)

---

## 🔄 Suggested Adjustments

### If Running 5 Minutes Behind:
1. Skip `np.empty()` (1 min)
2. Reduce special matrices to 1 example (1 min)
3. Skip GPU section (2 min)
4. Shorter summary (1 min)

### If Running 5 Minutes Ahead:
1. Add broadcasting quick demo (2 min)
2. Show NumPy↔PyTorch conversion (2 min)
3. Live coding exercise (3 min)
4. Take more questions (flexible)

---

## 📱 Slide/Cell Markers

**Key cells to definitely run live:**
- Cell with version checks (verify setup)
- Performance comparison (1M elements)
- Reshape with -1 (image flattening)
- Boolean indexing modification
- Matrix multiply @ vs *
- Reduction with axis demonstration

**Cells to have pre-run:**
- All `%timeit` cells (show output, don't wait)
- Large performance comparisons
- Final benchmark section

---

**Good luck with your lecture! 🎉**