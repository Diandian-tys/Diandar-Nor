# Diandar Nor

A cute little companion that lives on your Android screen 🐾

**Diandar Nor** is an Android desktop pet (floating overlay) app. It keeps a small pet always on top of other apps, supports custom phrases, auto-sleep, a home-screen widget, and real AI chat using your own API key.

- **Package**: `com.example.desktoppet`
- **Version**: 1.7 (versionCode 8)
- **Min SDK**: Android 7.0 (API 24)
- **Target SDK**: Android 14 (API 34)

## Features

### Floating Desktop Pet
- Uses `SYSTEM_ALERT_WINDOW` for a global overlay window
- Drag to reposition, tap to interact (randomly speaks a custom phrase)
- Auto-sleep after ~30 seconds of inactivity (multi-frame WebP animation); tap to wake
- Adjustable size (approx. 60%–160%) and opacity (30%–100%)
- Foreground service with notification for reliable persistence

### Custom Phrases
- Edit the lines the pet says when tapped (one phrase per line)
- Restore default phrases at any time
- Interface language changes are reflected immediately

### AI Chat
- Supports multiple OpenAI-compatible providers:
  - OpenAI (`https://api.openai.com/v1`)
  - DeepSeek (`https://api.deepseek.com/v1`) — `deepseek-chat` / `deepseek-reasoner`
  - Moonshot (`https://api.moonshot.cn/v1`)
  - Zhipu BigModel (`https://open.bigmodel.cn/api/paas/v4`)
  - Alibaba Cloud DashScope compatible mode (`https://dashscope.aliyuncs.com/compatible-mode/v1`)
- You provide your own API key (stored only on the device)
- Three reply modes: Simple (1–2 sentences), Medium, Deep (detailed)
- Multi-turn conversations, conversation history, edit / delete / regenerate messages
- System prompt automatically switches with the current UI language (Chinese, English, Japanese, Korean, Spanish, Filipino, Hindi, Russian, etc.)

### Home Screen Widget
- App Widget that shows the pet on the launcher
- Tap the phrase to cycle lines, tap the pet to open the app

### Other
- Multi-language UI + matching AI system prompts
- Debuggable build
- Developer links (GitHub / X / YouTube)

## Permissions

| Permission | Purpose |
|------------|---------|
| `SYSTEM_ALERT_WINDOW` | Show the floating pet window |
| `FOREGROUND_SERVICE` / `FOREGROUND_SERVICE_SPECIAL_USE` | Keep the overlay service alive |
| `POST_NOTIFICATIONS` | Foreground service notification |
| `INTERNET` | AI chat requests |

> On some Chinese OEM devices (Xiaomi, Huawei, OPPO, etc.) you may also need to allow “Display over other apps”, “Background popup”, or “Autostart” in system settings.

## Technical Notes (from APK analysis)

- Native Android (Java) with AndroidX / Material components
- Main classes:
  - `MainActivity` / `SettingsActivity` / `ApiSettingsActivity`
  - `ChatActivity` / `ConversationListActivity`
  - `PetService` (overlay core)
  - `PetWidgetProvider`
  - `AiClient` / `AiConfig` / `ChatStore`
- Assets include a pet PNG and sleep WebP frame sequence
- Overlay implemented with `WindowManager`

## Build & Release Notes

If you are the original author and plan to publish:

1. Change the package name from `com.example.desktoppet` to your own reverse-domain name
2. Disable `android:debuggable="true"`
3. Configure signing and ProGuard / R8
4. Keep the `PROPERTY_SPECIAL_USE_FGS_SUBTYPE` description clear in the manifest

## Disclaimer

- The API key is provided and stored entirely by the user; this app does not offer any proxy or free quota
- Please follow the terms of service of each AI provider and local regulations
- Overlay permission may be restricted by some systems; make sure it is granted before use

## Developer

- GitHub: [Diandian-tys](https://github.com/Diandian-tys)
- X: [@Diandian162](https://x.com/Diandian162)
- YouTube: [@diandian-r4o1p](https://youtube.com/@diandian-r4o1p)

---

Made with ❤️ for desktop companion lovers.
