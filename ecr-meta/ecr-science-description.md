## Science

This application demonstrates how edge computing can be used to perform real-time pedestrian flow analysis using YOLOv8 and a lightweight tracker. By detecting people and estimating their left-versus-right movement across a scene, the system provides continuous insight into how humans move through spaces such as hallways, sidewalks, campus pathways, and transit areas.

The scientific relevance lies in enabling **low-latency observation of movement patterns** without streaming full video to the cloud. This supports research and applications in:

* crowd safety and congestion monitoring
* space utilization and urban planning
* behavioral and environmental studies
* smart-infrastructure and sensor network design

This app is also designed as an **educational instructional activity**. It helps students understand how edge AI systems work by showing how object detection, tracking, and metadata publishing can run directly on edge devices like Thor, connecting core concepts in AI@Edge to a simple movement-tracking task.

---

## AI@Edge

The application uses **YOLOv8 with Ultralytics ByteTrack** to detect and track people in real time.

Workflow:

1. A frame is captured from a video file, RTSP stream, or Waggle camera.
2. YOLOv8 detects people, and ByteTrack assigns stable track IDs across frames.
3. For each track, the change in X position determines whether a person moved left or right.
4. Direction counts and system statistics are logged to CSV and can be published as Waggle metadata.

Running this pipeline directly on the edge reduces bandwidth use, lowers latency, and allows continuous operation even in bandwidth-limited or remote locations.

---

## Model Capabilities

**YOLOv8 (n, s, m, l, x)**

* Real-time object detection with configurable model sizes
* Detects people reliably in typical indoor and outdoor scenes
* Scales from fast/lightweight (`n`) to more accurate/heavier (`x`) depending on device resources

---

## Ontology

Each movement event is tagged with:

* direction (left or right)
* starting and ending X positions
* timestamp
* CPU and GPU utilization
* RAM usage
* device temperature (when available)
* cumulative left/right counts

These metadata support analysis of movement patterns and device performance over time, while keeping the processing and storage local to the edge.
