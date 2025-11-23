# BARTstop - TRMNL Plugin

A TRMNL e-ink display plugin that shows real-time train arrivals at any BART (Bay Area Rapid Transit) station.

![Full](https://github.com/jetsharkvibes/BARTstop/blob/main/BARTstop.png)

## Features

- **Real-time arrivals** for any BART station
- **Train line indicators** showing destination abbreviations (RICH, MLBR, DUBL, etc.)
- **Direction filtering** (optional) to show only northbound or southbound trains
- **Multiple layout options** for different TRMNL screen sizes
- **Zero infrastructure** - no backend server required, calls BART API directly
- **Store-ready** - optimized with 6 or fewer inline styles per template

## Layouts

![Vertical and Quad](https://github.com/jetsharkvibes/BARTstop/blob/main/mash_up.png)

Choose from 4 responsive layouts:

### Full (3-column grid)
Best for: Full-screen displays showing 3 upcoming trains
- Large time display (2.6em)
- Detailed train info including platform and bike availability

### Half Horizontal (4-column grid)
Best for: Horizontal half-screen displays showing 4 upcoming trains
- Compact design with abbreviated labels
- Efficient use of horizontal space

### Half Vertical (Vertical stack)
Best for: Vertical half-screen displays showing 4 upcoming trains
- Tight vertical spacing
- Optimized for tall, narrow displays

### Quadrant (2-column grid)
Best for: Quarter-screen displays showing 2 upcoming trains
- Medium time display (1.9em)
- Balanced information density

## Setup

### 1. Add to TRMNL

1. Go to your TRMNL dashboard
2. Click "Add Plugin"
3. Paste the GitHub repository URL: `https://github.com/jetsharkvibes/BARTstop`
4. Select your preferred layout template
5. Configure your settings (see below)

### 2. Configuration

**BART Station** (required)
- Select your station from the dropdown (all 50+ BART stations supported)
- Uses official BART station codes (12TH, EMBR, MONT, etc.)

**Direction** (optional)
- Leave blank for all trains
- Select `n` for northbound trains only
- Select `s` for southbound trains only

### 3. Refresh Interval

Default: 30 seconds (recommended)
- BART API updates every 20-30 seconds
- Faster refresh = more current data, but more API calls

## Train Line Abbreviations

The plugin shows abbreviated train destinations:

| Abbreviation | Destination |
|--------------|-------------|
| RICH | Richmond |
| MLBR | Millbrae |
| DUBL | Dublin/Pleasanton |
| BERY | Berryessa/North San José |
| DALY | Daly City |
| WARM | Warm Springs/South Fremont |
| ANTC | Antioch |
| PITT | Pittsburg/Bay Point |
| SFIA | SFO International Airport |
| OAKL | Oakland Airport |

## Technical Details

### API Integration
- **Endpoint**: BART Real-Time ETD (Estimated Time of Departure) API
- **Format**: JSON
- **Authentication**: Public API key (MW9S-E7SL-26DU-VV8V)
- **Rate limiting**: Respectful polling every 30 seconds

### Code Quality
- **Inline styles**: 2-3 per template (well under TRMNL's 6-style limit)
- **Framework**: TRMNL v2 with utility-first CSS classes
- **Templating**: Liquid (Shopify template language)
- **Responsive**: Adapts to 1-bit through 4-bit e-ink displays

### Data Processing
- Converts PST/PDT timezone automatically
- Handles "Leaving" and "Now" states for imminent departures
- Shows platform numbers and direction when available
- Indicates bike-friendly trains (full layout only)

## Error Handling

If no trains are available:
- Displays ⚠️ warning emoji
- Shows "No trains available" message
- Automatically recovers when service resumes

## License

Public Domain - feel free to modify and distribute

## Credits

- Created by jetsharkvibes
- Inspired by [BARTcom-TRMNL](https://github.com/jetsharklambo/BARTcom-TRMNL)
- BART API provided by [Bay Area Rapid Transit](https://www.bart.gov/)
- Built for [TRMNL](https://usetrmnl.com/)

## Support

For issues or feature requests, please open an issue on GitHub:
https://github.com/jetsharkvibes/BARTstop/issues

## Version History

### v1.0.0 (2025-01-18)
- Initial release
- 4 responsive layouts (full, half_horizontal, half_vertical, quadrant)
- Real-time train arrivals with line indicators
- Direction filtering support
- Store-ready optimization (≤6 inline styles per template)


