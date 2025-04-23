# Discord Stepn Marketplace Price Alerts

A Python bot designed to monitor the Stepn marketplace and send price alerts directly to Discord.

## Rust Library: `stepn-password`

This project includes a Rust library, `stepn-password`, which is a fork of [Numenorean/stepn-password](https://github.com/Numenorean/stepn-password). It is used for secure password hashing and encoding.

## Build Instructions

To build the Rust library and set up the Python environment, follow these steps:

1. Install `virtualenv`:
   ```bash
   pip3 install virtualenv
   ```

2. Create and activate a virtual environment:
   ```bash
   virtualenv venv
   source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
   ```

3. Install the required Python dependencies:
   ```bash
   pip3 install -r requirements.txt
   ```

4. Build the Rust library using `maturin`:
   ```bash
   maturin develop
   ```

## Dependencies

- **Rust**: Required for building the `stepn-password` library.
- **Python**: Version 3.10 or higher.

## Example `secrets.py`

Below is an example of the `secrets.py` file required for the bot to function. Replace the placeholders with your actual credentials and configuration:

```python
ID = "1000000000000000000"  # Discord bot ID
TOKEN = "..."  # Discord bot token
PUBLIC = "..."  # Discord bot public key

STEPN_ACCOUNT = "user@mail.com"  # Stepn account email
STEPN_PASSWORD = "password"  # Stepn account password

RULES = [
    {
        "title": "Any shoes under 2 $GMT",
        "conditions": "%sellPrice < 2000000",
        "params": {
            "order": mapping_order["lowest_price"],
            "chain": mapping_chain["sol"],
            "refresh": "true",
            "page": 0,
            "type": mapping_type["sneakers_all"],
        },
        "page_end": 0,
        "limit": 2,
    },
    {
        "title": "Shoes with at least luck > 10",
        "conditions": "%sellPrice < 1500000",
        "conditions_on_stats": "%attr.Luck > 100",
        "params": {
            "order": mapping_order["lowest_price"],
            "chain": mapping_chain["sol"],
            "refresh": "true",
            "page": 0,
            "type": mapping_type["sneakers_all"],
        },
        "page_end": 0,
        "limit": 3,
    },
]
```

## Public Bot Usage

To use the bot with your Discord server:

1. Create a role named `stepnwatcher`.
2. Create a channel named `stepn-marketplace`.
3. Invite the bot to your server using the following link:
   ```
   https://discord.com/api/oauth2/authorize?client_id=1000748328490893422&permissions=154890923024&scope=bot
   ```
   Ensure the bot has the minimum permissions required for writing messages and managing roles.

## Features

- Alerts for Stepn marketplace price changes.
- Configurable rules for monitoring specific conditions (e.g., price thresholds, attributes like "Luck").
- Discord integration for seamless notifications.

## Future Enhancements

If time permits, a dashboard will be developed to allow users to customize their alerts directly.

## License

This project is licensed under the [GNU General Public License v3.0](LICENSE).