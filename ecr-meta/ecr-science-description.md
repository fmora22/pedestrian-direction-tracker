## Science

This application is primarily designed as an educational activity that teaches students how edge computing works in real time. By running YOLOv8 detection and simple movement tracking directly on an edge device, students gain hands on experience with video processing, object detection, tracking, and publishing metadata on a live system. The goal is to help learners understand the core ideas behind artificial intelligence at the edge through a simple and approachable movement tracking task.

In addition to its instructional purpose, this application also demonstrates how edge devices can be used for real time pedestrian flow analysis. By detecting people and estimating whether they move left or right across a scene, the system provides continuous insight into how individuals navigate hallways, sidewalks, campus paths, or crowded spaces without sending full video feeds to the cloud.

The scientific value of this tool extends to several areas of research and practice including:

* crowd safety and congestion monitoring
* analysis of space usage in urban and campus environments
* behavioral and environmental movement studies
* design of intelligent infrastructure and sensor networks

Processing happens directly on the device which allows low latency observations, efficient use of bandwidth, and improved privacy. This makes the tool useful both for teaching and for real world applications that benefit from artificial intelligence at the edge.

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
