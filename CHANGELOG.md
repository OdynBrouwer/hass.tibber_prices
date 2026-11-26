# Changelog

## [0.41.0](https://github.com/OdynBrouwer/hass.tibber_prices/compare/v0.40.0...v0.41.0) (2026-11-26)


### ⚠ BREAKING CHANGES

* **attributes:** templates, automations and dashboards that read an attribute ending in "_%" must use the "_percent" name.
* **periods:** day_price_min, day_price_max and day_price_span of the best/peak price period sensors now use the display unit like price_mean. With prices shown in base currency (€, kr) they read e.g. 0.10 instead of 10; update automations and templates that compare them.
* **trend:** Current Price Trend, Next Price Trend Change and Next Price Trend Change In now follow the trend line, so their states and change times differ from before. previous_direction can also be "stable". Review automations that use these sensors; for "is now cheaper than the next hours?" use the Price Outlook sensors instead.
* **periods:** periods_remaining renamed to period_count_remaining.
* **periods:** periods_found_total removed (replace with period_count_today + period_count_tomorrow). periods_total renamed to period_count_total.
* **migrations:** Duration sensors (remaining time, starts in, period duration, trend change countdown) now report state values in minutes instead of hours. Display unit in dashboards remains hours by default. Update numeric comparisons in automations accordingly.
* **sensors:** State values for all duration sensors change from hours to minutes (e.g. 1.5 → 90). The display unit remains hours (suggested_unit_of_measurement). Automations using numeric state comparisons must be updated (multiply old thresholds by 60).
* **sensors:** Entity ID changes from sensor.<home>_trend_change_in_minutes to sensor.<home>_next_price_trend_change_in. Automations and dashboards referencing the old entity ID must be updated.
* **sensors:** Sensors price_trend_1h, price_trend_2h, price_trend_3h, price_trend_4h, price_trend_5h, price_trend_6h, price_trend_8h, price_trend_12h have been removed without a deprecation period.
* **sensors:** Sensor state unit changes from minutes to hours for users whose entity registry stored "min" as the display unit (the previous default). Automations using the raw state value (e.g., `state < 60` for "less than 60 minutes") must be updated to use hours (e.g., `state < 1`). The state attributes `remaining_minutes` and `next_in_minutes` continue to provide integer minutes and are unaffected.

### 🎉 What's new

