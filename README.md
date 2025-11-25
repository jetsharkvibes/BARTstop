# BARTstop - TRMNL Plugin

A TRMNL e-ink display plugin that shows real-time train arrivals at any BART (Bay Area Rapid Transit) station.

![Full](https://github.com/jetsharkvibes/BARTstop/blob/main/BARTstop.png)

## Features

- **Real-time arrivals** for any BART station
- **Train line indicators** showing destination abbreviations (RICH, MLBR, DUBL, etc.)
- **Smart filtering** - filter by direction and/or specific train lines
- **Customizable badges** - show platform, bike availability, delays, and cancellations (full and half_vertical layouts)
- **Multiple layout options** for different TRMNL screen sizes
- **Zero infrastructure** - no backend server required, calls BART API directly
- **Store-ready** - optimized with 6 or fewer inline styles per template

## Layouts

![Vertical and Quad](https://github.com/jetsharkvibes/BARTstop/blob/main/mash_up.png)

Choose from 4 responsive layouts:

### Full (4-column grid)
Best for: Full-screen displays showing up to 12 trains
- Large time display (1.9em)
- Detailed train info with customizable badges (platform, bike, delay, cancel)
- Shows first train for each unique line, then fills remaining slots

### Half Horizontal (2x2 grid)
Best for: Horizontal half-screen displays showing up to 4 trains
- Compact horizontal layout with destination and times
- Sans-serif time display for clarity
- Smart filter display in titlebar

### Half Vertical (2-column grid)
Best for: Vertical half-screen displays showing up to 6 trains
- Vertical stack with customizable badges
- Optimized for tall, narrow displays
- Same badge options as Full layout

### Quadrant (vertical stack)
Best for: Quarter-screen displays showing 2 trains
- Clean horizontal card layout (destination left, times right)
- Sans-serif time display
- Maximum 2 train cards to fit small space

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
- Select **North** for northbound trains only
- Select **South** for southbound trains only
- Filters appear in titlebar when active

**Train Line Filter** (optional, multi-select)
- Default: **No filters** (shows all train lines)
- Select specific lines to show only those trains (RICH, MLBR, DUBL, etc.)
- Filters display in titlebar only when actively filtering trains
- Combine with Direction filter for precise control

**Badge Visibility** (optional, multi-select, full and half_vertical layouts only)
- Default: **All badges enabled** (platform, bike, delay, cancel)
- **Platform**: Shows platform number (e.g., "PLAT 1")
- **Bike**: Shows if train allows bikes (highlighted when available)
- **Delay**: Shows if train is delayed (highlighted when delayed)
- **Cancel**: Shows if train is cancelled (highlighted when cancelled)
- Select **No badges** to hide all badges

### 3. Refresh Interval

Default: 30 seconds (recommended)
- BART API updates every 20-30 seconds
- Faster refresh = more current data, but more API calls

## Filtering & Display

### Smart Filter Display
Filters only appear in the titlebar instance when they're actively filtering trains:
- **Direction only**: Shows "North" or "South"
- **Lines only**: Shows line abbreviations (e.g., "RICH,MLBR")
- **Both**: Shows both separated by · (e.g., "North · RICH,MLBR")
- **No filters/All trains shown**: Shows only direction (or nothing if no direction set)

This smart display ensures you always know when filters are active without cluttering the interface.

## Available Train Lines

Select from these train lines in the filter (or choose "No filters" to show all):

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

## Available Badges

For **full** and **half_vertical** layouts, choose which information badges to display:

| Badge | Description | When Highlighted |
|-------|-------------|------------------|
| **Platform** | Shows platform number | Always shown (e.g., "PLAT 1") |
| **Bike** | Bike availability | When bikes are allowed on train |
| **Delay** | Train delay status | When train is delayed |
| **Cancel** | Cancellation status | When train is cancelled |

**Note**: Badges are not available on quadrant and half_horizontal layouts due to space constraints.

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

### v1.1.0 (2025-01-23)
- Added smart train line filtering (filter by specific lines)
- Added customizable badge visibility (platform, bike, delay, cancel)
- Moved filters to titlebar instance for cleaner display
- Updated quadrant and half_horizontal layouts to horizontal card design
- Changed half_horizontal to 2x2 grid layout
- Unified time fonts to sans-serif across layouts
- Smart filter display (only shows when actively filtering)
- Improved direction field (North/South instead of n/s)

### v1.0.0 (2025-01-18)
- Initial release
- 4 responsive layouts (full, half_horizontal, half_vertical, quadrant)
- Real-time train arrivals with line indicators
- Direction filtering support
- Store-ready optimization (≤6 inline styles per template)


