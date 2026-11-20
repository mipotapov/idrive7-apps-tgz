# idrive7 — русские пакеты приложений для MGU (iDrive 7)

Собрано из трёх исходных репозиториев в `~/Downloads` с русским интерфейсом:

| Исходники | Что собрано |
|---|---|
| `idrive7-apps-main` | 15 приложений основного набора |
| `idrive7-apps-main-2` | eDrive Live, Light Show |
| `idrive7-cluster-info-main` | Cluster Info, Cluster Layouts, Cluster Centre |

Итого: **20 пакетов приложений** (`apps/*.tgz`) и **3 инструмента** (`tools/*.tgz`).

Английский набор в эту папку не входит: здесь только русские пакеты и их `catalog.json`.

---

## Важно: почему внутри нет BMW SDK

`oap-sdk` — проприетарный код BMW, его нельзя распространять, и в репозиториях его нет.
Пакеты собраны **без** `node_modules/oap-sdk` — это штатный формат для MGU Store
(см. `docs/PUBLISHING.md` в репозитории `mgu-store`). При установке через **MGU Store**
модуль `oap-sdk` создаётся автоматически из donor-приложения, уже установленного в машине
(обычно `x_call`). Поэтому:

* устанавливать нужно через **MGU Store** (с флешки или как источник);
* старый установщик из `idrive7-apps` (`push-to-car.sh`, `mgu-app-install.sh`,
  `deploy-car.sh`) эти пакеты «как есть» не поставит — для него нужно сначала извлечь SDK
  из своей машины и пересобрать пакеты (команды в конце файла).

## Установка через MGU Store

1. Скопируйте папку `idrive7` на USB-флешку так, чтобы получилось:

   ```
   <флешка>/mgu-repo/idrive7/catalog.json
   <флешка>/mgu-repo/idrive7/apps/...
   <флешка>/mgu-repo/idrive7/tools/...
   <флешка>/mgu-repo/idrive7/icons/...
   ```

   Либо скопируйте **содержимое** папки `idrive7` в корень флешки — тогда `catalog.json`
   будет в корне.

2. Вставьте флешку в машину и откройте в MGU Store страницу **USB**.
3. Установите нужные приложения. `idrive7-renderd`, `mgu-inputgate` и `cluster-render`
   Store поставит первыми как зависимости.

**Если английская версия уже установлена.** Номера версий русских пакетов совпадают с
английскими (`2.7.7`, `1.6.22`, …), потому что формат каталога MGU Store требует версию
строго `x.y.z`. Store считает такую версию уже установленной и может не предложить
переустановку. Перед установкой русского варианта удалите соответствующее английское
приложение (или ставьте русский набор на чистую машину).

Примечания:

* `mgu-inputgate` загружается в HMI при следующем запуске — может потребоваться перезагрузка ГУ.
* `cluster-render` нужен только для Cluster Info / Cluster Layouts / Cluster Centre.
* Doom использует GPU-рендерер, он входит в комплект.

---

## Что переведено

За основу взят официальный русский перевод основного репозитория. Дополнительно переведены
строки, которых в нём не было:

* все настройки и подписи приложений из форков (`eroobeeroo/idrive7-apps` и
  `idrive7-cluster-info`): eDrive Live, Light Show, Cluster Info, Cluster Layouts,
  Cluster Centre;
* новые опции Redline и других приложений, появившиеся после официального перевода.

Единицы измерения (`rpm`, `psi`, `kPa`, `mpg`), коды валют, названия шрифтов, игровые эпизоды
Doom и фирменные названия (`M Red`, `M Tricolour`, `Ice White`, `Night Amber`, `GT3`,
`Cluster Info` и т. п.) оставлены латиницей — так их проще узнать.

---

## Состав

### Инструменты (`tools/`)

| Пакет | Версия | Назначение |
|---|---|---|
| `idrive7-renderd` | 2.1.19 | GPU-рендерер экранов приложений (60 fps) |
| `mgu-inputgate` | 1.2.1 | Доступ приложений к контроллеру iDrive |
| `cluster-render` | 0.6.9 | Рендерер приборной панели и HUD |

