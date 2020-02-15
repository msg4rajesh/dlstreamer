# GStreamer Video Analytics (GVA) Plugin

## Overview
<div align="center"><img src="intro.gif" width=900/></div>

This repository contains GStreamer* elements that enable CNN model-based video analytics capabilities in the GStreamer framework. These elements include such things as object detection, classification, and recognition. Example above shows concise GStreamer pipeline that runs detection & emotion classification, using specific models on a video file:
```sh
gst-launch-1.0 filesrc location=cut.mp4 ! decodebin ! videoconvert ! gvadetect model=face-detection-adas-0001.xml ! gvaclassify model=emotions-recognition-retail-0003.xml model-proc=emotions-recognition-retail-0003.json ! gvawatermark ! xvimagesink sync=false
```

The solution leverages:
* Open-source GStreamer framework for pipeline management
* GStreamer plugins for input and output, such as media files and real-time streaming from a camera or network
* Video decode and encode plugins, including either CPU-optimized plugins or GPU-accelerated plugins, [based on VAAPI](https://github.com/GStreamer/gstreamer-vaapi)

In addition, the solution installs the following Deep Learning-specific elements, also available in this repository:
* Inference plugins leveraging [OpenVINO<sup>&#8482;</sup> Toolkit](https://software.intel.com/en-us/openvino-toolkit) for high-performance inference using CNN models
* Visualization of computer vision results (such as bounding boxes and labels of detected objects) on top of video stream

## License
The GStreamer Video Analytics Plugin is licensed under the [MIT license](LICENSE).

GStreamer is an open source framework licensed under LGPL. See [license terms](https://gstreamer.freedesktop.org/documentation/frequently-asked-questions/licensing.html?gi-language=c). You are solely responsible for determining if your use of Gstreamer requires any additional licenses.  Intel is not responsible for obtaining any such licenses, nor liable for any licensing fees due, in connection with your use of Gstreamer

## Prerequisites
### Hardware
* OpenVINO<sup>&#8482;</sup> Toolkit has information about the [hardware requirements for inference elements](https://software.intel.com/en-us/openvino-toolkit/hardware)
* On platforms with Intel Gen graphics, see the gstreamer-vaapi for [hardware accelerated video decode and encode requirements](https://github.com/GStreamer/gstreamer-vaapi)

### Software
* OpenVINO<sup>&#8482;</sup> Toolkit 2020.1 (Inference Engine 2.1.0) or above
* Linux* system with kernel 4.15 or above
* GStreamer framework 1.14 or above

## Getting Started
* Start here: [Getting Started Guide](https://github.com/opencv/gst-video-analytics/wiki/Getting-Started-Guide-%5B2020.1%5D)
* [API reference](https://opencv.github.io/gst-video-analytics/)
* Gstreamer VA plugin on YouTube: [Full pipeline simulation using GStreamer](https://www.youtube.com/watch?v=fWhPV_IqDy0); [Full pipeline simulation using GStreamer (Samples)](https://www.youtube.com/watch?v=EqHznsUR1sE)

## Samples
See the [command-line examples](samples/shell) and [C++ example](samples/cpp/face_attributes)

## Reporting Bugs and Feature Requests
Report bugs and requests [on the issues page](https://github.com/opencv/gst-video-analytics/issues)

## Usage and integration into application
### Pipelining and data flow
[Details](https://github.com/opencv/gst-video-analytics/wiki/Data-flow) about pipeline construction and the data flow between pipeline elements

### Metadata
[Details](https://github.com/opencv/gst-video-analytics/wiki/Metadata) about metadata generated by inference plugins and attached to video frames

### Model preparation
[Details](https://github.com/opencv/gst-video-analytics/wiki/Model-preparation) about how to prepare Tensorflow*, Caffe*, and other models for the inference plugins

### Plugins parameters
[Elements list](https://github.com/opencv/gst-video-analytics/wiki/Elements) and properties list for each element

## How to contribute
Pull requests aren't monitored, so if you have bug fix or an idea to improve this project, post a description on the [issues page](https://github.com/opencv/gst-video-analytics/issues).

---
\* Other names and brands may be claimed as the property of others.
