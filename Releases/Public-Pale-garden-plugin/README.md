PaleGarden Plugin Documentation

Version: 1.0.0
Author: _TekkSchuster_
License: _TekkSchuster_ Proprietary License
Copyright: 2025 _TekkSchuster_. All rights reserved.

================================================================================

TABLE OF CONTENTS

1. Overview
2. Installation
3. Features
4. Commands
5. Permissions
6. Configuration
7. Gameplay Mechanics
8. Discord Integration
9. Troubleshooting
10. License and Legal

================================================================================

OVERVIEW

PaleGarden is a hardcore Minecraft plugin that transforms your server into a challenging survival experience. The plugin converts worlds to the Pale Garden biome, introduces powerful Cursed Blades with unique mechanics, implements a hardcore death system, and provides comprehensive tracking and notification systems.

Key Features:
- World Conversion: Automatically converts biomes to Pale Garden
- Cursed Blades: Special diamond swords with unique properties
- Hardcore Death System: 24-hour bans upon death
- Tracking System: Compass-based player tracking
- Discord Integration: Real-time notifications
- Container Restrictions: Advanced item protection

================================================================================

INSTALLATION

Requirements:
- Minecraft Version: 1.21+
- Server Software: Bukkit/Spigot/Paper
- Java Version: 17+
- Dependencies: None

Installation Steps:

1. Download the pale-garden-plugin-1.0.0.jar file
2. Stop your Minecraft server
3. Place the JAR file in your server's plugins/ directory
4. Start your server
5. Configure the plugin using the generated config.yml
6. Restart the server to apply changes

First-Time Setup:

1. Edit plugins/PaleGarden/config.yml with your Discord webhook URL
2. Adjust hardcore ban duration if desired (default: 24 hours)
3. Set maximum Cursed Blade count (default: 2)
4. Configure world conversion settings
5. Restart the server

================================================================================

FEATURES

Cursed Blades:

Properties:
- Material: Diamond Sword (unbreakable)
- Enchantments: Sharpness VI, Fire Aspect II
- Visual: Dynamic texture switching every 5 seconds
- Unique ID: Each blade has a unique identifier
- Maximum Count: Configurable (default: 2)

Restrictions:
- Cannot be stored in Ender Chests
- Cannot be moved by hoppers or automation
- Cannot be placed in chests below Y-level 60
- Cannot be stored in Shulker Boxes or Barrels

Hardcore Death System:

- Death Ban: Players are banned for 24 hours upon death
- Ban Message: Customizable death notification
- Early Unban: Admins can unban players early
- Grace Period: Recently unbanned players have protection

World Conversion:

- Biome Change: Converts world biomes to Pale Garden
- Mountain Preservation: Keeps mountain biomes unchanged
- Hardcore Mode: Forces world to hardcore difficulty

Tracking System:

- Compass Tracking: Players can track Cursed Blade holders
- Eligibility: Available after 7 hours of blade possession
- Single Use: Each compass is used once per eligibility
- Real-time Updates: Compass points update every 5 seconds

================================================================================

COMMANDS

Player Commands:

/findblade
Description: Obtain a tracking compass to locate Cursed Blade holders
Permission: None (available to all players)
Usage: /findblade
Cooldown: Single use per eligibility period

Requirements:
- A player must have held a Cursed Blade for 7+ hours
- You must not have used your compass for the current eligible player

Example:
/findblade
> You have received a tracking compass pointing to PlayerName!

Admin Commands:

/palegarden
Description: Main admin command for plugin management
Permission: palegarden.admin
Usage: /palegarden <subcommand>

Subcommands:

/palegarden reload
Description: Reload plugin configuration
Usage: /palegarden reload
Example:
/palegarden reload
> Configuration reloaded!

/palegarden give
Description: Give a Cursed Blade to yourself
Usage: /palegarden give
Note: Only works if under maximum blade count
Example:
/palegarden give
> Given you a Cursed Blade!

/palegarden status
Description: Check current Cursed Blade count
Usage: /palegarden status
Example:
/palegarden status
> Cursed Blades: 1/2

/palegarden unban <player>
Description: Unban a player early from hardcore death
Usage: /palegarden unban <playername>
Example:
/palegarden unban Steve
> Player 'Steve' has been unbanned!

