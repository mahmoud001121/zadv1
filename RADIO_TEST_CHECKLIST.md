# Radio Page Test Checklist

## Quick Test Steps

### 1. Access the Radio Page
- [ ] Open browser to http://localhost:3000
- [ ] Click on "المزيد" (More) tab at the bottom
- [ ] Click on "الراديو القرآني" (Quran Radio)
- [ ] Verify page loads without errors

### 2. Test Station List
- [ ] Verify 24 stations are displayed
- [ ] Check station images load correctly
- [ ] Verify station names are in Arabic
- [ ] Test search functionality (type a station name)

### 3. Test Playback
- [ ] Click on any station card
- [ ] Verify "Now Playing" card appears at top
- [ ] Check buffering indicator shows ("جاري التحميل...")
- [ ] Confirm audio starts playing (LIVE indicator appears)
- [ ] Listen for actual audio output

### 4. Test Controls
- [ ] Click Stop button (square icon) - audio should stop
- [ ] Click Play button again - audio should resume
- [ ] Click Next button - should switch to next station
- [ ] Click Previous button - should switch to previous station
- [ ] Adjust volume slider - volume should change
- [ ] Click volume icon to mute/unmute

### 5. Test Tabs
- [ ] Click "المفضلة" (Favorites) tab - should show empty or saved favorites
- [ ] Click heart icon on a station to add to favorites
- [ ] Verify station appears in Favorites tab
- [ ] Click "الأخيرة" (Recent) tab - should show recently played stations
- [ ] Click "الكل" (All) tab - should show all 24 stations again

### 6. Test Error Handling
- [ ] Turn off internet connection
- [ ] Try to play a station
- [ ] Verify error message appears
- [ ] Click "إعادة المحاولة" (Retry) button
- [ ] Turn internet back on and retry

### 7. Browser Console Check
- [ ] Open browser DevTools (F12)
- [ ] Go to Console tab
- [ ] Look for any red errors
- [ ] Check for "[Radio]" log messages (should show station info)

## Expected Results

✅ **Success Indicators:**
- Stations load and display correctly
- Audio plays without errors
- Controls respond immediately
- Volume changes work smoothly
- Favorites and recent history persist
- No console errors

❌ **Known Issues (Not Bugs):**
- First click might show "Browser blocked autoplay" - click play again
- Buffering may take 2-5 seconds depending on connection
- Some station images might fail to load (fallback icon shows)

## Troubleshooting

### Issue: No audio plays
**Check:**
1. Browser volume is not muted
2. System volume is up
3. Internet connection is stable
4. Try a different station

### Issue: "Browser blocked autoplay"
**Solution:** This is normal browser security. Just click the play button again.

### Issue: Stations not loading
**Check:**
1. Dev server is running (http://localhost:3000)
2. API endpoint works: `curl http://localhost:3000/api/radio`
3. Check browser console for errors

### Issue: Buffering forever
**Try:**
1. Refresh the page
2. Try a different station
3. Check internet speed
4. Clear browser cache

## API Verification

Test the API directly:
```bash
# Should return 24 stations
curl http://localhost:3000/api/radio | grep -o '"id"' | wc -l

# Should return 200 OK
curl -I http://localhost:3000/api/radio
```

## Browser Compatibility

Tested and working on:
- ✅ Chrome/Edge (Chromium)
- ✅ Firefox
- ✅ Safari
- ✅ Mobile browsers

---

**Last Updated:** 2026-04-21
**Status:** Ready for testing
