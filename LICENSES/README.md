# Лицензии и attribution

Эта папка — не новая лицензия на приложения, а набор текстов и notices, которые
относятся к пакетам в `apps/` и `tools/`. Авторские права принадлежат авторам
исходных проектов; русская локализация — изменение, а не новый оригинальный
продукт.

## Что к чему относится

| Пакеты | Лицензия | Файл |
|---|---|---|
| `ambient_config`, `brake_test`, `car_vitals`, `draggy`, `dtc_scanner`, `dyno`, `edrive`, `gforce`, `live_adjustments`, `live_data`, `redline`, `service`, `warmup`, `zf8hp` | MIT (Copyright © 2026 cauliflowermossgrape; Chinese translation © 2026 小白151 / JackieZ123430) | `MIT-idrive7-apps.txt` |
| `doom` | GPL-2.0 для `doom.wasm` (doomgeneric); игровые данные Freedoom — BSD; JavaScript приложения — MIT, но распространяется в составе GPL-пакета | `GPL-2.0-doom.txt`, `NOTICE-doom.txt`, `MIT-idrive7-apps.txt` |
| `edrive2`, `light_show`, `cluster_info`, `cluster_layouts`, `cluster_centre` | PolyForm Noncommercial 1.0.0 (Copyright © 2026 eroobeeroo); унаследованный kit — MIT | `PolyForm-Noncommercial-1.0.0.txt`, `MIT-idrive7-apps-main-2.txt`, `MIT-idrive7-cluster-info.txt` |
| `cluster_layouts`, `cluster_centre` — части GT3/M/Sport, shaders, иконки, tyre readings | MIT (Copyright © 2026 bimmer-lab, cauliflowermossgrape) | `NOTICE-cluster-layouts.txt` |
| `idrive7-renderd` | GPL-3.0-or-later для `mgu-render`; части прежнего renderer — MIT | `GPL-3.0.txt`, `MIT-mgu-renderd.txt`, `NOTICE-tools.txt` |
| `mgu-inputgate` | MIT (controller gate из `kit/renderd/inputgate`); vsomeip headers — MPL-2.0 | `MIT-idrive7-apps.txt`, `MPL-2.0.txt`, `NOTICE-tools.txt` |
| `cluster-render` | GPL-3.0; Node-клиент `cluster_render_client.js` — MPL-2.0 | `GPL-3.0.txt`, `MPL-2.0.txt`, `NOTICE-tools.txt` |
| Шрифты Barlow, Noto Sans SC, Noto Sans KR | SIL Open Font License 1.1 | `OFL-1.1-Barlow.txt`, `OFL-1.1-NotoSansSC.txt`, `OFL-1.1-NotoSansKR.txt` |
| Кириллический атлас `cyrillic.json` | Ubuntu Font Licence 1.0 | `UFL-1.0.txt` |
| Шрифты кластера: Barlow, Michroma, Orbitron | SIL Open Font License 1.1 | `NOTICE-cluster-layouts.txt` (полный OFL-текст и copyright) |
| Attribution и notices upstream | — | `NOTICE-cluster-info.md`, `NOTICE-main-zh-CN.md` |

## Важно при публикации

- **PolyForm Noncommercial 1.0.0** разрешает бесплатно использовать, менять и
  распространять приложения в некоммерческих целях. Продавать их, брать деньги
  за установку/сборку/сопровождение или включать в коммерческий продукт нельзя.
  Текст лицензии и строку `Required Notice: Copyright (C) 2026 eroobeeroo`
  нужно сохранять.
- **GPL-3.0-or-later / GPL-2.0**: при распространении бинарников нужен
  соответствующий исходный код или ссылка на него. Источники:
  - `idrive7-renderd`: <https://github.com/cauliflowermossgrape/idrive7-apps/tree/main/kit/renderd>
  - `cluster-render`: <https://github.com/robertnisipeanu/idrive-apps/tree/main/native/cluster-render>
  - `doom.wasm`: <https://github.com/cauliflowermossgrape/idrive7-apps/tree/main/third_party/doomgeneric>
- **MPL-2.0** относится к `cluster_render_client.js` (и vsomeip-заголовкам
  inputgate). Исходники и уведомления не удалять.
- **Attribution** авторов и переводчиков нужно сохранить. Русская локализация
  является изменением; при публикации укажите, что это перевод/модификация,
  и оставьте ссылки на upstream.
- **BMW `oap-sdk`** в этих пакетах нет и распространять его нельзя: SDK
  генерируется на конкретном головном устройстве из его donor-приложения.

## Исходные проекты

- <https://github.com/cauliflowermossgrape/idrive7-apps> — основной проект (MIT)
- <https://github.com/eroobeeroo/idrive7-apps> — форк с eDrive Live / Light Show
- <https://github.com/eroobeeroo/idrive7-cluster-info> — cluster-приложения
- <https://github.com/robertnisipeanu/idrive-apps> — `cluster-render` и его Node-клиент
- <https://github.com/bimmer-lab/apps> — layouts/shaders/tyre readings (MIT)
- <https://github.com/jpt/barlow>, <https://github.com/googlefonts/Michroma-font>,
  <https://github.com/theleagueof/orbitron>, <https://github.com/notofonts/noto-cjk> — шрифты
- <https://ubuntu.com/legal/font-licence> — Ubuntu Font Licence 1.0 для кириллического атласа
- <https://freedoom.github.io> — игровые данные Freedoom
