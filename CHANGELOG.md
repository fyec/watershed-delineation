# Changelog

## [0.1.3] - 2025-08-29
### Added
- Unified export toggles for final/basin stage outputs:
  - Input pour point (WGS84)
  - Snapped pour point (DEM CRS)
  - Basin-clipped DEM
  - Final D8 pointer (within basin)
  - Final Flow Accumulation (within basin)
  - Longest Flow Path (LFP)
- Automatic addition of UTM zone information (`UTMBX_*`, `UTMBN_*`) to polygon attributes.
- Safe shapefile writing helper that removes existing sidecars to avoid driver errors.

### Changed
- Snap distance is now estimated dynamically from DEM resolution × multiplier (default `20`) if not provided.
- Pour point snapping improved with robust DEM CRS handling and geographic vs projected CRS support.
- Internal logging messages standardized with clearer stage separation.
- Export scope simplified: Stage-1 rasters (intermediate D8/FAC) are no longer written out; only final basin-stage outputs are supported.

---

## [0.1.1] - 2025-08-24
### Fixed
- **Longest Flow Path calculation**: now projects geometries to UTM before computing lengths.  
  This removes warnings about “Geometry is in a geographic CRS” and ensures correct LFP length in meters.
- Improved watershed attribute computation robustness by handling CRS properly.

### Changed
- Bumped package version from `0.1.0` → `0.1.1`.

---

## [0.1.0] - 2025-08-23
- Initial release with core watershed delineation workflow:
  - DEM clipping
  - Pour point snapping
  - Flow direction & accumulation
  - Watershed polygon extraction
  - Basin attributes (area, perimeter, slope, elevation stats, drainage density, etc.)
