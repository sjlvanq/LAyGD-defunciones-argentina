# Defunciones en Argentina (2017–2023)

Material de análisis previo para la elaboración del primer trabajo práctico de la materia **Apoyo en Matemática y Herramientas del Entorno Virtual – 2026** correspondiente al ingreso a la carrera **Licenciatura en Análisis y Gestión de Datos** — Universidad Nacional de San Luis.

---

## Descripción


Este repositorio contiene el análisis exploratorio y procesamiento preliminar de datos de defunciones en Argentina, elaborado como trabajo previo a un informe académico con predicción mediante modelos funcionales, en el marco del ingreso a la **Licenciatura en Análisis y Gestión de Datos** (UNSL) — materia **Apoyo en Matemática y Herramientas del Entorno Virtual**, 2026.

---

## Fuente de datos

Los datos de defunciones fueron obtenidos del portal oficial del **Ministerio de Salud de la Nación – DEIS (Dirección de Estadísticas e Información de Salud)**: [https://www.argentina.gob.ar/salud/deis/datos/defunciones](https://www.argentina.gob.ar/salud/deis/datos/defunciones)

---

## Estructura del repositorio

```
.
├── causas.csv                      # Tabla de referencia: código CIE-10 → descripción
├── defweb17_utf8.csv               # Defunciones 2017 (convertido a UTF-8)
├── defweb18_utf8.csv               # Defunciones 2018 (convertido a UTF-8)
├── defweb19_utf8.csv               # Defunciones 2019 (convertido a UTF-8)
├── defweb20_0.csv                  # Defunciones 2020
├── defweb21_0.csv                  # Defunciones 2021
├── defweb22_0.csv                  # Defunciones 2022
├── defweb23.csv                    # Defunciones 2023
├── ranking_causas_2017-2023.ipynb  # Principales causas de defunción por año
├── defunciones_2017-2023.ipynb     # Total de defunciones por grupo de edad y año
├── covid_2017-2023.ipynb           # Análisis de muertes por COVID-19 (U07)
├── neumonia_2017-2023.ipynb        # Análisis de muertes por neumonía (J18)
├── vih_2017-2023.ipynb             # Análisis de muertes por VIH (B20–B24, R75, Z21)
├── suicidios_2017-2023.ipynb       # Análisis de muertes por suicidio (X60–X84)
└── desnutricion_2017-2023.ipynb    # Análisis de muertes por desnutrición (E40–E46, D50–D53, P05)
```

---

## Datasets originales (defweb\*.csv)

Cada archivo presenta defunciones agregadas con las siguientes columnas:

| Columna   | Descripción |
|-----------|-------------|
| `PROVRES` | Código de provincia de residencia |
| `SEXO`    | Sexo del fallecido |
| `CAUSA`   | Código de causa de muerte (CIE-10) |
| `MAT`     | Maternidad (si aplica) |
| `GRUPEDAD`| Grupo etario |
| `CUENTA`  | Cantidad de defunciones |

### Nota sobre codificación y formato

Los archivos presentan divergencias en su formato según el año:

- Los datasets **2017, 2018 y 2019** fueron renombrados con el sufijo `_utf8` y su codificación fue normalizada a **UTF-8** (los originales usaban otra codificación).
- Los datasets **2017–2019** usan **coma** como separador y comillas dobles para los campos.
- Los datasets **2020–2023** usan **punto y coma** como separador, sin comillas.

Por este motivo, los notebooks utilizan `sep=None, engine='python'` al cargar los archivos, para que pandas detecte automáticamente el separador en cada caso.

---

## Notebooks

| Notebook | Descripción |
|----------|-------------|
| `ranking_causas_2021.ipynb` | Tabla con las 5 principales causas de muerte por año (2017–2023) según código CIE-10 |
| `defunciones_2017-2023.ipynb` | Total de defunciones por grupo etario para cada año |
| `covid_2017-2023.ipynb` | Defunciones por COVID-19 (`U07`) por grupo etario y año |
| `neumonia_2017-2023.ipynb` | Defunciones por neumonía (`J18`) por grupo etario y año |
| `vih_2017-2023.ipynb` | Defunciones por VIH (`B20`–`B24`, `R75`, `Z21`) por grupo etario y año |
| `suicidios_2017-2023.ipynb` | Defunciones por suicidio (`X60`–`X84`) por grupo etario y año |
| `desnutricion_2017-2023.ipynb` | Defunciones por desnutrición (`E40`–`E46`, `D50`–`D53`, `P05`) por grupo etario y año |

---

## Principales hallazgos (resumen)

| Causa | 2017 | 2018 | 2019 | 2020 | 2021 | 2022 | 2023 |
|---|---:|---:|---:|---:|---:|---:|---:|
| Total defunciones | 341.688 | 336.823 | 341.728 | 376.219 | 436.799 | 397.115 | 353.428 |
| Neumonía (J18) | 31.246 | 29.543 | 30.133 | 25.508 | 31.206 | 36.613 | 32.862 |
| COVID-19 (U07) | — | — | — | 53.122 | 84.695 | 23.850 | 2.228 |
| Suicidios | 3.222 | 3.322 | 3.297 | 2.871 | 2.864 | 3.221 | 3.488 |
| VIH | 1.458 | 1.339 | 1.265 | 1.139 | 1.260 | 1.174 | 1.102 |
| Desnutrición | 885 | 789 | 855 | 743 | 859 | 849 | 880 |

---

## Referencia de códigos CIE-10 utilizados

| Código(s) | Descripción |
|-----------|-------------|
| `J18` | Neumonía, organismo no especificado |
| `U07` | COVID-19 |
| `I50` | Insuficiencia cardíaca |
| `I21` | Infarto agudo de miocardio |
| `R99` | Otras causas mal definidas de mortalidad |
| `A41` | Otras sepsis |
| `X60`–`X84` | Lesiones autoinfligidas intencionalmente (suicidios) |
| `B20`–`B24`, `R75`, `Z21` | Enfermedades por VIH |
| `E40`–`E46` | Desnutrición |
| `D50`–`D53` | Anemias nutricionales |
| `P05` | Retardo del crecimiento fetal / desnutrición fetal |

---

## Licencia

Material académico de uso educativo. Los datos originales son de acceso público y pertenecen al **Ministerio de Salud de la Nación Argentina – DEIS**.
