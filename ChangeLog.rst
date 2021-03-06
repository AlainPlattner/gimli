2017-01-19
    Change License to Apache-v2.0

2013-2017
    See git commit messages

2013-12-19
    pygimli:
        meshconvert.py
            add new interpolation target --interpolateMesh
    gimli:
        mesh_io.cpp
            add dimension flag into vtk-export/import

2013-09-04
    pygimli:
        - automatic right-value type conversion for sequence< Tuple> to std::vector < RVector3 >

2012-08-24
    pygimli
        - automatic right-value type conversion for RVector(any sequence with elements that can be transformed into doubles)
            - obsoletes libgimli.asvector() but need heavy testing
        - automatic right-value type conversion for RVector3( list(3), typle(3) )

        - add prototype for solver tutorial (not yet functional)

2012-08-22
    pygimli
        - add app: createParaMesh.py to replace the old dcfemlib createParaMesh
            - currently support only grid/triangle hybrid meshes

2012-08-17
    libgimli::mesh()
        - replaced pIndx by sf( shape function) in isInside method for more sophisticated neighbor search
        - fixed:  slopesearch

2012-08-13
    libgimli::mesh()
        - new createH2 method to support all mesh entity types (need tests)
        - remove old stuff for adaptive meshing ... this needs a new implementation

2012-08-10
    gimli
        - hex, hex20, prism and prism15 and corresponding p2-refinement are seems to be work now
        - add some more FEM-kernel unittests

2012-08-07
    gimli
        - FEM-kernel generalization rebuild (need performance optimizations for simplexes)
        - add 3d-polynomial functor and modelling-class (allow symbolic polynomial expressions and derivations)
        - add shape function cache singleton
        - add generic shape function generator
        - support for hex8, hex20, prism6 prism15

    libgimli::mesh()
        - new createP2 method to support all mesh entity types (need tests)

    libgimli::shape()
        - add generic isInside function
        - renamed touch -> isInside
        - add generic rst2xyz and xyz2rst functions for coordinate transformation between shape coordinates and Cartesian coordinates
        - renamed coordinates() -> rst()
        - add: support for arbitrary valid quadrangles ... we are not longer limited to parallelograms
        - dim()
        - removed jacobianDeterminant() not longer needed
        - add createJacobian()
        - add inverseJacobian()
        - add N, dNdL, dNdrst
        - removed all stuff called 'Shapefunctions' and 'deriveShapeFunctions' and so on
        - add triangular prism
        - add pyramid( unfinished & untested )

    libgimli::meshEntities()
        - renamed dimension() -> dim()
        - removed all stuff called 'Shapefunctions' and 'deriveShapeFunctions'  and so on
        - add N, dNdL

    tests/basics:
        - add script showShapeFunctions3D.py (create vtk-files for all 3d shapefunctions
        - add script testShapePoly.py (play around with shape function generation)



2012-07-10
    libgimli
        mesh_io add vector support for export VTK .. just add std::vector< RVector> to the mesh.exportVTK()

2012-04-03
    libgimli
        fixed bug in Mesh::createNeighbourInfos().
            -fix from 2012-03-26 worked only for 2d.
            -3d case rolled back to working version
        refactor integration rules in integration.h/integration.cpp
            -fixed wrong triangle integration abscissa for order 6
            -add new quadrature weights/abs for generic triangle (not yet tested for fem)
            -convert integration rules to singleton class
        add singleton template class

2012-03-28
    libgimli
        add mesh.importSTL, stl-ascii seams to work, stl-binary need tests

2012-03-26
    libgimli
        fixed bug in Mesh::createNeighbourInfos().
        Sometimes it could happen that a boundary got the wrong left or right cell.
        Unsure if this played any role before. The correct right or left cell for each boundary is essential for gravimetric calculation using integration over boundaries.
    gravimetric:
        add very basic 2d gravimetric modelling based on cell or boundary integration.
        Boundary based is faster then cell based.

2012-02-28
    libgimli
        add default --debug option to the optionmap that enables global --debug mode for all gimli.
        Currently spams a lot of memwatch messages, if available

2012-02-22
    libgimli
        add singleton class memwatch (linux only)

2012-01-27
    version bump -> 0.9.0
    internal change of jacobian storage.
    Jacobian is now stored in forward modelling class.


2012-01-17
    meshconvert.py
        - add input support for *.mod(dc2dinvres), *.vtk, *.vtu(untested)
        - add interpolation into external coordinates to apply a 2D->3D transformation.
            --interpolateCoords=(file) file is a 3-column-ascii-file (dxy x y) to interpolate a 2D-mesh into 3D coordinates
