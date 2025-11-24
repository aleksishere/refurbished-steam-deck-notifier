[![Latest Release](https://img.shields.io/github/v/release/oblassgit/refurbished-steam-deck-notifier?include_prereleases)](https://github.com/oblassgit/refurbished-steam-deck-notifier/releases)
[![Python Version](https://img.shields.io/badge/python-3.8%2B-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/github/license/oblassgit/refurbished-steam-deck-notifier)](https://github.com/oblassgit/refurbished-steam-deck-notifier/blob/main/LICENSE)  
[![GitHub Stars](https://img.shields.io/github/stars/oblassgit/refurbished-steam-deck-notifier?style=social)](https://github.com/oblassgit/refurbished-steam-deck-notifier/stargazers)
[![Forks](https://img.shields.io/github/forks/oblassgit/refurbished-steam-deck-notifier?style=social)](https://github.com/oblassgit/refurbished-steam-deck-notifier/network/members)
[![Discord](https://img.shields.io/discord/1142517154370043974?label=Discord&logo=discord&style=flat)](https://discord.gg/5gpFTMkvJn)
[![Ko-fi](https://img.shields.io/badge/Buy%20me%20a%20coffee-Ko--fi-FF5E5B?logo=kofi&logoColor=white&style=flat)](https://ko-fi.com/looti)
# Refurbished Steam Deck Notifier

This script checks the availability of refurbished Steam Decks on Steam and sends notifications to a specified Home Assistant webhook. It queries Steam's API and compares the current stock status with previously stored values.

## 🚀 Features

* Checks the availability of refurbished Steam Decks for a configurable country
* Sends notifications via a **Home Assistant webhook** when stock availability changes
* Supports different Steam Deck models (LCD & OLED versions)
* Prevents duplicate notifications by storing the last known stock status
* **Optional CSV logging** for availability statistics
* **Command-line arguments** for easy configuration

#### How to Run

Run it via terminal/command prompt:

```bash
./steam_deck_notifier --webhook-url "YOUR-WEBHOOK-HERE"
```

You can pass the same arguments as you would for the Python version.

### Option 2: Run the Python Script

```bash
python steam_deck_checker.py --webhook-url "https://homeassistant/api/webhooks/YOUR-WEBHOOK-HERE"
```

### Command Line Arguments

* `-h`: Provides list of possible Arguments
* `--webhook-url`: Home Assistant webhook URL for notifications (**required**)
* `--country-code`: Country code for Steam API (default: `DE`, **important**)
* `--role-mapping`: JSON file containing Discord role mappings (optional)
* `--csv-dir`: Directory path for daily CSV log files (optional)

### Country Codes

Find valid country codes [here](https://github.com/RudeySH/SteamCountries/blob/master/json/countries.json)

## 💪 Steam Deck Models Monitored

The script checks availability for these models:

* **64GB LCD** (Package ID: 903905)
* **256GB LCD** (Package ID: 903906)
* **512GB LCD** (Package ID: 903907)
* **512GB OLED** (Package ID: 1202542)
* **1TB OLED** (Package ID: 1202547)

## ⏲️ Running Periodically

This script/executable **does not run continuously**. Use cron (Linux/macOS) or Task Scheduler (Windows) to automate execution.

### Example (Linux/macOS)

Edit your crontab with:

```bash
crontab -e
```

Add this line to check every 3 minutes:

```bash
*/3 * * * * /path/to/steam_deck_notifier --webhook-url "YOUR_WEBHOOK" >> /path/to/logfile.log 2>&1
```

## 📦 Dependencies & Attribution

This project uses the excellent [**python-discord-webhook**](https://github.com/lovvskillz/python-discord-webhook) library by [lovvskillz](https://github.com/lovvskillz)
Licensed under the MIT License.

It also makes use of Valve’s public Steam Store API — specifically the  
[`CheckInventoryAvailableByPackage`](https://api.steampowered.com/IPhysicalGoodsService/CheckInventoryAvailableByPackage/v1?origin=https:%2F%2Fstore.steampowered.com) endpoint ([documentation](https://steamapi.xpaw.me/#IPhysicalGoodsService)). Data and trademarks belong to [Valve Corporation](https://www.valvesoftware.com/), owners of Steam and Steam Deck.

Big thanks to all contributors and maintainers of the open-source packages used in this project.

## ❤️ Support

If this project helps you, consider supporting via [**Ko-fi**](https://ko-fi.com/Y8Y41BZ8SM)

## 🥇 Special Thanks

Huge thanks to [leo-petrucci](https://github.com/leo-petrucci) for helping improve the codebase and guiding proper Steam API usage!