================================================================================

PERMISSIONS

Admin Permissions:

palegarden.admin - Access to all admin commands (OP only)

Player Permissions:

None required - /findblade command access (All players)

================================================================================

CONFIGURATION

Discord Integration:

discord:
  webhook-url: "YOUR_DISCORD_WEBHOOK_URL"
  enabled: true

Setup Instructions:
1. Create a Discord webhook in your server
2. Copy the webhook URL
3. Paste it in the config file
4. Set enabled: true
5. Restart the server

Cursed Blade Settings:

special-item:
  max-count: 2                    # Maximum blades in world
  spawn-rate: 0.25               # Spawn chance (25%)
  texture-change-interval: 100   # Texture change (5 seconds)
  min-chest-y: 60               # Minimum Y for chest storage
  inactivity-hours: 30          # Hours before blade respawns
  compass-tracking-hours: 7     # Hours before tracking available

Hardcore System:

hardcore:
  ban-duration-hours: 24
  ban-message: "You died in hardcore mode! You will be unbanned in 24 hours."
  death-message: "%player% has fallen in the pale garden and been banished for 24 hours!"

World Settings:

world:
  force-hardcore: true           # Enable hardcore mode
  convert-to-pale-garden: true   # Convert biomes
  preserve-mountain-biomes: true # Keep mountains

Container Restrictions:

item-restrictions:
  blocked-containers:
    - "ENDER_CHEST"
    - "SHULKER_BOX"
    - "BARREL"
    - "CHEST_BELOW_Y"
  prevent-hopper-interaction: true
  prevent-automation-pickup: true
  prevent-item-throwing: false

================================================================================

GAMEPLAY MECHANICS

Cursed Blade Lifecycle:

1. Spawning: Blades spawn based on configured spawn rate
2. Acquisition: Players can pick up blades (notifications sent)
3. Tracking: After 7 hours, other players can track the holder
4. Inactivity: If holder is inactive for 30 hours, blade becomes available
5. Destruction: If blade is destroyed, notifications are sent

Death and Banning:

1. Player Dies: Death is detected by the plugin
2. Ban Applied: Player is banned for configured duration
3. Notifications: Discord and in-game notifications sent
4. Grace Period: Upon unban, player has temporary protection

Tracking System:

1. Eligibility: Player holds blade for 7+ hours
2. Notification: Server notified that tracking is available
3. Compass Request: Other players use /findblade
4. Tracking: Compass points to blade holder in real-time
5. Single Use: Each compass works once per eligibility

================================================================================

DISCORD INTEGRATION

Notification Types:

Event                | Discord Message                        | In-Game Message
Blade Pickup         | Player has claimed a Cursed Blade!    | Player has claimed a Cursed Blade!
Blade Spawn          | A new Cursed Blade has spawned!       | A new Cursed Blade has materialized!
Tracking Available   | Player held blade for 7 hours!        | Player has held blade for 7 hours!
Blade Destroyed      | A Cursed Blade has been destroyed!    | A Cursed Blade has been lost!
Player Death         | Player died and was banned!           | Player has fallen and been banished!

Webhook Setup:

1. Discord Server: Go to your Discord server
2. Channel Settings: Right-click channel and select Edit Channel
3. Integrations: Go to Integrations tab
4. Webhooks: Click Create Webhook
5. Configure: Set name and avatar
6. Copy URL: Copy the webhook URL
7. Plugin Config: Paste URL in config.yml

================================================================================

TROUBLESHOOTING

Common Issues:

Plugin Not Loading:
Symptoms: Plugin doesn't appear in /plugins list
Solutions:
- Check server console for errors
- Verify Minecraft version compatibility (1.21+)
- Ensure Java 17+ is installed
- Check file permissions

Discord Notifications Not Working:
Symptoms: No messages in Discord channel
Solutions:
- Verify webhook URL is correct
- Check discord.enabled: true in config
- Test webhook URL manually
- Restart server after config changes

Cursed Blades Not Spawning:
Symptoms: No blades appear in world
Solutions:
- Check special-item.max-count setting
- Verify special-item.spawn-rate (0.0-1.0)
- Use /palegarden give to test
- Check console for errors

