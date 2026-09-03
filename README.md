# Tabata Timer - React Native App

A simple and intuitive Tabata timer application built with React Native for interval training workouts.

## Overview

Tabata Timer is a mobile application designed to help users perform Tabata interval training workouts. Tabata is a high-intensity interval training (HIIT) method that alternates between intense workout periods and short rest intervals. This app provides an easy-to-use timer with customizable intervals and workout tracking.

## Features

- **Customizable Intervals**
  - Set custom number of sets
  - Configure workout duration (in seconds)
  - Configure rest duration (in seconds)
  - Default: 10 sets, 20-second workout, 10-second rest

- **Timer Display**
  - Large, clear timer display showing remaining time
  - Visual feedback during workouts and rest periods
  - Current set/round counter
  - Total workout progress indicator

- **Workout Control**
  - Start/Pause workout button
  - Stop/Reset button
  - Easy-to-use controls
  - Smooth timer transitions

- **Audio & Visual Feedback**
  - Sound notifications for interval transitions
  - Visual indicators for workout vs. rest periods
  - Different alert sounds for start and completion

- **Workout History**
  - View previous workouts
  - Track workout completion history
  - Session statistics
  - Personal progress tracking

- **Local Storage**
  - Save workout preferences
  - Persist timer settings
  - Store workout history
  - AsyncStorage integration

## Tech Stack

- **Framework**: React Native
- **Language**: JavaScript
- **Build Tool**: Expo
- **State Management**: React Hooks
- **Storage**: AsyncStorage (local device storage)
- **Platforms**: iOS & Android (cross-platform)
- **Package Manager**: npm/yarn

## Prerequisites

- Node.js (v12 or higher)
- npm (v6+) or yarn (v1.22+)
- Expo CLI installed globally
- Expo Go app on Android/iOS device (for development)
- Or Android Studio/Xcode for simulator/emulator

## Installation

1. Clone the repository:
```bash
git clone https://github.com/hungle88/tabata-timer-react-native.git
cd tabata-timer-react-native
```

2. Install Expo CLI globally (if not already installed):
```bash
npm install -g expo-cli
```

3. Install project dependencies:
```bash
npm install
```

4. Navigate to the app directory:
```bash
cd tabata-timer
```

## Development

### Start Development Server
```bash
expo start
```

This will open the Expo Metro Bundler in your terminal.

### Run on Android Device/Emulator

Option 1 - Using Expo Go:
```bash
# Scan QR code with Expo Go app on your Android device
expo start
```

Option 2 - Using Android Emulator:
```bash
expo start --android
```

### Run on iOS Device/Simulator

Option 1 - Using Expo Go:
```bash
# Scan QR code with Expo Go app on your iOS device
expo start
```

Option 2 - Using iOS Simulator (macOS only):
```bash
expo start --ios
```

### Web Preview
```bash
expo start --web
```

Navigate to `http://localhost:19006`

## Project Structure

```
tabata-timer-react-native/
├── tabata-timer/
│   ├── src/
│   │   ├── components/
│   │   │   ├── TimerDisplay.js      # Main timer display
│   │   │   ├── IntervalSettings.js  # Settings configuration
│   │   │   ├── ControlButtons.js    # Start/Stop/Reset buttons
│   │   │   ├── WorkoutHistory.js    # Past workouts list
│   │   │   └── ProgressBar.js       # Progress indicator
│   │   ├── screens/
│   │   │   ├── HomeScreen.js        # Main screen
│   │   │   ├── SettingsScreen.js    # Settings screen
│   │   │   └── HistoryScreen.js     # Workout history
│   │   ├── services/
│   │   │   ├── StorageService.js    # AsyncStorage management
│   │   │   ├── TimerService.js      # Timer logic
│   │   │   └── SoundService.js      # Audio notifications
│   │   ├── styles/
│   │   │   └── styles.js            # Global styles
│   │   ├── App.js                   # Root component
│   │   └── index.js                 # Entry point
│   ├── assets/
│   │   ├── sounds/                  # Audio files
│   │   ├── images/                  # Icon assets
│   │   └── fonts/                   # Custom fonts
│   ├── app.json                     # Expo configuration
│   └── package.json
├── .expo-shared/                    # Expo shared files
└── README.md
```

## Key Components

### Timer Display Screen
- **Large Time Display** - Shows MM:SS format
- **Set Counter** - Displays current set / total sets
- **Phase Indicator** - Shows "Workout" or "Rest" phase
- **Progress Bar** - Visual representation of current interval progress

### Settings Screen
- **Sets Input** - Number of sets (default: 10)
- **Workout Duration** - Seconds for intense workout (default: 20)
- **Rest Duration** - Seconds for rest period (default: 10)
- **Save/Reset** - Apply or reset to defaults
- **Preview** - Show total workout time

### Workout History Screen
- **Completed Workouts List** - Shows date, time, and duration
- **Workout Details** - Sets completed, total time
- **Delete Option** - Remove individual workouts
- **Stats Summary** - Total workouts, total time

## Tabata Workout Format

Standard Tabata format:
- 20 seconds: High-intensity workout
- 10 seconds: Rest period
- Repeat: 8 sets (4 minutes total)

This app allows customization:
- Sets: 1-20 (customizable)
- Workout: 10-60 seconds (customizable)
- Rest: 5-30 seconds (customizable)

