# DJI Photo Map Viewer

A lightweight, privacy-focused web app for viewing geotagged drone photos on an interactive map. Perfect for visualizing aerial photography from DJI drones and other GPS-enabled cameras.

## Features

- **Photo thumbnails on map** - See 80x80px previews of your photos at their GPS locations
- **Satellite imagery** - View photos overlaid on high-resolution satellite maps (with optional street map toggle)
- **Full-size image viewer** - Click any thumbnail to view the full-resolution image in a modal
- **Drag-and-drop interface** - Simple file upload with drag-and-drop or click-to-browse
- **100% client-side processing** - All images are processed in your browser; nothing is uploaded to any server
- **Works offline** - After initial load, works completely offline (perfect for field use)
- **No API keys required** - Uses free map tiles from Esri and OpenStreetMap
- **EXIF metadata display** - Shows GPS coordinates, altitude, date/time, and camera model
- **Auto-fit map bounds** - Automatically zooms to show all your photos
- **Single file** - The entire app is contained in one HTML file

## Demo

Just open `photo-map.html` in any modern web browser - no installation or build process needed!

## Usage

1. **Download** the `photo-map.html` file
2. **Open** it in your web browser (Chrome, Firefox, Safari, Edge)
3. **Drop photos** onto the "Drop Photos Here" box or click to select files
4. **View on map** - Thumbnails appear at their GPS coordinates
5. **Click thumbnails** - Opens full-size image with metadata

### Keyboard Shortcuts

- `ESC` - Close full-size image modal

### Switching Map Layers

Click the layers control (top-right corner) to toggle between:
- **Satellite** - High-resolution aerial imagery (default)
- **Street Map** - Traditional road map view

## Browser Compatibility

Works in all modern browsers:
- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Any browser with ES6+ JavaScript support

## Technical Details

### Built With

- **[Leaflet.js](https://leafletjs.com/)** - Interactive map library
- **[exifr](https://github.com/MikeKovarik/exifr)** - Fast EXIF metadata extraction
- **[Esri World Imagery](https://www.arcgis.com/home/item.html?id=10df2279f9684e4a9f6a7f08febac2a9)** - Free satellite tile layer
- **[OpenStreetMap](https://www.openstreetmap.org/)** - Free street map tiles

### How It Works

1. User drops image files into the browser
2. `exifr` extracts GPS coordinates (latitude/longitude) and metadata from EXIF data
3. Photos with valid GPS data are added to the map as thumbnail overlays
4. Leaflet.js handles map rendering, panning, and zooming
5. Clicking a thumbnail displays the full image using JavaScript FileReader API

### Privacy & Security

- **No server uploads** - All processing happens in your browser
- **No external requests** (except CDN libraries on first load and map tiles)
- **No tracking or analytics**
- **No cookies or local storage**
- Your photos never leave your device

## Supported Image Formats

Any image format with EXIF GPS data:
- JPEG (.jpg, .jpeg)
- TIFF (.tif, .tiff)
- PNG (with EXIF)
- RAW formats (DNG, CR2, NEF, etc.)

### Tested With

- DJI Drones (Mini, Air, Mavic, Phantom series)
- Smartphones with GPS
- Cameras with GPS modules

## Troubleshooting

### Photos don't appear on the map

- **Check GPS data** - Use the included `exif-test.html` to verify your photos have GPS coordinates
- **File format** - Ensure images are in a supported format (JPEG recommended)
- **Browser console** - Open developer tools (F12) to check for errors

### Satellite imagery not loading

- **Internet connection** - Satellite tiles require an internet connection
- **Firewall** - Check if `arcgisonline.com` is blocked
- **Switch to street map** - Use the layer control to toggle to OpenStreetMap

## Development

Want to customize the app? Key sections in `photo-map.html`:

```javascript
// Change default map view
const map = L.map('map').setView([0, 0], 2);

// Modify thumbnail size
img.style.width = '80px';  // Line ~304
img.style.height = '80px';

// Adjust initial zoom level when photos load
map.setView([photoData.lat, photoData.lng], 15);  // Line ~284
```

## Contributing

Contributions are welcome! Feel free to:
- Report bugs by opening an issue
- Suggest features or improvements
- Submit pull requests

## License

MIT License - feel free to use, modify, and distribute this project.

## Acknowledgments

- Built with inspiration from [Metainfo Mapper](https://github.com/MaineSkyPixels/Metainfo-Mapper)
- Map data from [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors
- Satellite imagery from [Esri](https://www.esri.com/)

## Support

If you find this useful, please star the repository!

For issues or questions, please open a GitHub issue.

---

**Made with Claude Code** - A simple tool for drone photographers who want to visualize their flights.
