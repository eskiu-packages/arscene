<p align="center">
  <img src="https://raw.githubusercontent.com/eskiu-lang/eskiu/main/assets/logo.png" alt="Eskiu, a kitten with a ball of yarn" width="140">
</p>

<h2 align="center">arscene</h2>
<p align="center">Augmented reality on scene: the camera, occlusion, placement and image markers.</p>
<p align="center"><sub>Part of the <a href="https://github.com/eskiu-lang">Eskiu</a> project</sub></p>
<p align="center">
  <a href="https://eskiu-lang.org">eskiu-lang.org</a> &nbsp;&middot;&nbsp;
  <a href="docs/README.md">Documentation</a> &nbsp;&middot;&nbsp;
  <a href="https://github.com/eskiu-lang/eskiu">The language</a>
</p>

<p align="center">
  <a href="https://github.com/eskiu-packages/arscene/actions/workflows/ci.yml?query=branch%3Adevelop"><img src="https://github.com/eskiu-packages/arscene/actions/workflows/ci.yml/badge.svg?branch=develop" alt="CI"></a>
  <img src="https://img.shields.io/badge/version-0.1.5-6448d4" alt="Version 0.1.5">
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue" alt="License: MIT"></a>
</p>

---

`arscene` joins an [ar](https://github.com/eskiu-packages/ar) session to a
[scene](https://github.com/eskiu-packages/scene), doing what ViroReact's AR scene navigator does
for an app:

- **ArStage.** Each frame: the camera picture behind the scene, the device as the scene's
  camera with the session's projection, and the real world's depth (LiDAR, ARCore's Depth
  API) hiding virtual content behind real surfaces.
- **ArPlacer.** Tap to place, as `ViroARPlaneSelector`: the surfaces found drawn translucent,
  a ring where the middle of the view meets one, the content put on the surface tapped,
  facing the user, with a floor that shows its shadows on the real one. It can be limited to
  kinds of surface (floor, table, wall...).
- **ArMarkers.** Content on tracked images, as `ViroARImageMarker`, with found and lost
  events.
- **ArWorldMesh.** The room as LiDAR reconstructs it, as invisible occluders (or shown, to see
  what was mapped).

```eskiu
ArStage stage = ar_stage(&scene, cam)?;
ArPlacer placer = ar_placer(&scene, content)?;
placer.scale = 0.2;
use_ar_session(ArOptions{horizontal: true, depth: true, people: true}, void(*ArFrame frame) {
    stage.frame(&scene, frame, width, height)?;
    placer.frame(&scene, frame, (float)width, (float)height)?;
    if (tapped) placer.tap(&scene, frame, tap_x, tap_y, (float)width, (float)height);
    scene.render(view, width, height, format)?;
});
```

## Documentation

- [Guide](docs/README.md): the stage, placing, markers, tests
- [API reference](docs/api.md): every public function and type

## Install

```bash
eskiuc add arscene --git https://github.com/eskiu-packages/arscene --rev v0.1.5
```

It brings ar and scene.

## License

MIT. See [LICENSE](LICENSE).
