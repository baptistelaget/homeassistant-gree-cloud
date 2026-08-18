# Quick Start Guide

Get your cloud-only Gree devices working with Home Assistant in 5 minutes!

## Prerequisites

- ✅ Home Assistant 2024.1.0 or later
- ✅ Gree+ app account with registered devices
- ✅ Devices connected to WiFi and working in Gree+ app
- ✅ Internet connection (required for cloud communication)

## Step 1: Install the Integration

### Option A: HACS (Recommended)

1. Open **HACS** in Home Assistant
2. Click **Integrations**
3. Click the **⋮** menu (top right) → **Custom repositories**
4. Add repository URL: `https://github.com/baptistelaget/homeassistant-gree-cloud`
5. Category: **Integration**
6. Click **Add**
7. Find **Gree Climate Cloud** in HACS and click **Download**
8. **Restart Home Assistant**

### Option B: Manual Installation

1. Download the latest release from GitHub
2. Extract and copy `custom_components/gree_cloud` to your Home Assistant `config/custom_components/` directory
3. **Restart Home Assistant**

## Step 2: Add the Integration

1. Go to **Settings** → **Devices & Services**
2. Click **+ Add Integration** (bottom right)
3. Search for **"Gree Climate Cloud"**
4. Select your **Server Region** (e.g., Europe)
5. Enter your **Gree+ username** (email)
6. Enter your **Gree+ password**
7. Click **Submit**

### Finding Your Server Region

Not sure which region? Try these:
- 🇪🇺 **Europe** - Most European countries
- 🇺🇸 **North American** - USA, Canada
- 🇦🇺 **Australia** - Australia, New Zealand
- 🇨🇳 **China Mainland** - China
- 🌏 **East South Asia** - Hong Kong, Singapore, etc.

## Step 3: Verify Devices

1. Go to **Settings** → **Devices & Services**
2. Click on **Gree Climate Cloud**
3. You should see all your devices listed
4. Click on a device to see its entities:
   - 🌡️ **Climate entity** (main control)
   - 🔘 **Switch entities** (panel light, quiet mode, etc.)

## Step 4: Test Basic Control

1. Go to **Overview** dashboard
2. Find your device's climate card
3. Try these actions:
   - Turn on/off
   - Change temperature
   - Change mode (Cool, Heat, etc.)
   - Change fan speed

💡 **Tip**: Changes may take up to 60 seconds to reflect (cloud polling interval)

## Quick Examples

### Add to Dashboard

```yaml
type: thermostat
entity: climate.your_device_name
```

### Simple Automation - Turn on when home

```yaml
automation:
  - alias: "AC on when home"
    trigger:
      - platform: state
        entity_id: person.your_name
        to: "home"
    action:
      - service: climate.turn_on
        target:
          entity_id: climate.your_device_name
      - service: climate.set_temperature
        target:
          entity_id: climate.your_device_name
        data:
          temperature: 22
```

### Voice Control (Alexa/Google Home)

Just expose the climate entity in **Configuration** → **Alexa/Google Assistant**

Then say:
- "Alexa, turn on Living Room AC"
- "Hey Google, set Living Room AC to 22 degrees"

## Common Issues

### ❌ Login Failed
- Double-check username and password
- Verify server region is correct
- Try logging in to Gree+ app to confirm credentials work

### ❌ No Devices Found
- Ensure devices are online in Gree+ app
- Try removing and re-adding them in Gree+ app
- Check Home Assistant logs for errors

### ❌ Commands Not Working
- Verify device is online in Gree+ app
- Check internet connectivity
- Wait 60 seconds for state to sync

## Need More Help?

- 📖 [Full Documentation](README.md)
- 🤖 [Example Automations](EXAMPLES.md)
- 🐛 [Report an Issue](https://github.com/baptistelaget/homeassistant-gree-cloud/issues)
- 💬 [Troubleshooting Guide](README.md#troubleshooting)

## Next Steps

Once everything is working:

1. **Create automations** - See [EXAMPLES.md](EXAMPLES.md)
2. **Enable debug logging** - For troubleshooting (see README)
3. **Customize dashboard** - Add climate cards, switches, etc.
4. **Set up voice control** - Expose to Alexa/Google Assistant

---

Enjoy controlling your Gree devices! 🎉
