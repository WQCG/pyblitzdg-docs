---
description: Explanation of pyblitzdg classes and their member functions
---

# Python 3 API - v1.0

**MeshManager** Class Reference

The MeshManager class is primarily used for constructing unstructured numerical meshes in pyblitzdg, either from known supported mesh file formats \(e.g., Gmsh .msh files\), or from numpy arrays.

Member function reference:

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
      <td style="text-align:left">[in] <em>path</em> - string containing the &apos;path/to/meshFile.msh&apos;</td>
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
        <p>[in] <em>elements</em> - 2D numpy array of elements pointing to row-indices
          in the <em>vertices</em> array with shape (K, Vk) where K is the number of
          elements in the mesh and Vk is the number of vertices per element (e.g.,
          Vk=3 for triangles).</p>
        <p></p>
        <p>[in] <em>vertices</em> - 2D numpy array with each row containing the (x,
          y, z) coordinates of a vertex in the mesh. For 2D meshes, take z=0.0 for
          all rows. The shape of this array is (Nv, 3) where Nv is the number of
          vertices in the unstructured mesh and 3 is the (fixed) dimensionality of
          the Cartesian coordinate system.</p>
      </td>
    </tr>
  </tbody>
</table>

