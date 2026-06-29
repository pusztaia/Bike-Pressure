# Bicycle Tire Pressure Calculator

A single-file, mobile-first bicycle tire pressure calculator designed for iPhone use. The calculator answers one practical question:

**How much should I pump the tires in the garage so that the pressure is correct outside at the riding temperature?**

## Main Purpose

A floor pump shows gauge pressure: the pressure relative to atmospheric pressure. The tire, however, may be pumped in a warmer or colder garage and then ridden outside at a different temperature.

For that reason, the calculator first estimates the desired **outside goal** pressure, then converts that target into the required **pump garage** pressure.

Temperature correction is calculated using absolute pressure:

```js
garagePSI = (outsideTargetPSI + 14.7) * (garageKelvin / outsideKelvin) - 14.7
```

This matters because the ideal gas law relates absolute pressure and absolute temperature, while a bicycle pump displays gauge pressure. The `14.7 PSI` offset approximates atmospheric pressure at sea level.

## How to Use

1. Open `index.html` in Safari or another modern browser.
2. Select the bike profile.
3. Check the tire model, tire width, wheelset, rim type, and rider/gear weight.
4. Enter:
   - **Outside °C**: expected outdoor riding temperature.
   - **Garage °C**: temperature where you inflate the tires.
5. Read the **Pressure Result** section:
   - **Pump garage**: set your pump to this pressure indoors.
   - **Outside goal**: expected/desired pressure outside.

## Default Bike Profiles

| Bike | Weight | Wheelset | Rim | Tire | Size | Weight distribution |
|---|---:|---|---|---|---:|---|
| BMC Alpenchallenge 01 THREE | 9.6 kg | DT SWISS C 1800 SPLINE 23 DB | Hooked, 22 mm | Panaracer Gravelking Slick TLC | 32c | Fitness, 43/57 |
| Giant TCR Adv 0 Di2 2025 | 7.6 kg | Giant/CADEX SLR 0 | Hookless, 22.4 mm | CADEX Race GC | 28c | Road Race, 44/56 |
| TCR Advanced 2022 | 8.4 kg | DT Swiss PR 1600 32 | Hooked, 18 mm | Giant Gavia Course | 28c | Road Race, 44/56 |

## What the Calculator Considers

- Rider weight
- Bike weight
- Gear weight
- Front/rear weight distribution
- Tire width
- Tire model maximum pressure
- Rim type: hooked or hookless
- Inner rim width
- Surface type
- Comfort/speed preference
- Garage temperature
- Outside temperature

## Safety Limits

The calculator always applies a safety ceiling:

```js
safeMax = Math.min(rimLimit, tireRatedMax)
```

For hookless wheels, the current configuration uses a 73 PSI maximum limit. For hooked rims, the rim allows higher pressure, but the tire's own rated maximum pressure still applies.

Always obey the lower limit between the tire and rim manufacturer specifications.

## Pressure Result Display

The result section is intentionally simple:

- **Front** and **Rear** are shown separately.
- Each wheel shows two main values:
  - **Pump garage**: pressure to set on the pump indoors.
  - **Outside goal**: target/expected pressure outside.
- PSI is shown as the primary value.
- Bar is shown as a smaller secondary value.
- A short temperature-correction note explains the adjustment.

## Chart

The embedded Chart.js graph shows how the expected outside pressure changes across different outdoor temperatures, starting from the same garage inflation pressure.

## iPhone Optimization

The page is optimized for both iPhone 16 Pro Max and iPhone 13 mini:

- `viewport-fit=cover`
- Safe area inset handling for Dynamic Island, notch, and home indicator
- Input font size of 16 px or larger to avoid automatic iOS zoom
- Larger touch targets
- Simplified mobile pressure result layout
- Fewer chart ticks and reduced animation on smaller iPhones
- Chart resize after orientation changes

## Technology

- HTML
- CSS
- JavaScript
- Embedded Chart.js 4.4.1
- No build step
- No backend
- No installation required

## Customization

Bike, wheelset, tire, and pressure-limit data can be edited directly in the JavaScript section of `index.html`.

### Bikes

```js
const bikes = {
  'bmc_ac01': {
    name: 'BMC Alpenchallenge 01 THREE',
    weight: 9.6,
    defaultWheel: 'dtc1800',
    distroProfile: 'fitness',
    defaultTire: 'panaracer_gravelking_slick',
    defaultTireWidth: 32
  }
};
```

### Wheelsets

```js
const wheelsets = {
  'dtc1800': { type: 'hooked', limit: 110, name: 'Hooked Rim', w: 22 },
  'slr0': { type: 'hookless', limit: 73, name: 'Hookless', w: 22.4 }
};
```

### Tire Maximum Pressures

```js
const tireMaxPressure = {
  panaracer_gravelking_slick: 75,
  cadex_race: 95,
  giant_gavia_course: 105
};
```

## Important Note

This calculator provides an estimate. It does not replace official safety instructions from tire and rim manufacturers.

Always check the official maximum pressure for both the tire and the rim. Use the lower of the two. For hookless systems, also confirm that the tire is approved for hookless use.

## Background / References

- WebKit: `viewport-fit=cover` and safe area inset handling for modern iPhone displays.
- Apple Safari Web Content Guide: viewport configuration for iOS Safari.
- OpenStax College Physics: ideal gas law and pressure-temperature relationship examples.
- Arden tire pressure calculator explanation: gauge pressure to absolute pressure conversion using an atmospheric pressure offset.
- SRAM/Zipp tire pressure guidance: common inputs for modern bicycle tire pressure calculators, including rider/bike/gear weight, tire width, rim type, and inner rim width.

## Files

- `index.html` - the calculator.
- `README.md` - this documentation.
