# DataCEVA US Layoff Notices

Research U.S. layoffs and plant closings with Claude, using WARN Act notices: the advance notices employers must
file with the state before larger layoffs and closures. DataCEVA collects the notices published by 46 states and
Washington, D.C., standardizes them and refreshes them daily.

This plugin adds three skills on top of DataCEVA's read-only layoff notices connector, so Claude follows the same
careful steps every time: it checks which states are covered, cites the state agency for each notice, gives the
date the data is current to, and says what the data can't show.

## Skills

| Skill | Use it for | Example |
|---|---|---|
| Company layoff brief | One employer's WARN history as a sourced briefing: totals by year and state, latest notices with details | "Is Intel laying people off?" |
| Local layoff scan | Recent notices near a city or ZIP, or in a state or region, with the industry mix and a comparison with the period before | "Which employers near Milwaukee, WI filed layoff notices this month?" |
| Layoff trend analysis | Trends and rankings by period, state, region, industry or company, compared fairly | "Are manufacturing layoffs rising in the Midwest?" |

Ask in plain language; Claude picks the skill that fits.

## Setup

1. Install the plugin from Claude's plugin directory: in Claude, open **Customize > Plugins** and search for
   **DataCEVA US Layoff Notices**. In Claude Code, run `/plugin` and search for the same name.
2. Connect its **DataCEVA US Layoff Notices** connector from the plugin's Connectors tab (in Claude Code it
   connects automatically). No account or sign-in is needed.

If you already use the DataCEVA US Layoff Notices connector from the directory, it is the same server, so you get
one set of tools, not two.

## Data and privacy

- The plugin itself stores nothing and runs no code; it contains instructions (skills) and the connector's
  address.
- When Claude uses the connector, it sends only search details (for example a company name, place, state,
  industry or dates) to DataCEVA's server at `https://dc-ai-plugin-layoff-notices-mcp.onrender.com/mcp`. It
  sends nothing anywhere else.
- The notices are public records from state workforce agencies. They describe employers, not individual
  employees.
- Privacy policy: https://dc-ai-plugin-layoff-notices-mcp.onrender.com/privacy
- Terms: https://dc-ai-plugin-layoff-notices-mcp.onrender.com/terms

## Limits

WARN covers larger layoffs only (generally 50 or more workers at one site), so it is a floor, not a count of all
job losses. Arkansas, Wyoming and New Hampshire don't publish notices, and Ohio is temporarily unavailable; a few
states are updated in part or from saved history only. Industry is reported by some states only, and locations
are approximate. See which states are covered: https://dc-ai-plugin-layoff-notices-mcp.onrender.com/coverage

## Support

Help: https://dc-ai-plugin-layoff-notices-mcp.onrender.com/docs · Email: access@dataceva.com ·
Built by [DataCEVA](https://www.dataceva.com), Chicago.

## License

MIT. See `LICENSE`.