Commands Not Working:
Symptoms: Unknown command or permission errors
Solutions:
- Verify player has palegarden.admin permission
- Check command syntax: /palegarden <subcommand>
- Restart server if commands aren't registered

Tracking Compass Not Working:
Symptoms: /findblade says not eligible
Solutions:
- Verify someone has held blade for 7+ hours
- Check compass-tracking-hours setting
- Ensure tracking.compass-enabled: true
- Player may have already used compass for current eligible holder

Debug Mode:

Enable debug mode for detailed logging:

debug:
  enabled: true
  log-item-events: true
  log-tracking-events: true
  log-container-events: true

Log Files:

Check these locations for error information:
- logs/latest.log - Server console output
- plugins/PaleGarden/ - Plugin data files

================================================================================

LICENSE AND LEGAL

Copyright Notice:

_TekkSchuster_ PROPRIETARY LICENSE
Version 1.0 – 2025
Copyright (c) 2025 _TekkSchuster_. All rights reserved.

This License Agreement (“Agreement”) governs the use of the PaleGarden Plugin (“Software”) developed by _TekkSchuster_.

By installing, copying, or using the Software, you accept and agree to be bound by the terms of this Agreement. If you do not agree to these terms, you must not use the Software.

---

1. Ownership

All rights, title, and interest in the Software, including all intellectual property rights, remain the exclusive property of _TekkSchuster_. This Agreement does not grant any ownership rights to the user.

---

2. Grant of License

You are granted a limited, non-exclusive, non-transferable, and non-sublicensable license to use the Software solely for personal or non-commercial Minecraft server use.

---

3. Restrictions

You may not, under any circumstances:

a) Redistribute, resell, sublicense, rent, or publicly share the Software
b) Modify, decompile, disassemble, reverse engineer, or attempt to derive the source code
c) Claim ownership, authorship, or originate derivative works based on the Software
d) Remove or obscure any copyright, trademark, or proprietary notices
e) Circumvent any rules or restrictions defined by _TekkSchuster_ for the Software’s use in gameplay or server behavior
f) Store the Software or any associated elements in restricted containers as defined by event rules (including but not limited to ender chests, shulker boxes, hoppers, or barrels)

---

4. Termination

This License terminates immediately upon breach of any term. Upon termination, you must cease all use of the Software and delete all copies in your possession or control.

---

5. Disclaimer of Warranty

The Software is provided “AS IS” without any warranties, express or implied. This includes but is not limited to warranties of merchantability, fitness for a particular purpose, or non-infringement.

---

6. Limitation of Liability

Under no circumstances shall _TekkSchuster_ be held liable for any damages or losses arising from the use, misuse, or inability to use the Software. This includes, without limitation:

* Data loss
* Server failures or downtime
* Player account issues
* Conflicts with third-party plugins or modifications

Furthermore, _TekkSchuster_ is not responsible for any consequences resulting from modified, redistributed, or tampered versions of the Software by third parties. Use of such unauthorized versions is strictly at the user’s own risk.
All liability for any misuse of the Software, whether intentional or accidental, lies entirely with the user or operator.

---

7. Governing Law and Jurisdiction

This Agreement shall be governed by and construed in accordance with the laws of the Federal Republic of Germany. Any disputes arising from or related to this License shall be subject to the exclusive jurisdiction of the competent courts in Germany.

---

8. Contact

For licensing questions, permissions beyond the scope of this License, or legal inquiries, please contact _TekkSchuster_ directly via Discord.

---

9. Verification and Distribution

The Software is **only officially distributed through _TekkSchuster_ Discord server**. Any copy of the Software obtained from a different source must be considered unauthorized.

To ensure file integrity and authenticity:

* All official releases are **digitally signed** using _TekkSchuster_ private key.
* Each release includes a **SHA-256 checksum** posted alongside the official file.
* Users are encouraged to **verify the SHA Checksum** and confirm that the hash matches the one published by _TekkSchuster_.

Instructions and verification information are available in the designated release channels on Discord.

_TekkSchuster_ accepts no responsibility or liability for the use of any unofficial, modified, or redistributed versions of the Software.


================================================================================

2025 _TekkSchuster_. All rights reserved. PaleGarden Plugin is proprietary software owned by _TekkSchuster_.
