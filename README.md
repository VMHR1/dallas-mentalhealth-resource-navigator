# mental-health-resource-navigator
Neutral post-discharge mental health resource navigator for Dallas-FortWorth area youth

## Mobile Performance

This application is optimized for mobile performance with comprehensive monitoring and optimization tools.

### Quick Start - Performance Testing

1. **Enable performance monitoring**: Add `?perf=1` to any URL
   - Example: `https://your-site.com/?perf=1`
   - Shows real-time FPS, jank count, and performance metrics

2. **Test with kill switches**: Isolate performance issues
   - `?perf=1&noAnim=1` - Disable animations
   - `?perf=1&noShadow=1` - Remove shadows
   - `?perf=1&noFixedBg=1` - Hide fixed background

3. **Check console logs**: Every 10 seconds, detailed metrics are logged

### Mobile Performance Policy

On mobile/coarse pointer devices:
- ✅ No infinite background animations
- ✅ No moving shadow animations  
- ✅ Simplified shadows and backdrop-filters
- ✅ Content-visibility optimizations for offscreen content
- ✅ GPU-optimized sticky elements

**Full documentation**: See [MOBILE_PERFORMANCE.md](./MOBILE_PERFORMANCE.md) for complete details.

## Geocoding for Distance Features

The "Near Me" feature requires geocoded location data. To generate it:

```bash
node scripts/geocode-programs.js
```

This will:
- Read `programs.json`
- Geocode all program addresses using Nominatim OpenStreetMap (free, open-source)
- Generate `programs.geocoded.json` with latitude/longitude coordinates
- Respect rate limits (1 request/second as required by Nominatim ToS)

**Note:** The geocoding script uses Nominatim, which requires:
- Proper User-Agent header (included)
- Rate limiting (1 req/sec, enforced)
- Attribution: © OpenStreetMap contributors

After generating, commit and push `programs.geocoded.json` to make distance sorting available to all visitors.
