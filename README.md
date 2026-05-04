# IPTV Channels Android App

A comprehensive Android application for streaming 1,130+ IPTV channels with support for both mobile devices and Android TV.

## Features

- ✅ **1,130+ Channels**: Access to a vast library of live TV channels
- ✅ **Dynamic Configuration**: Channels are fetched from a centralized API
- ✅ **Android TV Support**: Optimized interface for smart TVs and Android TV boxes
- ✅ **Custom Headers**: Supports channels requiring custom HTTP headers (Referer, Origin, Cookie, etc.)
- ✅ **Offline Caching**: Configuration is cached for offline access
- ✅ **HLS Streaming**: Full support for HLS (M3U8) streams via ExoPlayer
- ✅ **Modern UI**: Material Design with responsive layouts

## Requirements

- Android 7.0 (API 24) or higher
- Internet connection for initial channel loading
- Android TV support (optional, for TV devices)

## Building the App

1. **Open the project** in Android Studio
2. **Sync Gradle** dependencies
3. **Build** the project (Build > Make Project)
4. **Run** on an emulator or physical device

### Build Commands

```bash
# Build debug APK
./gradlew assembleDebug

# Build release APK
./gradlew assembleRelease

# Install on connected device
./gradlew installDebug
```

## Project Structure

```
app/
├── src/main/
│   ├── java/com/example/iptv/
│   │   ├── MainActivity.java          # Channel list screen
│   │   ├── PlayerActivity.java        # Video player screen
│   │   ├── ConfigManager.java         # API configuration manager
│   │   ├── Channel.java               # Channel data model
│   │   └── ChannelAdapter.java        # RecyclerView adapter
│   ├── res/
│   │   ├── layout/                    # UI layouts
│   │   ├── values/                    # Strings, themes, colors
│   │   └── drawable/                  # Icons and graphics
│   └── AndroidManifest.xml            # App configuration
```

## Configuration API

The app fetches channel data from:
```
https://adsportal.media-colony.com/users/AlbKanaleV9.1/config.php
```

### Request Parameters
- `device`: Android Device ID
- `android`: Android version
- `model`: Device model

### Required Headers
- `User-Agent`: Android Vinebre Software
- `Referer`: https://www.digitalturbine.com/
- `Cookie`: Update=1763997662

## Usage

1. **Launch the app** - The app will automatically fetch the latest channel configuration
2. **Browse channels** - Scroll through the channel list (grid layout)
3. **Select a channel** - Tap/click on any channel to start playback
4. **Watch** - The player opens in fullscreen landscape mode
5. **Navigate back** - Use the back button to return to the channel list

### Android TV Usage

- Use the **D-pad** or **remote control** to navigate
- **OK/Select** button to play a channel
- **Back** button to return to channel list
- Channels are displayed in a 4-column grid for better TV viewing

## Channel Information

Each channel contains:
- **ID**: Unique channel identifier
- **Name**: Display name
- **URL**: Stream URL (M3U8, MP4, or PHP proxy)
- **Headers**: Custom HTTP headers (Referer, Origin, Cookie, X-Forwarded-For)
- **User-Agent**: Custom user agent string (optional)
- **Type**: TV or Radio

## Technical Details

### Dependencies

- **ExoPlayer 1.2.1**: Media playback engine
- **OkHttp 4.12.0**: HTTP client for API calls and streaming
- **AndroidX Libraries**: Modern Android support libraries
- **Leanback**: Android TV support

### Stream Formats Supported

- **HLS (M3U8)**: Primary format for live streams
- **DASH**: Adaptive streaming (fallback)
- **Progressive (MP4)**: Direct video files (fallback)

### Caching

Configuration is cached locally using SharedPreferences:
- Location: `albkanale_prefs`
- Key: `config_json`
- Updated on app startup or manual refresh

## Troubleshooting

### Channels Not Loading

1. Check internet connection
2. Verify API endpoint is accessible
3. Check device date/time settings
4. Clear app cache and restart

### Playback Issues

1. Ensure channel URL is valid
2. Check if channel requires custom headers
3. Verify network connectivity
4. Try a different channel

### Android TV Issues

1. Ensure device supports Leanback
2. Check remote control connectivity
3. Verify TV has internet access
4. Restart the app

## Permissions

The app requires:
- **INTERNET**: For fetching configuration and streaming
- **ACCESS_NETWORK_STATE**: To check network availability
- **WAKE_LOCK**: To keep screen on during playback

## License

This project is provided as-is for educational and personal use.

## Support

For issues or questions:
1. Check the troubleshooting section
2. Review the code documentation
3. Verify API endpoint accessibility

---

**Note**: Channel availability depends on the configuration API. The app does not host any content and only provides access to streams configured by the API provider.
# free_iptv