Example: 10 sets × (20s workout + 10s rest) = 5 minutes

## Features in Detail

### Timer Logic
- Countdown timer starting from configured duration
- Automatic phase switching (workout → rest)
- Set counter increment after rest period
- Auto-stop after all sets completed
- Pause/Resume functionality

### Storage Management
- Save workout preferences using AsyncStorage
- Persist workout history
- Automatic data backup
- Clear history option

### Audio/Visual Feedback
- Beep sound at workout start
- Beep sound at workout end (rest start)
- Beep sound at rest end (next workout start)
- Different sound volumes for different events
- Visual color changes (red for workout, green for rest)

## Customization

### Change Default Values
Edit `src/screens/SettingsScreen.js`:
```javascript
const DEFAULT_SETS = 10;
const DEFAULT_WORKOUT_DURATION = 20; // seconds
const DEFAULT_REST_DURATION = 10;    // seconds
```

### Modify Styling
Edit `src/styles/styles.js` to customize:
- Colors
- Font sizes
- Layout dimensions
- Border radius
- Shadow effects

### Change Sound Files
Replace audio files in `assets/sounds/`:
- `workout-start.mp3`
- `workout-end.mp3`
- `rest-end.mp3`

## Building for Production

### Build for Android
```bash
eas build --platform android
```

### Build for iOS
```bash
eas build --platform ios
```

### Create Standalone APK (Android)
```bash
expo build:android
```

### Create Standalone IPA (iOS - requires paid Apple Developer account)
```bash
expo build:ios
```

## Performance Optimization

- Optimize re-renders with React.memo for static components
- Use useCallback for event handlers
- Implement useRef for timer intervals
- Lazy load audio files
- Optimize image assets
- Minimize bundle size

## Testing

### Manual Testing
- Test timer accuracy
- Test pause/resume functionality
- Test custom interval inputs
- Test history storage and retrieval
- Test audio playback
- Test on multiple devices

### Unit Tests
```bash
npm test
```

## Common Issues & Solutions

### Issue: Timer not starting
- Ensure audio permissions are granted
- Check if permissions are requested in `app.json`
- Verify timer service initialization

### Issue: Audio not playing
- Check device volume is not muted
- Verify audio files exist in assets folder
- Test audio permissions on device

### Issue: History not saving
- Verify AsyncStorage is properly initialized
- Check device storage availability
- Clear app cache if data corrupts

### Issue: App crashes on start
- Clear Expo cache: `expo r -c`
- Reinstall dependencies: `rm -rf node_modules && npm install`
- Check for console errors: `expo start --verbose`

## Device Compatibility

### Android
- Minimum SDK: Android 5.0 (API 21)
- Target SDK: Android 12+ (API 31+)
- Recommended: Android 6.0+

### iOS
- Minimum: iOS 11.0
- Recommended: iOS 13.0+
- Tested on: iPhone 8 and newer

## Platform-Specific Notes

### Android
- Uses MediaPlayer for audio
- Requires `INTERNET` permission (for Expo services)
- `READ_EXTERNAL_STORAGE` for local files
- `WRITE_EXTERNAL_STORAGE` for history backup

### iOS
- Uses AVFoundation for audio
- Requires microphone permission (for Expo)
- Background mode for timer notifications (if enabled)

## Configuration Files

### app.json
Configure Expo settings:
```json
{
  "expo": {
    "name": "Tabata Timer",
    "slug": "tabata-timer",
    "version": "1.0.0",
    "sdkVersion": "45.0.0",
    "platforms": ["ios", "android", "web"]
  }
}
```

### EAS Build Configuration
Create `eas.json` for building:
```json
{
  "build": {
    "production": {
      "android": {
        "buildType": "apk"
      }
    }
  }
}
```

## Deployment

### Submit to Google Play Store
1. Build APK: `eas build --platform android`
2. Sign with keystore
3. Upload to Google Play Console
4. Complete store listing details
5. Submit for review

### Submit to Apple App Store
1. Requires Apple Developer account ($99/year)
2. Build IPA: `eas build --platform ios`
3. Sign with certificates
4. Upload via Transporter
5. Complete app information
6. Submit for review

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## Code Style

- Follow React best practices
- Use functional components with hooks
- Use meaningful variable names
- Add comments for complex logic
- Follow ESLint configuration
- Use camelCase for variables
- Use PascalCase for components

## Performance Tips

- Keep re-renders minimal
- Use React.memo for expensive components
- Cache computed values with useMemo
- Debounce input handlers
- Lazy load components when possible
- Monitor app performance with React DevTools

## Resources

- [React Native Documentation](https://reactnative.dev)
- [Expo Documentation](https://docs.expo.dev)
- [Tabata Training Info](https://en.wikipedia.org/wiki/Tabata)
- [React Hooks Guide](https://react.dev/reference/react/hooks)

## License

This project is open source and available under the MIT License.

## Author

**Hung Le** - [GitHub Profile](https://github.com/hungle88)

## Support

For support, open an issue in the repository or contact the development team.

## Related Projects

- [Course Review App (React Native)](https://github.com/hungle88/course-review-app-react-native)
- [GitHub App (React Native)](https://github.com/hungle88/github-app-react-native)
- [CSR React Native](https://github.com/hungle88/csr-reactnative)