---
description: Explanation of pyblitzdg classes and their member functions and properties
---

# Python 3 API - v1.0

### **MeshManager** **Class Reference**

The MeshManager class is primarily used for constructing unstructured numerical meshes in pyblitzdg, either from known supported mesh file formats \(e.g., Gmsh .msh files\), or from numpy arrays containing vertices and connectivity information.

Member functions reference:

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left">__init__(<em>self</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">Constructor</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Arguments</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"> <b>Method</b>
      </td>
      <td style="text-align:left">readMesh (<em>self, path</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">
        <p>Reads the Gmsh at <em>path</em>, provided as a string and store its</p>
        <p>data on the MeshManager object itself.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Arguments</b>
      </td>
      <td style="text-align:left"><b>[in]</b>  <em>path</em> - string containing the &apos;path/to/meshFile.msh&apos;</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left">buildMesh(<em>self</em>, <em>elements</em>, <em>vertices</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">Builds a mesh from known <em>numpy.ndarray</em> objects <em>elements</em> and <em>vertices</em>.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Arguments</b>
      </td>
      <td style="text-align:left">
        <p><b>[in]</b>  <em>elements</em> - 2D numpy array of elements pointing to row-indices
          in the <em>vertices</em> array with shape (K, Vk) where K is the number of
          elements in the mesh and Vk is the number of vertices per element (e.g.,
          Vk=3 for triangles).</p>
        <p></p>
        <p><b>[in]</b>  <em>vertices</em> - 2D numpy array with each row containing
          the (x, y, z) coordinates of a vertex in the mesh. For 2D meshes, take
          z=0.0 for all rows. The shape of this array is (Nv, 3) where Nv is the
          number of vertices in the unstructured mesh and 3 is the (fixed) dimensionality
          of the Cartesian coordinate system.</p>
      </td>
    </tr>
  </tbody>
</table>Properties reference:

|  |  |
| :--- | :--- |
| **Property** | numElements |
| **Description** | The __number of elements in the mesh. |
|  |  |

### TriangleNodesProvisioner Class Reference

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left">__init__(self, <em>N</em>, <em>meshManager</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">Constructor - Takes as arguments the order N of the underlying interpolating
        polynomials to use, and a MeshManager object that is expected to already
        contain the mesh in its state.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Arguments</b>
      </td>
      <td style="text-align:left">
        <p><b>[in]</b>  <em>N</em> - The order of the basis polynomials used in the
          local Galerkin expansion.</p>
        <p><b>[in]</b>  <em>meshManager</em> - An instance of the MeshManager class.
          It is assumed that either .<em>readMesh(...) or .buildMesh(...) </em>has
          already been called on this MeshManager object</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left">dgContext(<em>self</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">Returns the triangular element nodal discontinuous Galerkin (DG) context
        that was created during construction of this instance of the TriangleNodesProvisioner
        class.</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Arguments</b>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Method</b>
      </td>
      <td style="text-align:left">buildFilter(<em>self</em>, <em>Nc</em>, <em>Nf</em>)</td>
    </tr>
    <tr>
      <td style="text-align:left"><b>Description</b>
      </td>
      <td style="text-align:left">Builds a local exponential cut-off filter in the space of the basis polynomial
        coefficients. Here, is the polynomial cut-off order, above which the filter
        is active, and below which the filter is identically equal to the identity
        map (inactive), and is a shape parameter that specifies the order of the
        exponential transfer function,</td>
    </tr>
  </tbody>
</table>

|  |  |
| :--- | :--- |
|  |  |

