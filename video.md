Instructions for USB camera video display 

```bash
GST_DEBUG=3 gst-launch-1.0 v4l2src ! videoscale ! videoconvert ! video/x-raw, width=640, height=480 ! queue ! waylandsink window-width=640 window-height=48
```

