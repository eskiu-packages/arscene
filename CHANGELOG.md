# Changelog

All notable changes to this package are documented here. The format follows
[Keep a Changelog](https://keepachangelog.com/en/1.1.0/), and versions follow
[Semantic Versioning](https://semver.org/).

## [0.1.5] - 2026-11-26

### Changed

- Depends on ui 0.8.0, gpu 0.8.0, scene 0.3.0 and ar 0.2.4.

## [0.1.4]

### Changed

- Depends on gpu 0.7.2 and scene 0.2.3.

## [0.1.3]

### Changed

- Depends on ar 0.2.3 and ui 0.7.0.

## [0.1.2]

### Added

- `<arscene/anchors>`: `ArAnchors` keeps nodes where they were put in the real world. Each gets
  an anchor of the session once tracking is normal, and the anchor's movement becomes the
  node's base (scene's `SceneNode.base`), so its position, animations, drags and physics stay
  in its parent's coordinates. Tries, their spacing and re-anchoring by distance are settings.

### Changed

- Depends on ar 0.2.2, scene 0.2.2 and ui 0.6.2.

## [0.1.1]

### Changed

- The package moved to the eskiu-packages organization; the old URL redirects. Depends on ar 0.2.1, scene 0.2.1, gpu 0.7.1 and ui 0.6.1.

## [0.1.0]

The first release. Needs Eskiu 0.15.1 or newer; brings ar 0.2.0, scene 0.2.0, gpu 0.7.0 and
ui 0.6.0.

### Added

- `ArStage`: each AR frame into a scene: the camera picture as the background, the device as
  the camera with the session's projection, depth occlusion, the light estimate.
- `ArPlacer`: tap to place (ViroARPlaneSelector): translucent planes, a ring at the middle of
  the view, placement facing the user at a scale, a shadow-catching floor, kinds of surface.
- `ArMarkers`: nodes on tracked images with found and lost events (ViroARImageMarker).
- `ArWorldMesh`: the LiDAR reconstruction as scene nodes, invisible occluders by default or
  shown in a color.
- `ArStage` passes the session's scene semantics to the scene, for semantic masks.
- Physics against the real world: `ArWorldMesh.physics` (a body per LiDAR piece) and
  `ArDepthCollider` / `ar_depth_triangles` (the depth image as a triangle body).
- `ArMarkers_add_object`: nodes on ARKit object targets (ViroARObjectMarker).
