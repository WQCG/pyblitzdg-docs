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
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>__init__(</b><em><b>self</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Constructor</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"> <em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>readMesh (</b><em><b>self, path</b></em><b>) </b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">
        <p>Reads the Gmsh *.msh file at <em>path</em>, provided as a string and store
          its</p>
        <p>data on the MeshManager object itself.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left"><b>[in]</b>  <em>path</em> - string containing the &apos;path/to/meshFile.msh&apos;</td>
    </tr>
    <tr>
      <td style="text-align:left"></td>
      <td style="text-align:left"></td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>buildMesh(</b><em><b>self</b></em><b>, </b><em><b>elements</b></em><b>, </b><em><b>vertices</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Builds a mesh from known <em>numpy.ndarray</em> objects <em>elements</em> and <em>vertices</em>.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
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
| _**Property**_ | **numElements** |
| _**Description**_ | The __number of elements in the mesh. |
|  |  |

### TriangleNodesProvisioner Class Reference

The TriangleNodesProvisioner object bridges the gap between the triangular finite element mesh and a complete nodal discretization of the domain of interest. It takes a MeshManager object and a polynomial order $$N = 1,2,\cdots\;$$and provides access to the _DGContext_, an object that encapsulates all the spatial discretization data necessary for carrying out a PDE simulation in the domain of interest.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>__init__(</b><em><b>self</b></em><b>, </b><em><b>N</b></em><b>, </b><em><b>meshManager</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Constructor - Takes as arguments the order N of the underlying interpolating
        polynomials to use, and a MeshManager object that is expected to already
        contain the mesh in its state.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
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
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>dgContext(</b><em><b>self</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Returns the triangular element nodal discontinuous Galerkin (DG) context
        that was created during construction of this instance of the TriangleNodesProvisioner
        class.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>buildFilter(</b><em><b>self</b></em><b>, </b><em><b>Nc</b></em><b>, </b><em><b>Nf</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Builds a local exponential cut-off filter in the space of the basis polynomial
        coefficients. Here, is the polynomial cut-off order, above which the filter
        is active, and below which the filter is identically equal to the identity
        map (inactive), and is a shape parameter that specifies the order of the
        exponential transfer function, .</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">
        <p><b>[in] </b><em>Nc </em>- The cut-off order of the exponential filtering
          function.</p>
        <p><b>[in]</b>  <em>Nf</em> - Shape parameter specifying the order of the exponential
          filtering function.</p>
      </td>
    </tr>
  </tbody>
</table>### QuadNodesProvisioner Class Reference

The QuadNodesProvisioner object bridges the gap between the quadrilateral finite element mesh and a complete nodal discretization of the domain of interest. It takes a MeshManager object and a polynomial order $$N = 1,2,\cdots\;$$and provides access to the _DGContext_, an object that encapsulates all the spatial discretization data necessary for carrying out a PDE simulation in the domain of interest.

<table>
  <thead>
    <tr>
      <th style="text-align:left"></th>
      <th style="text-align:left"></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>__init__(</b><em><b>self</b></em><b>, </b><em><b>N</b></em><b>, </b><em><b>meshManager</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Constructor - Takes as arguments the order N of the underlying interpolating
        polynomials to use, and a MeshManager object that is expected to already
        contain the mesh in its state.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
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
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>dgContext(</b><em><b>self</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Returns the triangular element nodal discontinuous Galerkin (DG) context
        that was created during construction of this instance of the TriangleNodesProvisioner
        class.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>buildFilter(</b><em><b>self</b></em><b>, </b><em><b>Nc</b></em><b>, </b><em><b>Nf</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Builds a local exponential cut-off filter in the space of the basis polynomial
        coefficients. Here, is the polynomial cut-off order, above which the filter
        is active, and below which the filter is identically equal to the identity
        map (inactive), and is a shape parameter that specifies the order of the
        exponential transfer function, .</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">
        <p><b>[in] </b><em>Nc </em>- The cut-off order of the exponential filtering
          function.</p>
        <p><b>[in]</b>  <em>Nf</em> - Shape parameter specifying the order of the exponential
          filtering function.</p>
      </td>
    </tr>
  </tbody>
</table>### VtkOutputter Class Reference

The VtkOutputter class provides an easy-to-use interface for outputting the physical fields value at runtime-determined physical output times. The output is in unstructured \*.vtu file format from the [VTK](https://vtk.org) library, and can be readily rendered, visualized, and animated with [Paraview](https://paraview.org).

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
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>__init__(</b><em><b>self</b></em><b>, </b><em><b>triangleNodesProvisioner</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Constructor. Requires a TriangleNodesProvisioner object.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left"><b>[in]</b>  <em>triangleNodesProvisioner</em> - Instance of the TriangleNodesProvisioner
        class containing the details of the nodal element-wise spatial discretization
        of the domain of interest.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>writeFieldToFile(self</b>, <em><b>fileName, field, fieldName</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Write a single physical field to a vtu file.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">
        <p><b>[in]</b>  <em>fileName </em>- String containing then name of the output
          file, e.g., &quot;u0000010.vtu&quot;.</p>
        <p><b>[in</b>] <em>field<b> - </b></em>numpy.ndarray object containing a physical
          field (i.e., a function of the spatial coordinates).</p>
        <p><b>[in] </b><em>fieldName - </em>String containing the name of the field,
          e.g., &quot;u&quot; or &quot;rho&quot;. Note: Choosing an appropriate fieldName
          makes navigating the Paraview tool easier.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>writeFieldsToFiles(self, </b><em><b>fields</b></em><b>, </b><em><b>tstep</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Write a <em>dict()</em> of physical fields to a set of vtu files. Unlike
        with the &apos;writeFieldToFile&apos; method, filenaming is handled internally
        using the value of <em>tstep</em> and the name of each field as provided
        by the python dictionary.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">
        <p><b>[in]</b>  <em>fields</em> - dictionary whose keys correspond to <em>fieldNames </em>(strings)<em> </em>and
          whose values correspond to numpy.ndarray objects containing the corresponding
          physical field.</p>
        <p><b>[in]</b>  <em>tstep</em> - An integer time-index value, used for numbering
          the vtu files.</p>
      </td>
    </tr>
  </tbody>
</table>### Poisson2DSparseMatrix Class Reference

The Poisson2DSparseMatrix class allows for the construction of the two-dimensional discrete Poisson operator in sparse matrix form. The sparse matrix types are from the popular scipy.sparse Python 3 module.



<table>
  <thead>
    <tr>
      <th style="text-align:left">title</th>
      <th style="text-align:left"><b>title</b>
      </th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>__init__(self, dgContext2D)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Constructor. Requires a DGContext2D object. Currently only support context
        from TriangleNodesProvisioner</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left"><b>[in] </b><em>dgContext2D - </em>DGContext2D object.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>buildBcRhs(self, </b><em><b>dgContext2D, meshManager, ubc, qbc</b></em><b>)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Build boundary conditions contribution to right-hand side of the linear
        system for the Poisson problem. Boundary fields are specified as <em>ubc </em>(Dirichlet)<b> </b>and <em>qbc </em>(Neuman).</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">
        <p><b>[in] </b><em>dgContext2D - </em>DGContext2D object.</p>
        <p><b>[in]</b>  <em>meshManager</em> - The MeshManager object. Possibly containing
          updated information about the types of boundary conditions selected along
          the physical boundary.</p>
        <p><b>[in]</b>  <em>ubc - </em>2D numpy array of dimension (NumFacePoints*NumFaces)
          x NumElements specifying the Dirichlet boundary condition functions along
          the physical boundary.</p>
        <p><b>[in]</b>  <em>qbc - </em>2D numpy array of dimension (NumFacePoints*NumFaces)
          x NumElements</p>
        <p>specifying the Neuman boundary condition functions along the physical
          boundary.</p>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>getOP(self)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Method to retrieve the DG-discretized sparse 2D Poisson operator.</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Arguments</b></em>
      </td>
      <td style="text-align:left">None</td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Method</b></em>
      </td>
      <td style="text-align:left"><b>getMM(self)</b>
      </td>
    </tr>
    <tr>
      <td style="text-align:left"><em><b>Description</b></em>
      </td>
      <td style="text-align:left">Method to retrieve the DG-discretized sparse 2D Mass matrix operator.</td>
    </tr>
  </tbody>
</table>|  | _\*\*\*\*_ |
| :--- | :--- |


