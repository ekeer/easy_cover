# Font Setup Instructions

## Issue Fixed
The CORS errors you were experiencing were caused by `html-to-image` trying to access CSS rules from external CDN stylesheets (jsdelivr.net and cdnfonts.com). Browsers block this for security reasons.

## Solution Applied
1. **Removed external font CDN links** from `app/layout.tsx`
2. **Updated export function** to handle CORS errors gracefully
3. **Added local font fallbacks** in `app/globals.css`

## To Fully Enable MiSans and HarmonyOS Sans Fonts

### Option 1: Download and Self-Host (Recommended)

#### MiSans Font
1. Download MiSans from: https://github.com/dsrkafuu/misans-vf
2. Place the font files in `public/fonts/`
3. Update `app/globals.css`:

```css
@font-face {
  font-family: 'MiSans';
  src: url('/fonts/MiSans-VF.woff2') format('woff2');
  font-weight: 100 900;
  font-style: normal;
  font-display: swap;
}
```

#### HarmonyOS Sans Font
1. Download HarmonyOS Sans from: https://developer.harmonyos.com/cn/design/resource
2. Place the font files in `public/fonts/`
3. Update `app/globals.css`:

```css
@font-face {
  font-family: 'HarmonyOS Sans';
  src: url('/fonts/HarmonyOSSans-Regular.woff2') format('woff2');
  font-weight: 400;
  font-style: normal;
  font-display: swap;
}

@font-face {
  font-family: 'HarmonyOS Sans';
  src: url('/fonts/HarmonyOSSans-Bold.woff2') format('woff2');
  font-weight: 700;
  font-style: normal;
  font-display: swap;
}
```

### Option 2: Use System Fonts (Fallback)
The current setup uses `local()` which will use the fonts if they're installed on the user's system. This works but won't guarantee consistency across devices.

### Option 3: Use the Upload Font Feature
Users can upload their own font files directly through the UI using the upload button next to the font selector.

## Testing
After adding the fonts:
1. Restart your development server
2. Select MiSans or HarmonyOS Sans from the font dropdown
3. Try exporting - the CORS errors should be gone

## Current Working Fonts
These fonts are already working without CORS issues:
- ✅ Inter (default)
- ✅ Geist Sans
- ✅ Geist Mono
- ✅ SmileySans (得意黑)
- ✅ OPPO Sans
- ✅ Arial, Times New Roman, Courier New
- ✅ 微软雅黑, 黑体, 楷体
- ✅ Any uploaded custom fonts
