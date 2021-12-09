# mvt

[![GoDoc](https://img.shields.io/badge/api-reference-blue.svg?style=flat-square)](https://godoc.org/github.com/tidwall/mvt)

Draw [Mapbox Vector Tiles](https://www.mapbox.com/vector-tiles/) with ease.

## Features

- Mapbox Vector Tiles 2.1 support
- MoveTo, LineTo, CubicTo, QuadraticTo
- Defined 512x512 canvas
- Uses floating points
- Add tags and IDs to features
- Fast encoding to MVT protobufs
- No external dependencies

## Install

```
go get -u github.com/tidwall/mvt
```

## Example

```go
var tile mvt.Tile
l := tile.AddLayer("triforce")
f := l.AddFeature(mvt.Polygon)

f.MoveTo(128, 96)
f.LineTo(148, 128)
f.LineTo(108, 128)
f.LineTo(128, 96)
f.ClosePath()

f.MoveTo(148, 128)
f.LineTo(168, 160)
f.LineTo(128, 160)
f.LineTo(148, 128)
f.ClosePath()

f.MoveTo(108, 128)
f.LineTo(128, 160)
f.LineTo(88, 160)
f.LineTo(108, 128)
f.ClosePath()

data := tile.Render()

// Data now contains a valid mapbox vector tile protobuf 
// for sending over the internets and styling to your 
// heart's content.
```

<img src="https://i.imgur.com/ynIx6nt.png" width="300" height="300">

## Helper functions

- `mvt.LatLonXY`: Converts a lat/lon to the pixel offset for a specific tile.
- `mvt.TileBounds`: Returns the lat/lon boundary for a tile.

## Contact
Josh Baker [@tidwall](http://twitter.com/tidwall)

## License
mvt source code is available under the MIT [License](/LICENSE).