### Приложения (`apps/`)

| Пакет | Версия | Что делает |
|---|---|---|
| `ambient_config` | 2.7.7 | Настройка ambient-подсветки |
| `brake_test` | 1.5.21 | Таймер торможения |
| `car_vitals` | 2.27.8 | M Vitals: живые параметры двигателя |
| `doom` | 1.7.22 | Doom (для стоянки) |
| `draggy` | 2.6.0 | Драг-таймер |
| `dtc_scanner` | 2.9.8 | Сканер/очистка ошибок (DTC) |
| `dyno` | 1.6.3 | Виртуальный диностенд |
| `edrive` | 2.11.0 | eDrive для PHEV/BEV |
| `edrive2` | 1.10.1 | eDrive Live |
| `gforce` | 1.6.22 | G-Force |
| `light_show` | 0.5.2 | Световые сцены внешними лампами |
| `live_adjustments` | 0.9.8 | Engine Config: настройки/адаптации |
| `live_data` | 1.0.18 | Live Data и поездки |
| `redline` | 2.0.45 | Тахометр, shift lights, HUD |
| `service` | 1.6.3 | Сервисные позиции CBS |
| `warmup` | 1.9.0 | Прогрев двигателя/масла |
| `zf8hp` | 1.5.8 | Монитор АКПП ZF 8HP |
| `cluster_info` | 1.6.8 | Панель значений поверх Waze в приборке |
| `cluster_layouts` | 0.28.1 | Свои раскладки приборной панели |
| `cluster_centre` | 0.9.0 | Центр приборной панели с данными |

---

## Если нужен вариант со встроенным SDK (для старого установщика)

Нужен SSH-доступ к своей машине (как в README `idrive7-apps`, раздел 3.1):

```sh
# в папке нужного репозитория, например idrive7-apps-main
scp root@<IP-машины>:'/usr/lib/oap-mainapp/preinstalled_apps/x_call@*.tgz' .
mkdir x_call && tar xzf x_call@*.tgz -C x_call
node kit/tools/extract_sdk.js x_call/javascript/app.js      # создаст ./oap-sdk/

python3 kit/tools/build.py --language ru                    # все приложения
# или только нужные:
python3 kit/tools/build.py --language ru redline gforce
```

Такие пакеты (`dist/<id>@<version>-ru.1.tgz`) содержат SDK и подходят для
`make-car-kit.sh` / `push-to-car.sh` / `mgu-app-install.sh`.

Русские файлы локализации добавлены и в форки, поэтому `--language ru` работает во всех
трёх репозиториях.

---

## Лицензии

Полные тексты и карта «пакет → лицензия» лежат в **`LICENSES/README.md`**. Кратко:

- 14 приложений основного репозитория — **MIT**; `doom` — **GPL-2.0** (из-за
  `doom.wasm`), данные Freedoom — BSD;
- `edrive2`, `light_show`, `cluster_info`, `cluster_layouts`, `cluster_centre` —
  **PolyForm Noncommercial 1.0.0**: бесплатно использовать, менять и
  распространять в некоммерческих целях, но **не продавать** и не брать деньги
  за установку; текст лицензии и `Required Notice` сохранять;
- `idrive7-renderd` — GPL-3.0-or-later + MIT-часть; `mgu-inputgate` — MIT;
  `cluster-render` — GPL-3.0, его Node-клиент — MPL-2.0;
- шрифты — SIL OFL 1.1; кириллический атлас — Ubuntu Font Licence 1.0;
  части cluster-раскладок от bimmer-lab — MIT.

Русская локализация — это изменение исходных приложений. При публикации
сохраняйте attribution авторов, переводчиков и ссылки на upstream. BMW
`oap-sdk` в пакетах нет, и распространять его нельзя.

---

## Проверка целостности

`SHA256SUMS` содержит контрольные суммы пакетов, иконок и `catalog.json`.
Проверка на macOS:

```sh
shasum -a 256 -c SHA256SUMS
```

на Linux:

```sh
sha256sum -c SHA256SUMS
```
