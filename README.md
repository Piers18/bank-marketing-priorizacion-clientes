# Priorización de clientes para campañas de depósito a plazo

Trabajo Parcial (TP1), semana 7, Data Mining Tools (CC209). Universidad Peruana de Ciencias Aplicadas.

**Integrantes:**

- Aguilar Anticona, Piero Antonio (u202419995)
- Chumbiauca Camac, Humberto Aesio (u202110619)

## Problema y datos

El proyecto estima la probabilidad de que un cliente suscriba un depósito a plazo **antes de llamarlo**, para priorizar una lista de contactos. Usa `bank-additional-full.csv` del conjunto [Bank Marketing de UCI](https://archive.ics.uci.edu/dataset/222/bank+marketing): 41 188 contactos, 20 predictores y la respuesta `y`. Los datos corresponden a campañas de un banco portugués entre 2008 y 2010; la ficha del proyecto documenta la procedencia y las condiciones de uso. La variable `duration` se excluye porque solo se conoce después de la llamada.

El notebook compara un clasificador trivial, una regla basada en `poutcome` y tres modelos de clasificación. La medida principal es PR-AUC; también evalúa cuántos suscriptores aparecen entre el 20 % de clientes mejor puntuados. Incluye una prueba temporal para mostrar la principal limitación: el rendimiento cae cuando cambia el contexto económico.

## Estructura

```text
dataMiningFinal/
├── 01_tp1_eda_preparacion_modelado.ipynb  # análisis y resultados ejecutados
├── bank-additional-full.csv               # datos originales
├── requirements.txt
├── models/                                # modelo y metadatos generados por el notebook
└── reports/                               # tablas y figuras generadas por el notebook
```

## Reproducir

Desde esta carpeta, con Python 3.11 o posterior:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
python -m jupyterlab
```

Abrir `01_tp1_eda_preparacion_modelado.ipynb` y ejecutar **Run All** desde el inicio. El CSV debe permanecer junto al notebook. La ejecución crea `models/` y `reports/`; no se necesita una descarga adicional. Para ejecutar sin interfaz:

```bash
jupyter nbconvert --to notebook --execute --inplace 01_tp1_eda_preparacion_modelado.ipynb
```

La validación cruzada, los modelos de árboles y la importancia por permutación pueden tardar varios minutos. El notebook conserva salidas visibles para revisar los resultados sin volver a ejecutarlo.

## Estado del TP1

El notebook documenta el problema, diccionario de variables, calidad y preparación, EDA con interpretación, separación 70/15/15, pipeline, baselines, comparación de modelos, evaluación y plan hacia el TF1. El mejor resultado con partición aleatoria no demuestra que el modelo funcione en campañas futuras: la prueba temporal muestra una caída considerable. Los costos de llamadas y el identificador de cliente no están disponibles; por eso todavía no se puede estimar el beneficio económico ni controlar repeticiones por cliente.

**Uso de IA generativa:** se utilizó para apoyar la organización del repositorio, la documentación y la presentación. El grupo debe revisar, comprender y poder sustentar cada decisión y conclusión antes de la entrega.