* add versioned sidebars for user and developer documentation ([4efd6b7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/4efd6b7267f3855ea6b69dd84843f8574343ee56))
* **api:** add energy and tax fields to Tibber GraphQL queries ([f5dcf04](https://github.com/OdynBrouwer/hass.tibber_prices/commit/f5dcf04aabb2e921c9e59c8845c423d7e51d0367))
* **best_price,peak_price:** add optional extension to VERY_CHEAP/VERY_EXPENSIVE intervals ([b7f1efc](https://github.com/OdynBrouwer/hass.tibber_prices/commit/b7f1efce1f60481de3434fda279afc7b35d1bd98))
* **blueprints:** add appliance scheduling blueprints with auto-install ([e75e0ed](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e75e0ed1dc903e8f583f184bca67cf525b3bc193))
* **brand:** add local brand images for HA brands proxy API ([50dc874](https://github.com/OdynBrouwer/hass.tibber_prices/commit/50dc874274264c81d8db119bcda861bb9258ee0a))
* **brand:** update dark icons for improved visual consistency ([55e02e3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/55e02e3b54418e1aefab586c8a6cde5054a028e2))
* **cards:** add energy card with solar, battery and grid over the prices ([d37dbab](https://github.com/OdynBrouwer/hass.tibber_prices/commit/d37dbab2bb40ef478a6cfa5fbc0f6a2f7a6b7eb8))
* **cards:** add the chart card and open cards in windows of each other ([0e3856c](https://github.com/OdynBrouwer/hass.tibber_prices/commit/0e3856c27fabeb7c5a8aa8c3757f49fb75313a1c))
* **cards:** add the forecast card, the now card and a tile feature ([a9909bf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a9909bf9c288666660b1779818cba7b53a52e2dc))
* **cards:** name the time zone of a repeated hour by its abbreviation and mention clock changes in the details ([ecc4454](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ecc445406dd3a8db07c82ebf07c57a8285628251))
* **cards:** offer a reload when an update left a page with old cards ([#281](https://github.com/OdynBrouwer/hass.tibber_prices/issues/281)) ([0f00a56](https://github.com/OdynBrouwer/hass.tibber_prices/commit/0f00a56c1a531e567e6ec215e76c95031409f290))
* **cards:** read a day's prices by holding a finger on its chart ([c6e6800](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c6e6800abed09766a9eb428918ffe576593b92bd))
* **cards:** show the quarter hours of an hour's details unrounded ([e1d855a](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e1d855a0ba9b036427d1420b83b6e442d14e5348))
* **cards:** show the total or the energy price only, per card ([98fe36d](https://github.com/OdynBrouwer/hass.tibber_prices/commit/98fe36d150075f6575fa77636b28d900f1c75a09))
* **coordinator:** surface prolonged API outages and cache-fallback state ([ada4e33](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ada4e3344894b17ae1a97cb752d9b75599207008))
* **deps:** add npm package updates for user and developer documentation directories ([f4fecc3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/f4fecc3ee0d920b75c43941020768b2a65b9fd47))
* **devcontainer:** add common CLI tools and setup symlinks for compatibility ([c7af02f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c7af02f7c2a474f05c2a05a35cfa1828857b6c8e))
* **devcontainer:** add yq and additional CLI tools, improve compatibility symlinks ([8aa5769](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8aa57697843db97ae3af0cc1ffb2972d349c5019))
* **device:** mark headless views in model_id and offer them in the picker ([cdfab43](https://github.com/OdynBrouwer/hass.tibber_prices/commit/cdfab4387fe19351c7b6a1cbe4e21ecb5a589d5e))
* **docs:** add click-to-zoom lightbox for Mermaid diagrams ([552db6e](https://github.com/OdynBrouwer/hass.tibber_prices/commit/552db6ef7d04ee78216848747b2f875c041c8d7d))
* **docs:** add comprehensive configuration documentation for Tibber Prices integration ([ee9adce](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ee9adce9d52d1da31b789e5e341a64b3b4d97263))
* **docs:** add multi-language entity reference with search ([0e699ae](https://github.com/OdynBrouwer/hass.tibber_prices/commit/0e699ae14219a95b4764f170d1c254a8a9ad31d9))
* **docs:** add price phase sensors documentation and update references ([76a3a0f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/76a3a0f1fde28f7991457d20d3a36ae598c0db3c))
* **docs:** enable mdx1 compatibility for admonitions in Docusaurus config ([112b169](https://github.com/OdynBrouwer/hass.tibber_prices/commit/112b169f26172f86a83249e3c41477d27b57b1a5))
* **docs:** improve sidebar and navbar UX ([1db86d1](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1db86d1766ea21ae04adb097825a492ecbb54566))
* **editorconfig,devcontainer:** configure JSON formatting settings for consistency ([e44f639](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e44f639b41d1f86acbc9713461b9364eae73b4f2))
* enhance mermaid lightbox interaction with improved accessibility and hover hints ([b7cf444](https://github.com/OdynBrouwer/hass.tibber_prices/commit/b7cf4442bd786776664b3f96e66e61c36972e36b))
* **entity:** expose integration version as sw_version in device info ([2d2873f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2d2873f75f7971c7bbffaedc799c5a0c1c027516))
* **marketplace:** support the built-in Marketplace, rename to Tibber Prices & Planning ([2d670dd](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2d670dd5177a5bddd37d43d7e4d2eddd513560da))
* **migrations:** add entity auto-migration system with HA repairs ([565397b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/565397b8ca46527e8725dd4a5a6db9494027f19e))
* **options:** show persistent repair issue after currency mode change ([061b42b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/061b42b8f34715c254a380c5c1d846c0c1b3ffd2))
* **periods:** geometric V-shape flex extension for period detection ([4ddd19b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/4ddd19b1324e184a1f9f3d55d049007291cc4c65))
* **periods:** implement geometric_extension_attempted flag and time_range filtering ([a8d5230](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a8d5230531fd7b2cf53d948cb5ca097bac899963))
* **periods:** implement geometric_extension_attempted flag and time_range filtering ([796eb4b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/796eb4b4225f5bf25930c685ff4313e9bbb0a872))
* **pricing:** add relaxation logic for progressive filter loosening ([303a7c7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/303a7c7835cb2e544017cd19f601cfe2916d8b76))
* **pricing:** enhance scheduling actions with new parameters ([303a7c7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/303a7c7835cb2e544017cd19f601cfe2916d8b76))
* **release:** add Claude Code backend for release notes ([2e1cabc](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2e1cabc34be25f0069c8d7c2cadb528ffd967682))
* **repairs:** make notices confirmable and tidy issues on start ([ef058d3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ef058d38dbcfa834ee854a6c0e5412ee22a013a2))
* require Home Assistant 2026.11 or newer ([#288](https://github.com/OdynBrouwer/hass.tibber_prices/issues/288)) ([cfb04dc](https://github.com/OdynBrouwer/hass.tibber_prices/commit/cfb04dca2bb78053fd2136a996d1d889156e2cf1))
* **sensor:** add next/previous/rolling-hour price rank sensors ([51a62d7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/51a62d712ff13c0f59e2ec7b742351a3fed44c36))
* **sensor:** add price rank sensors and IQR-based volatility attributes ([6f52617](https://github.com/OdynBrouwer/hass.tibber_prices/commit/6f5261785bdf4cee8263f057305420aa02bf3811))
* **sensors:** add a price outlook to the current price sensor ([3a0ae90](https://github.com/OdynBrouwer/hass.tibber_prices/commit/3a0ae90221aababcb45eceeac089d18fabfc9098))
* **sensors:** add day pattern detection sensors (valley/peak/flat/rising/falling) ([447dc90](https://github.com/OdynBrouwer/hass.tibber_prices/commit/447dc907e6ac08701e57918ce261c00a934ba905))
* **sensors:** add new price phase and duration sensors ([c85f499](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c85f4991abeb32282a5b443e02cc38cf379b06c0))
* **sensors:** expose currency on chart_data_export for attribute-based consumers ([d62938a](https://github.com/OdynBrouwer/hass.tibber_prices/commit/d62938ac14c3847f91024286d3fd87af70adfd9f)), closes [#201](https://github.com/OdynBrouwer/hass.tibber_prices/issues/201)
* **sensors:** expose energy/tax breakdown as sensor attributes ([edabb49](https://github.com/OdynBrouwer/hass.tibber_prices/commit/edabb49309c06a378541f9cfcbd2ee5a1df083fc))
* **sensors:** rename price_trend_Xh → price_outlook_Xh, add price_trajectory_Xh ([33f57ff](https://github.com/OdynBrouwer/hass.tibber_prices/commit/33f57ff077d85a514cfb80b8b6627419fa94e2c5))
* **sensors:** rename trend change countdown sensor for naming consistency ([b1b41be](https://github.com/OdynBrouwer/hass.tibber_prices/commit/b1b41be9aa1264b7f5f33796aa8505df4206d46e))
* **sensors:** show the windows behind hourly sensors and cheap stretches ([ef5deb4](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ef5deb4ecc9aef608cfcd7748c9294803526c072))
* **sensors:** use native minutes for all duration sensors ([faa3b2b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/faa3b2b71a34862863fd925ae78c376ce6be0391))
* **sensor:** use dynamic precision for price rounding and display ([a4ad506](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a4ad506e01d087efa2ddfc62d515ecbfd5675507))
* **services:** add 5 scheduling services for price-optimized time windows ([6e0613c](https://github.com/OdynBrouwer/hass.tibber_prices/commit/6e0613c0557856ba6f43642c6504e993ff370519))
* **services:** add energy/tax fields to get_chartdata action ([d1b25e9](https://github.com/OdynBrouwer/hass.tibber_prices/commit/d1b25e9cfee1c8fafbc4d2238040f35fe8e64ec4))
* **services:** add get_dashboard_yaml for a complete dashboard view ([41a5632](https://github.com/OdynBrouwer/hass.tibber_prices/commit/41a56325c20f487ea3635bd46f74984402402d3b))
* **services:** add plan_charging service for battery/EV scheduling ([96f36a3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/96f36a33397ec4ac239f7de4630878ebd69722b4))
* **services:** add power-profile-weighted window selection ([b93eedf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/b93eedf00eb34f93afa862841ec6b08143b34b3b))
* **services:** add price_source parameter to get_chartdata and get_apexcharts_yaml ([dc4933e](https://github.com/OdynBrouwer/hass.tibber_prices/commit/dc4933ec5cb545a58ec784a66ea063e5ec527719))
* **services:** add reason codes and schedule comparison details to find services ([c89248d](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c89248d493288a962b03b80eda62cef760b36bfd))
* **services:** add sequential parameter to find_cheapest_schedule ([31fca73](https://github.com/OdynBrouwer/hass.tibber_prices/commit/31fca73ccd6cfd1e68c364a077123ab1a3f88023))
* **services:** allow entity IDs as service parameter values ([e01cc5d](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e01cc5d4471643247096fe46f4c0f8b4a16ac638))
* **services:** isolate price-fetch failures and add success flag to responses ([feaf748](https://github.com/OdynBrouwer/hass.tibber_prices/commit/feaf748cb65f983579138f1ffa18fc07d5e5d480))
* **services:** let actions answer for a time-travel view ([8bcbe67](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8bcbe672477e50461e4016e6431c41ad0064f8d7))
* **settings:** add local settings for script permissions ([870b716](https://github.com/OdynBrouwer/hass.tibber_prices/commit/870b716681a0c46e918f913cd275da70cd825d42))
* **time-travel:** add yearly mode, headless views and realism controls ([7755cee](https://github.com/OdynBrouwer/hass.tibber_prices/commit/7755cee208cb42ab5d99082ff1f11e1c17079554))
* **time-travel:** enable historical price views as config subentries ([430a858](https://github.com/OdynBrouwer/hass.tibber_prices/commit/430a8587616f2bd6590560c690f3e8829a3f2c13))
* **time-travel:** manage cache lifecycle, warn on retention, document ([a1429cf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a1429cf3ce43ceb0fc769fec9118918569f61dce))
* **translations:** add custom descriptions for price rank and volatility band sensors (5 languages) ([0ca52f8](https://github.com/OdynBrouwer/hass.tibber_prices/commit/0ca52f8d3c0dafa5020e46502c81f31426989900))
* **translations:** add price_outlook_Xh and price_trajectory_Xh strings ([2b96ccc](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2b96ccc6500aaa7d70182487ce8b3f980a40ceec))
* **translations:** add UI labels for price rank sensors (5 languages) ([7b477cd](https://github.com/OdynBrouwer/hass.tibber_prices/commit/7b477cd4c70e6d4751fb5a1a4d12580daef6d8e4))
* **translations:** enhance price trend change descriptions and usage tips ([4ba159d](https://github.com/OdynBrouwer/hass.tibber_prices/commit/4ba159d81595d04098f9829ec313c32b36a94b65))
* **translations:** translate attribute names in the more-info dialog ([3a37c02](https://github.com/OdynBrouwer/hass.tibber_prices/commit/3a37c0242e363090769c414efd9e9864c8048aaf))
* **trend:** make current price trend the direction prices move in now ([fdbc50e](https://github.com/OdynBrouwer/hass.tibber_prices/commit/fdbc50eb5b9c00064e48a242636d350963b47d43))
* **workflow:** add auto-assign GitHub Action for issue assignment ([1706bd7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1706bd7c0eb8041cffcfbdda2c3bf8a44d651ee7))


### 🐛 Fixed

* **api:** accept priceInfoRange-only responses and retry transient empty data ([8da3083](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8da3083fb2422db652ed6a38229d15ddd2da76a3))
* **attributes:** leave undeclared attributes out of the recorder, share the half-window threshold ([7cb380f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/7cb380fa67b8f9bab93831a4a179c4a160d2b940))
* **blueprints:** correct remote_start_sensor description in home_connect blueprints ([95d0278](https://github.com/OdynBrouwer/hass.tibber_prices/commit/95d0278241ea54a246fa572781eed71be8cc0707))
* **blueprints:** fix home_connect_alt service call and correct sensor description ([c2ff9cd](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c2ff9cd2f29a44383ad48965349e828648c39488))
* **cards:** fade a pushed-out day name within a few pixels ([e1e344f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e1e344f181e9649f216b57ddf660f77f5333c641))
* **cards:** keep the bars of a zoom chart inside it when prices differ below the rounding ([cd434c7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/cd434c71a49824f3ab4e26fdca89e79eb1b6c363))
* **cards:** keep the chart cursor tag clear of the switches on touch ([50b4a54](https://github.com/OdynBrouwer/hass.tibber_prices/commit/50b4a54dd395309c355a792f92f87886780ab1ab))
* **cards:** make the card windows and strips usable on phones ([#223](https://github.com/OdynBrouwer/hass.tibber_prices/issues/223)) ([c28ea9c](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c28ea9cd738aef60dff11801dbcae4c9926cdf5d))
* **cards:** scale each day of the hour and part-of-day strips on its own and keep a narrow span's pointers on it ([8922460](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8922460f8f859bd415aabebd79757a175be0b6b9))
* **cards:** scale each day of the hour and part-of-day strips on its own and keep a narrow span's pointers on it ([8e3b2da](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8e3b2da89883ccba94f591f15c69b645cd7145f7))
* **cards:** show the back arrow in a card's detail window opened from a card window ([c199a14](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c199a14b1c625eba15efdbff0e762af1d81a1bb0))
* **cards:** tell the two passes of the repeated hour apart when the clocks go back ([e9334cd](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e9334cd651331215b08ddfc09f2a5b2d6e235a7d))
* **charts:** aggregate hourly chart data by clock hour ([89fd341](https://github.com/OdynBrouwer/hass.tibber_prices/commit/89fd3415f1a24fd962d71ddf8cfffdad0578079c))
* **charts:** read the data of the time-travel view a chart was made for ([42e2541](https://github.com/OdynBrouwer/hass.tibber_prices/commit/42e25418cc15953c2947a862bafd2ddc267e6a61))
* **ci:** dispatch docusaurus workflow from auto-tag ([5688698](https://github.com/OdynBrouwer/hass.tibber_prices/commit/5688698e522a3888a97eec8fa3808659bfb3e6b7))
* **ci:** ensure release notes end with newline before heredoc delimiter ([bb17613](https://github.com/OdynBrouwer/hass.tibber_prices/commit/bb176135f6bd4c7fad14ab8b3d73aa7941f74d13))
* **ci:** rebase docs snapshot commit onto main before pushing ([4227b13](https://github.com/OdynBrouwer/hass.tibber_prices/commit/4227b1336894578e04c4b17c371b9a9670039722))
* **ci:** take the previous tag relative to the pushed tag, not HEAD ([e7858f2](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e7858f209b0ad8565346ce41a33b874a6608612f))
* **ci:** use random heredoc delimiter in release workflow ([8bd3ef8](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8bd3ef85c0e18bc476edf4e14f6aa96f565cf54c))
* **coordinator:** fetch prices of a contract that runs before its start date ([8294f63](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8294f6335028429c96d2bfa32e84dedb847e0b0f))
* **coordinator:** support contracts that have not started yet or have ended ([#235](https://github.com/OdynBrouwer/hass.tibber_prices/issues/235)) ([e4f94ee](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e4f94eea7c71d35e765ed1c2c6480f386cac2a82))
* **css:** adjust width of mermaid lightbox inner card for better responsiveness ([86c5db1](https://github.com/OdynBrouwer/hass.tibber_prices/commit/86c5db179e0d8e6f4a6ecd023a3f83b52f13e9e8))
* **css:** enhance mermaid lightbox styling for better theme integration ([dba96e3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/dba96e38e0e2e5eea1d73428a7d61eb4c81163e5))
* **day-pattern:** let segments end where the next one takes over ([7ce7139](https://github.com/OdynBrouwer/hass.tibber_prices/commit/7ce713991c86a1c93f1652a45cad207e5f428350))
* **deps:** remove unnecessary peer dependencies from package-lock.json ([9fea34b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/9fea34b8b40cea28d22e9f172cf3923596f6f12e))
* **device:** unify device info across all platforms ([08080b1](https://github.com/OdynBrouwer/hass.tibber_prices/commit/08080b1df0133307436e71d4b8d9ddf3e36efc7b))
* **diagnostics:** redact identifying data from the diagnostics download ([3942f87](https://github.com/OdynBrouwer/hass.tibber_prices/commit/3942f87e870df5d057d6e4286c866151256c3a03))
* **docs:** avoid mdx/ssg runtime error in energy-tax formula ([ac09e5f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ac09e5f235b71be6fdcd2c2de2b3ad0f26b54578))
* **docs:** commit missing versioned_sidebars for all existing versions ([3aa8a43](https://github.com/OdynBrouwer/hass.tibber_prices/commit/3aa8a43e3a7343bef8aa4f3364474f6434cc8e6a))
* **docs:** correct inaccuracies and add missing documentation ([0711780](https://github.com/OdynBrouwer/hass.tibber_prices/commit/07117801d20c1c7a4fbc0ef80efab0f2528d74c4))
* **docs:** update image URLs in README for proper rendering ([74cca18](https://github.com/OdynBrouwer/hass.tibber_prices/commit/74cca1857a9917dddb3d8692ea872abe6d7b43e2))
* **docs:** update links in automation examples and intro documentation ([db900c2](https://github.com/OdynBrouwer/hass.tibber_prices/commit/db900c2a4b85830a95656beaf7e1b60b40b98f88))
* ensure SVG backgrounds are solid to prevent transparency issues ([aa0f543](https://github.com/OdynBrouwer/hass.tibber_prices/commit/aa0f543ec5a033b9e5525122bc950afa84ab7996))
* **find_cheapest_schedule:** retry valid window start after time gaps ([36e9cdf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/36e9cdf4b904e44f7d383d95c72059df12ef73ff))
* **get_chartdata:** use proper statistics.median for chart metadata ([13b9870](https://github.com/OdynBrouwer/hass.tibber_prices/commit/13b9870f455e1895f91dbec68cc5879a42ae3283))
* **hacs:** hide the default branch, it cannot install with zip_release ([697d221](https://github.com/OdynBrouwer/hass.tibber_prices/commit/697d221b535ccd995856d4ac2e6d0ce19f948e92)), closes [#270](https://github.com/OdynBrouwer/hass.tibber_prices/issues/270)
* **i18n:** name the connection and chart export attributes, tidy the source ([5edcb7e](https://github.com/OdynBrouwer/hass.tibber_prices/commit/5edcb7e190a6bb3ce008a4b9d1e6cc86494d69b0))
* **i18n:** translate the rating sensors hint in the attribute rename notice ([a424821](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a424821dfcfc52f7d4985644c41d6eaa208127e3))
* **interval_pool:** rebuild index after dead interval cleanup without empty groups ([ebcb9cf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ebcb9cfe776bc913efcc3de62ac0cbb8c139af61))
* **interval_pool:** stop DST fall-back extras from growing on every re-add ([d1641b9](https://github.com/OdynBrouwer/hass.tibber_prices/commit/d1641b9e2d723a16db1c45d9e23d80b3f5945826))
* **interval-pool:** protect the home's days in the home's time zone ([2b7ebf0](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2b7ebf0a96ff94623f52155eae3cdec83a7b9635))
* **interval-pool:** select indexed timestamps instead of generating them ([69bbd87](https://github.com/OdynBrouwer/hass.tibber_prices/commit/69bbd873fa9284c761194a15d42c0d85ed044e82))
* **lint:** apply Python 3.14 ruff rules and update HA minimum version ([ac7cd5b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ac7cd5b572b7e2bf8193a23d6e5b323fa444facf))
* **periods:** give the day's price range of a period the display unit ([2aaa04a](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2aaa04a69b30d258c20216df534be2649d4647a0))
* **periods:** keep negative best-price windows strictly local ([10c83d6](https://github.com/OdynBrouwer/hass.tibber_prices/commit/10c83d672089001cd2bcd63bcfd2487a6d3a0883))
* **periods:** make flex a share of the gap between the daily extreme and the mean ([a854211](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a8542118d323007cfb571fff86dd3c8a69b9e412)), closes [#259](https://github.com/OdynBrouwer/hass.tibber_prices/issues/259)
* **periods:** rename periods_remaining to period_count_remaining ([1d3c550](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1d3c55097d080e09edadb0f67d8933ae7cd5fdbf))
* **periods:** replace redundant total attributes with per-day counts ([779e22a](https://github.com/OdynBrouwer/hass.tibber_prices/commit/779e22a84e111d2df65ce037a6084f91b86fe256))
* **periods:** separate smoothed levels from period detection ([9cb5b35](https://github.com/OdynBrouwer/hass.tibber_prices/commit/9cb5b351849298891147a859518f43a188770a06))
* **periods:** stabilize best and peak period outputs ([bbcfdd4](https://github.com/OdynBrouwer/hass.tibber_prices/commit/bbcfdd4443ec072b0624c67a6351a09a5083ea6e))
* **repairs:** force statistics-review issue visible on mode change ([e6ec54d](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e6ec54d8c58b92e2ec8c9037c0569ae71acef362))
* **repairs:** reliably show statistics-review issue on every HA restart ([09edcdb](https://github.com/OdynBrouwer/hass.tibber_prices/commit/09edcdb9a36f17e4996dd3767b704b0355cc20bf))
* **repairs:** respect dismissal of statistics-review repair issue ([5b5d5e7](https://github.com/OdynBrouwer/hass.tibber_prices/commit/5b5d5e73b02322b863567e5838a0b91a0218abf6))
* **scripts:** fall back to git-cliff when AI release notes are not valid ([2b0feda](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2b0feda57cbb26f414b4c0775d9681330bac6a6d))
* **sensors:** fix DURATION sensors displaying in minutes instead of hours ([d0b6ea0](https://github.com/OdynBrouwer/hass.tibber_prices/commit/d0b6ea0e1a848c2f5817c9fe7c690f56023fbda6))
* **sensors:** use consistent rounding for trend duration calculations ([2a08515](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2a08515ba0aa6a7a467393a4d7cd5573556b3df9))
* **services:** align search start to quarter boundary when current interval excluded ([2be6ed0](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2be6ed067435ab5151ea2e24c5442094aee35b7b)), closes [#190](https://github.com/OdynBrouwer/hass.tibber_prices/issues/190)
* **services:** correct min_distance_from_avg direction for negative prices ([1b207f0](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1b207f0db152ca3bef2dc7ddc860d5d3548df50a))
* **services:** name both homes when entry_id and view_id disagree ([ebb1d07](https://github.com/OdynBrouwer/hass.tibber_prices/commit/ebb1d0798793973d9a6f229ed40be0a4c49e261e))
* **services:** preserve service call data through coordinator data fetch ([#151](https://github.com/OdynBrouwer/hass.tibber_prices/issues/151)) ([db5d172](https://github.com/OdynBrouwer/hass.tibber_prices/commit/db5d172fb88478c7c0b04cab6001d3bc42d00f38))
* **services:** prevent plan_charging overcharge from segment-constraint bridging ([b8e40bf](https://github.com/OdynBrouwer/hass.tibber_prices/commit/b8e40bfa3b7358a5df90a793d3f26acb91de7846))
* **services:** prevent power_profile truncation during relaxation ([95004ef](https://github.com/OdynBrouwer/hass.tibber_prices/commit/95004efa2d16721ca4ecc981ad834cfc253c170c))
* **services:** snap every search boundary onto the quarter-hour grid ([1f93848](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1f93848a26bb14676465b950d704bd70a166dc46))
* **services:** use injected now in resolve_search_range day offset ([1d065b1](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1d065b11cdbcb46849658abb4d0994bdb2be70de))
* **tests:** move LogCaptureFixture import under TYPE_CHECKING for better type hinting ([c610dbe](https://github.com/OdynBrouwer/hass.tibber_prices/commit/c610dbe1a39457ce4ba35dec2f0440fd5bb10b2a))
* **time-travel:** detect reconfigured views against a config snapshot ([1a0b819](https://github.com/OdynBrouwer/hass.tibber_prices/commit/1a0b819c58972d304e4c478014eab5481048cf64))
* **time-travel:** explain why a zero-offset view is refused ([7fd2813](https://github.com/OdynBrouwer/hass.tibber_prices/commit/7fd28139e254a57ec6a26e19b776e1ed0ac557b9))
* **time-travel:** name a view after the home device, not the config entry ([07be6bc](https://github.com/OdynBrouwer/hass.tibber_prices/commit/07be6bc37f0341e6087671e1f362627bb72e08df))
* **translations:** correct message formatting in multiple language files ([e39d0be](https://github.com/OdynBrouwer/hass.tibber_prices/commit/e39d0be162007dd8f445ff796c7368c6fe758e9d))
* **translations:** stop ICU from escaping the mismatch placeholders ([238a26f](https://github.com/OdynBrouwer/hass.tibber_prices/commit/238a26fc0313e8532698c04a70a85a513e1eece3))
* update default Copilot model version to 4.6 ([a4a43e3](https://github.com/OdynBrouwer/hass.tibber_prices/commit/a4a43e3d34b0976a93602c2ca59a3286a6a148de))


### ⚡ More reliable

* **cards:** load the dashboard cards gzip-compressed ([#278](https://github.com/OdynBrouwer/hass.tibber_prices/issues/278)) ([4e1d93e](https://github.com/OdynBrouwer/hass.tibber_prices/commit/4e1d93ebeb27643db6539d6656f4063893f7d1e6))
* **interval_pool:** run GC after touch-only interval updates ([361498b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/361498b7f58f964d6b671ff527e8c6cf2e79f801))
* **interval_pool:** skip redundant API calls when prior fetch covers range ([db02f26](https://github.com/OdynBrouwer/hass.tibber_prices/commit/db02f262b6521ee43f91e89b9cb7a91166a22e35))
* **recorder:** also exclude the trend percentages and next-hours averages ([8fd78e8](https://github.com/OdynBrouwer/hass.tibber_prices/commit/8fd78e82dee69eaa27cd19a1a3d92d4b923b2215))
* **recorder:** exclude more derived and repeated attributes from history ([98acc38](https://github.com/OdynBrouwer/hass.tibber_prices/commit/98acc3826d9f103a16800059d9f4fc1d2b348347))
* **sensors:** add call-avoidance for timer-based state updates ([459d676](https://github.com/OdynBrouwer/hass.tibber_prices/commit/459d6762c7af13404e311cc13e7241ee8289e0e1))


### 📦 Updated dependencies

* **i18n:** generate the translated attribute names from one source ([2af1791](https://github.com/OdynBrouwer/hass.tibber_prices/commit/2af179156fe69ad5c300f6b69606e5311957d90f))


### Code refactoring

* **attributes:** rename attribute keys ending in % to _percent ([5dd3c5b](https://github.com/OdynBrouwer/hass.tibber_prices/commit/5dd3c5ba4e54bcb8e04959fe6542ba022c96cbe2))

## [0.40.0](https://github.com/jpawlowski/hass.tibber_prices/compare/v0.39.1...v0.40.0) (2026-11-22)

### ⚠️ Before You Update: Some Attribute Names Change

- **Attributes that ended in `_%` now end in `_percent`**, for example `rating_difference_%` → `rating_difference_percent`. They belong to the best and peak price period sensors and to the trend, rating and volatility sensors.

**What this means for you:** If a template, automation or dashboard card reads one of these attributes, change the name. After the update, a notice in **Settings → Repairs** lists every renamed attribute.

### 🎉 What's New

- **Attribute names in your language.** The more-info dialog now shows attribute names translated into English, German, Norwegian, Dutch and Swedish instead of the technical key, for example "Difference from daily maximum (%)". The dialog sorts attributes by their displayed name, so the order differs per language.

### 🐛 Fixed

- **Diagnostics files no longer contain personal data.** The home's address, coordinates, home ID, names and account email are removed from the diagnostics download, so you can attach it to a public issue.
- **The connection sensor and the chart export show readable attribute names** instead of raw keys.
- **The chart export no longer fills the database.** Its full result was stored in the history; now only the attributes it declares are kept, and unknown attributes of other entities aren't stored either.
- **The attribute rename notice reads fully in your language.** Its hint about the rating sensors was still in English in the German, Norwegian, Dutch and Swedish texts.

### ⚡ More Reliable

- **The Home Assistant database grows more slowly.** Attributes that repeat the state or can be recalculated from the recorded prices are no longer kept in the history, for example the trend percentages, next-hours averages, volatility statistics and timing minutes. The states and the main numbers stay in the history, and rows already stored are unchanged.
