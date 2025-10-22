
# 🖼️ Content-Aware Image Resizing (Seam Carving)

A **C# implementation** of the **Content-Aware Image Resizing** (also known as **Seam Carving**) algorithm.  
This technique intelligently resizes images by removing low-importance pixels (seams) based on their energy values — preserving key visual content while reducing dimensions.

---

## 📌 Overview

Traditional image resizing methods (like scaling or cropping) often distort or cut out important parts of an image.  
This project uses **seam carving** — an adaptive algorithm that removes the least important pixels along a calculated "seam" to reduce width while keeping essential content intact.

---

## 🧠 Core Algorithm

### 1. **Energy Map Calculation**
Each pixel’s **energy** is computed using gradient magnitude, indicating its importance.  
High-energy pixels correspond to edges and details that should be preserved.

### 2. **Dynamic Programming for Seam Selection**
The algorithm:
- Builds a cost matrix (`dp`) storing the minimum cumulative energy from top to bottom.
- Selects the **lowest-energy vertical seam** using backtracking.
- Removes the identified seam.

This process repeats for each seam to be removed.

---

## 🧩 Main Functionality

### **Class:** `ContentAwareResize`
| Method | Description |
|---------|-------------|
| `CalculateSeamsCost()` | Computes the minimum vertical seam and its energy using dynamic programming. |
| `CalculateVerIndexMap()` | Marks and removes the lowest-energy seams from the energy matrix. |
| `RemoveColumns()` | Removes the specified number of seams from the image. |
| `ContentAwareResize(string ImagePath)` | Initializes the class by loading the image and computing its energy map. |

### **Struct:** `coord`
Stores the (row, column) positions of pixels in a seam.

---

## ⚙️ Technologies Used
- **Language:** C#
- **Framework:** .NET
- **Concepts:**
  - Dynamic Programming
  - Image Processing
  - Gradient Energy Maps
  - Seam Path Tracking

---

## 🚀 How to Run

### **1. Prerequisites**
- .NET SDK installed ([Download here](https://dotnet.microsoft.com/download))
- Visual Studio or VS Code with C# extensions

### **2. Clone the Repository**
```bash
git clone https://github.com/Belal6205/ContentAwareResize.git
cd ContentAwareResize
````

### **3. Build & Run**

* Open the project in Visual Studio
* Add an image path in the constructor:

  ```csharp
  ContentAwareResize resize = new ContentAwareResize("path_to_image.jpg");
  ```
* Call:

  ```csharp
  resize.RemoveColumns(50);
  ```

---

## 📊 Example Workflow

```csharp
int minSeamValue = 0;
List<ContentAwareResize.coord> seamPathCoord = new List<ContentAwareResize.coord>();

ContentAwareResize resize = new ContentAwareResize("sample.jpg");
resize.CalculateSeamsCost(resize._energyMatrix, 400, 300, ref minSeamValue, ref seamPathCoord);

Console.WriteLine("Minimum Seam Energy: " + minSeamValue);
```

**Output:**

```
Minimum Seam Energy: 12530
Vertical Seam: [(299, 152), (298, 151), (297, 150), ...]
```

---

## 📁 Project Structure

```
ContentAwareResize/
│
├── ContentAwareResizee.cs   # Main algorithm implementation
├── ImageOperations.cs       # Helper functions for energy calculation (not shown)
├── Program.cs               # Entry point (if applicable)
└── README.md                # Project documentation
```

---

## 🔮 Future Improvements

* Add **horizontal seam removal**.
* Implement **multi-directional resizing** (both width and height).
* Build a **GUI interface** for visualization.
* Support **energy reweighting** to protect or remove specific regions.

---

## 👨‍💻 Author

**Belal Mohamed Fathy Sayed Nasr**

* GitHub: [Belal6205](https://github.com/Belal6205)
* Role: Computer Science Student
