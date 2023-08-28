# GeoIO.jl

[![][build-img]][build-url] [![][codecov-img]][codecov-url]

Load geospatial tables from known file formats and convert the
geometries to [Meshes.jl](https://github.com/JuliaGeometry/Meshes.jl)
geometries that are compatible with the
[GeoStats.jl](https://github.com/JuliaEarth/GeoStats.jl) ecosystem. 

Geometries are loaded from disk in pure Julia whenever possible
using packages such as [Shapefile.jl](https://github.com/JuliaGeo/Shapefile.jl)
and [GeoJSON.jl](https://github.com/JuliaGeo/GeoJSON.jl), or
(down)loaded from the internet using the
[GADM.jl](https://github.com/JuliaGeo/GADM.jl) package.

## Usage

### Loading/saving data from/to disk

The `load` and `save` functions are self-explanatory:

```julia
using GeoIO

table = GeoIO.load("file.shp")

GeoIO.save("file.geojson", table)
```

Additional keyword arguments can be passed to `load` and `save` functions. Valid
arguments are those accepted by `GeoJSON.read`, `GeoJSON.write`, `Shapefile.Table`,
`Shapefile.write` and `ArchGDAL.read`. See below some examples:

```julia
# read `.geojson` geometries with Float64 precision
table = GeoIO.load("file.geojson", numbertype = Float64)

# force writing on existing `.shp` file
GeoIO.save("file.shp", table, force = true)
```

Please read the docstrings for more details.

### Loading data from GADM

The `gadm` function (down)loads data from the GADM dataset:

```julia
julia> GeoIO.gadm("BRA", depth = 1)
```

Please read the docstring for more details.

## Asking for help

If you have any questions, please [contact our community](https://juliaearth.github.io/GeoStats.jl/stable/about/community.html).

[build-img]: https://img.shields.io/github/actions/workflow/status/JuliaEarth/GeoIO.jl/CI.yml?branch=master&style=flat-square
[build-url]: https://github.com/JuliaEarth/GeoIO.jl/actions

[codecov-img]: https://img.shields.io/codecov/c/github/JuliaEarth/GeoIO.jl?style=flat-square
[codecov-url]: https://codecov.io/gh/JuliaEarth/GeoIO.jl
