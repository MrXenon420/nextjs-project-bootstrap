# Padelo Flutter App - Play Store Deployment Guide

## 📱 Project Overview
**Padelo** is a comprehensive Flutter mobile application for padel tournaments and community management.

### Key Features
- Multi-language support (English/Arabic)
- Tournament management and player rankings
- Marketplace for equipment trading
- Court booking system
- Training coordination
- Community chat and support
- Admin panel for content moderation
- Role-based access control (Owner, Court Owner, Tournament Organizer, Coach, Player)

## 🚀 Play Store Deployment Steps

### 1. Prerequisites
- Install Flutter SDK (3.24.5 or later)
- Install Android Studio with Android SDK
- Set up Android signing key

### 2. Project Setup
```bash
# Extract the project
tar -xzf padelo-flutter-app.tar.gz
cd padelo

# Install dependencies
flutter pub get

# Verify Flutter setup
flutter doctor
```

### 3. Android Configuration

#### Update App Information
Edit `android/app/build.gradle`:
```gradle
android {
    compileSdkVersion 34
    
    defaultConfig {
        applicationId "com.padelo.app"
        minSdkVersion 21
        targetSdkVersion 34
        versionCode 1
        versionName "1.0.0"
    }
}
```

#### Update App Name
Edit `android/app/src/main/AndroidManifest.xml`:
```xml
<application
    android:label="Padelo"
    android:name="${applicationName}"
    android:icon="@mipmap/ic_launcher">
```

### 4. Generate App Icons
- Create app icons for different densities
- Place in `android/app/src/main/res/mipmap-*` folders
- Use the Padelo logo with the green padel ball "O"

### 5. Create Signing Key
```bash
keytool -genkey -v -keystore ~/padelo-key.jks -keyalg RSA -keysize 2048 -validity 10000 -alias padelo
```

### 6. Configure Signing
Create `android/key.properties`:
```properties
storePassword=YOUR_STORE_PASSWORD
keyPassword=YOUR_KEY_PASSWORD
keyAlias=padelo
storeFile=../padelo-key.jks
```

### 7. Build Release APK/AAB
```bash
# Build APK
flutter build apk --release

# Build App Bundle (recommended for Play Store)
flutter build appbundle --release
```

### 8. Play Store Submission

#### Required Assets
- App icon (512x512 PNG)
- Feature graphic (1024x500 PNG)
- Screenshots (phone and tablet)
- Privacy policy URL
- App description

#### App Store Listing
**Title**: Padelo - Padel Tournaments & Community

**Short Description**: 
Professional padel tournament management and community app with court booking, marketplace, and player rankings.

**Full Description**:
Padelo is the ultimate padel community app that brings players, coaches, court owners, and tournament organizers together in one comprehensive platform.

🏆 **Tournament Management**
- Create and join tournaments
- Player ranking system
- Performance tracking
- Entry fee management

🏪 **Marketplace**
- Buy and sell padel equipment
- Community-driven trading
- Secure transactions

🎾 **Court Booking**
- Find and book courts
- Real-time availability
- Direct reservation system

👨‍🏫 **Training & Coaching**
- Find certified coaches
- Book training sessions
- Skill development programs

💬 **Community Features**
- Chat with other players
- Follow your favorite players
- Community support system

🌍 **Multi-Language Support**
- English and Arabic
- RTL support for Arabic users

### 9. App Permissions
The app requires these permissions (already configured):
- Internet access
- Camera (for profile pictures)
- Storage (for image uploads)

### 10. Testing
```bash
# Run tests
flutter test

# Test on device
flutter run --release
```

## 📋 Pre-Launch Checklist
- [ ] Test all user roles and permissions
- [ ] Verify Arabic RTL layout
- [ ] Test tournament creation and joining
- [ ] Verify marketplace functionality
- [ ] Test court booking system
- [ ] Check chat functionality
- [ ] Verify admin panel access
- [ ] Test on different screen sizes
- [ ] Performance testing
- [ ] Security review

## 🔧 Configuration Notes

### Demo Credentials
- Email: `demo@padelo.com`
- Password: `demo123`
- Role: Player

### API Integration
The app currently uses mock data. To connect to a real backend:
1. Update `ApiConstants.baseUrl` in `lib/core/utils/constants.dart`
2. Implement actual API calls in service files
3. Add authentication tokens
4. Configure push notifications

### Customization
- Colors: Modify `lib/core/theme/app_theme.dart`
- Languages: Update `lib/core/providers/language_provider.dart`
- Features: Add new screens in `lib/screens/`

## 📞 Support
For technical support or questions about the app deployment, refer to the Flutter documentation or contact the development team.

## 📄 License
This project is proprietary software developed for Padelo.
