# Changelog

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
