# GLITCH.EXE
## Temporal Video Corruption Engine


## 🎯 Overview

GLITCH.EXE is a browser-based video manipulation tool that creates unique glitch aesthetics through temporal corruption algorithms. Unlike traditional video effects that modify pixel data, this engine manipulates the temporal dimension of video playback, creating organic, unpredictable corruption patterns.

### Key Features

- **Temporal Corruption Algorithm**: Probabilistic frame advancement with bidirectional movement
- **Real-time Performance**: Optimized for smooth 30fps playback
- **Professional Recording**: Export glitched videos with synchronized audio
- **Debug Monitoring**: Built-in performance analysis and logging
- **Retro Terminal UI**: Authentic computer terminal aesthetic
- **Zero Dependencies**: Pure HTML5/JavaScript implementation

---

## 🛠️ Technical Specifications

### Core Algorithm

The engine uses a probabilistic temporal manipulation system:

```javascript
if (Math.random() < frameProbability) {
    // Normal forward progression
    currentFrameTime += 1/frameRate;
} else {
    // Glitch behavior: 50% chance bidirectional movement
    if (Math.random() < 0.5) {
        currentFrameTime += (1/frameRate) * (0.5 + Math.random() * 0.5);
    } else {
        currentFrameTime -= (1/frameRate) * (0.2 + Math.random() * 0.3);
    }
}
```

### Performance Optimizations

- **Hardware Acceleration**: Uses requestAnimationFrame for smooth rendering
- **Efficient Video Seeking**: Only updates video time when significant difference detected
- **Canvas Optimization**: Minimal canvas operations for maximum performance
- **Memory Management**: Automatic cleanup and garbage collection optimization

### Browser Compatibility

| Feature | Chrome | Firefox | Safari | Edge |
|---------|--------|---------|--------|------|
| Video Playback | ✅ | ✅ | ✅ | ✅ |
| Canvas Recording | ✅ | ✅ | ✅ | ✅ |
| Audio Sync | ✅ | ✅ | ⚠️ | ✅ |
| File Upload | ✅ | ✅ | ✅ | ✅ |

---

## 🚀 Quick Start

### Option 1: Direct Usage
1. Download `glitch.html`
2. Open in any modern web browser
3. Drag and drop a video file
4. Adjust frame probability and hit play

### Option 2: Local Server
```bash
# Using Python
python -m http.server 8000

# Using Node.js
npx serve .

# Using PHP
php -S localhost:8000
```

### Option 3: Web Server Deployment
Upload to any web server - no server-side processing required.

---

## 📖 User Guide

### Controls

#### Playback Controls
- **PLAY/PAUSE**: Start/stop glitch processing
- **RESET**: Return to video beginning
- **MUTE/UNMUTE**: Toggle audio
- **REC/STOP**: Record glitched output
- **EXPORT**: Download recorded video

#### Parameters
- **Audio Volume**: Control playback volume (0-100%)
- **Frame Probability**: Core glitch control (0-100%)
  - `100%`: Normal playback
  - `75%`: Light glitching
  - `50%`: Moderate corruption
  - `25%`: Heavy glitching
  - `0%`: Maximum chaos

#### Timeline
- **Click to Seek**: Jump to specific time position
- **Progress Bar**: Visual playback progress indicator

### Debug Panel

Real-time performance monitoring:
- **FPS**: Current frame rate
- **Frame Time**: Processing time per frame
- **Video Ready**: Video buffer status
- **Live Log**: System events and warnings

---

## 🔧 Technical Details

### File Format Support
- **Video**: MP4, WebM, OGV, MOV
- **Codecs**: H.264, VP8, VP9, AV1
- **Audio**: AAC, Opus, Vorbis
- **Output**: WebM with VP9/Opus encoding

### API Reference

#### Core Functions
```javascript
// Playback control
play()              // Start glitch processing
pause()             // Pause playback
resetVideo()        // Reset to beginning

// Parameter control
setFrameProbability(value)  // Set glitch intensity (0-1)
setVolume(value)           // Set audio level (0-1)

// Recording
startRecording()    // Begin capture
stopRecording()     // End capture
```

#### Events
```javascript
// Video events
video.addEventListener('loadedmetadata', callback);
video.addEventListener('error', callback);
video.addEventListener('canplay', callback);

// Performance events
updatePerformanceStats();  // Called every 30 frames
```

### Performance Considerations

#### Optimal Settings
- **Video Resolution**: 1920x1080 or lower
- **File Size**: Under 100MB for smooth loading
- **Frame Rate**: 30fps target
- **Duration**: Under 5 minutes for browser stability

#### Memory Usage
- **Baseline**: ~50MB for application
- **Per Video**: ~file_size × 1.5
- **Recording**: ~30MB per minute

---

## 🐛 Troubleshooting

### Common Issues

#### Video Won't Load
```
ERROR: Video load failed
```
**Solutions:**
- Ensure file is valid video format
- Try different video codec (H.264 recommended)
- Check file isn't corrupted
- Use local server instead of file:// protocol

#### Poor Performance
```
WARNING: Low FPS detected
```
**Solutions:**
- Reduce video resolution
- Close other browser tabs
- Disable hardware acceleration if issues persist
- Use shorter video files

#### Recording Fails
```
ERROR: Recording not supported
```
**Solutions:**
- Use HTTPS (required for MediaRecorder)
- Update browser to latest version
- Check browser compatibility table
- Try different video format

### Browser Limitations

#### Security Restrictions
- Local file access limited in some browsers
- HTTPS required for recording features
- Cross-origin restrictions for external videos

#### Performance Limits
- Mobile devices: Reduced performance expected
- Large files: May cause memory issues
- Long recordings: Browser stability varies

---

## 🔬 Algorithm Deep Dive

### Temporal Corruption Theory

The core innovation lies in temporal rather than spatial manipulation:

1. **Traditional Glitch Effects**: Modify pixel values, colors, or spatial arrangements
2. **Temporal Corruption**: Manipulates time dimension, creating non-linear playback

### Mathematical Model

```
frame_advance = {
    if random() < probability:
        return normal_increment
    else:
        direction = random_choice([forward, backward])
        magnitude = random_uniform(0.2, 1.0)
        return direction * magnitude * normal_increment
}
```
