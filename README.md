# Lab-4-Se-ales-Fatiga Muscular
## INTRODUCCION.

El presente laboratorio tiene como objetivo el análisis de señales electromiográficas (EMG) asociadas a la fatiga muscular, empleando señales reales adquiridas mediante un sistema DAQ.
La actividad busca comprender cómo las características temporales y frecuenciales de una señal EMG permiten identificar la presencia de fatiga en el músculo durante la contracción sostenida.

En esta práctica se estudia el comportamiento de la señal EMG a partir de su registro con electrodos de superficie ubicados sobre un grupo muscular específico. A través de la adquisición en tiempo real mediante la DAQ (Data Acquisition Device), se obtiene la señal eléctrica generada por la actividad de las fibras musculares. Posteriormente, la señal se procesa digitalmente aplicando herramientas como el análisis RMS (Root Mean Square) en el dominio del tiempo y la Transformada Rápida de Fourier (FFT) en el dominio de la frecuencia.

Estas técnicas permiten observar dos indicadores fundamentales de fatiga:

Una disminución progresiva de la frecuencia media (desplazamiento espectral hacia bajas frecuencias).

Una variación en la amplitud (RMS) de la señal a medida que el músculo se fatiga.

De esta manera, el laboratorio integra la adquisición de datos mediante hardware (DAQ) con el análisis digital en software (Python – Spyder), reforzando los conceptos de procesamiento de señales biomédicas, filtrado, segmentación y análisis espectral.

## RESUMEN.

En este laboratorio se desarrolló un proceso completo de adquisición, procesamiento y análisis de señales EMG para evaluar la presencia de fatiga muscular.
Inicialmente, se utilizó una señal de PhysioNet como referencia para probar el algoritmo de segmentación, cálculo del valor RMS y obtención del espectro de frecuencia mediante la FFT. A partir de esta señal se identificaron los cambios en la amplitud y la frecuencia media, que permiten evidenciar el proceso de fatiga.

Posteriormente, durante la sesión práctica, se realizo la adquisición de la señal real con la DAQ, conectada a electrodos de superficie. La señal registrada será procesada en tiempo real en Spyder para obtener sus características en el dominio del tiempo y la frecuencia. Finalmente, se calcularán los estadísticos descriptivos y se compararán los resultados entre los distintos intervalos de esfuerzo, observando cómo la frecuencia media disminuye y el RMS se modifica conforme aumenta la fatiga muscular.

Con este procedimiento, se busca consolidar la comprensión de los procesos fisiológicos involucrados en la contracción muscular y su representación eléctrica, al tiempo que se aplican las herramientas de procesamiento digital de señales biomédicas para el análisis cuantitativo y cualitativo de la fatiga.

## MARCO TEORICO:

## 1. Señal Electromiográfica (EMG):

La señal electromiográfica (EMG) representa la actividad eléctrica producida por las fibras musculares durante la contracción.
Esta señal se origina debido a los potenciales de acción generados en las unidades motoras, las cuales se activan por la estimulación del sistema nervioso.
En el caso de los registros con electrodos de superficie, la señal capturada corresponde a la suma de los potenciales de acción de múltiples fibras musculares cercanas al electrodo.

Las señales EMG son no estacionarias y varían en amplitud y frecuencia dependiendo del tipo de contracción (isométrica, concéntrica o excéntrica), la fatiga muscular, la temperatura, y otros factores fisiológicos.
Generalmente, estas señales se encuentran en un rango de frecuencia entre 10 Hz y 500 Hz, con una mayor concentración de energía alrededor de los 100-150 Hz.

## 2. Fatiga Muscular:

La fatiga muscular se define como la disminución progresiva de la capacidad de generar fuerza o tensión en un músculo, como resultado de una actividad prolongada o repetitiva.
Desde el punto de vista fisiológico, ocurre debido a la acumulación de metabolitos (como ácido láctico) y la reducción en la eficiencia de la transmisión neuromuscular.
En términos electromiográficos, la fatiga se manifiesta en dos cambios característicos en la señal EMG:

Desplazamiento del contenido espectral hacia bajas frecuencias → la frecuencia media disminuye.

Variaciones en la amplitud de la señal (RMS) → el músculo puede aumentar o disminuir la actividad de las unidades motoras según el grado de fatiga.

Estos parámetros permiten cuantificar objetivamente la fatiga mediante el procesamiento digital de la señal EMG.

## 3. Análisis en el Dominio del Tiempo – RMS (Root Mean Square):

El RMS (Root Mean Square) es una medida del valor eficaz o energía de la señal en el dominio del tiempo.
En una señal EMG, el RMS refleja el nivel de activación muscular, ya que aumenta conforme se reclutan más unidades motoras o aumenta la frecuencia de disparo.
Sin embargo, durante la fatiga, puede observarse una disminución del RMS si el músculo pierde capacidad contráctil o una tendencia al aumento temporal cuando se intenta compensar la pérdida de fuerza.

Matemáticamente se define como:
                                   <img width="166" height="74" alt="image" src="https://github.com/user-attachments/assets/f9e239d7-736d-4e6b-a3f7-f81191f6a59e" />
                                   
donde 𝑥𝑖 son las muestras de la señal y 𝑁 es el número total de muestras del segmento analizado.

## 4. Análisis en el Dominio de la Frecuencia – Transformada Rápida de Fourier (FFT):

Para observar los componentes espectrales de la señal EMG se aplica la Transformada Rápida de Fourier (FFT), que convierte la señal del dominio del tiempo al dominio de la frecuencia.
Esto permite analizar cómo se distribuye la energía de la señal en diferentes frecuencias.

La FFT se define como:
                                <img width="191" height="61" alt="image" src="https://github.com/user-attachments/assets/1e0a5afe-26cb-4a0a-8455-9ecd3075cbcf" />
                                
A partir del espectro obtenido, se calculan indicadores relevantes como:

Frecuencia media (𝑓𝑚𝑒𝑎𝑛): promedio ponderado de las frecuencias.
                               <img width="148" height="54" alt="image" src="https://github.com/user-attachments/assets/d09e1552-09ec-4a31-be49-338873d55c24" />
                               
Frecuencia mediana (𝑓𝑚𝑒𝑑𝑖𝑎𝑛): frecuencia que divide el espectro en dos partes con igual energía.

Durante la fatiga muscular, ambas frecuencias tienden a disminuir, indicando un desplazamiento del espectro hacia bajas frecuencias debido al enlentecimiento de la conducción eléctrica muscular.

## 5. Procesamiento Digital y Adquisición (DAQ):

La adquisición de la señal EMG se realiza mediante una interfaz DAQ (Data Acquisition Device) conectada a un sensor EMG de superficie y a electrodos ubicados sobre el músculo de interés (por ejemplo, el bíceps braquial).
El DAQ convierte la señal analógica capturada en una señal digital para su procesamiento en software como Python (Spyder).

Una vez digitalizada, la señal pasa por etapas de:

Filtrado → eliminación de ruido de red (50/60 Hz) y artefactos de movimiento.

Segmentación temporal → análisis en ventanas de tiempo para evaluar la evolución de la fatiga.

Cálculo de RMS y FFT → obtención de los indicadores de fatiga en cada segmento.

## 6. Interpretación General:

Si el RMS disminuye → indica una reducción de la actividad muscular (fatiga avanzada).

Si la frecuencia media o mediana disminuye → se evidencia una fatiga fisiológica progresiva.

Si ambas cambian simultáneamente → el músculo entra en un estado de agotamiento neuromuscular, observable tanto en el dominio del tiempo como en el de la frecuencia.

# METODOLOGIA ANALISIS Y RESULTADOS.

En esta primera contracción, se observa una señal de amplitud elevada y forma estable, correspondiente a una activación muscular sin signos de fatiga.
La aplicación de la ventana Hanning suaviza los extremos del segmento temporal, reduciendo el efecto de fugas espectrales en la FFT.

<img width="1500" height="900" alt="EMG_20251024_142002_contraccion_1" src="https://github.com/user-attachments/assets/d0eaf861-b591-4f5b-a254-cb4c4f846759" />

El espectro de frecuencia muestra un pico principal entre 40 y 100 Hz, rango típico de las señales EMG saludables.
La energía se distribuye de forma amplia, indicando una activación muscular eficiente y sin pérdida de componentes de alta frecuencia.

Durante la segunda contracción, la amplitud se mantiene estable pero con una ligera disminución respecto a la primera.
La señal filtrada conserva buena morfología, lo que indica un correcto contacto de los electrodos y activación voluntaria controlada.

<img width="1500" height="900" alt="EMG_20251024_142002_contraccion_2" src="https://github.com/user-attachments/assets/05ddbafa-f4c3-417e-ab4b-cc6c65e8f91b" />

El espectro presenta un leve desplazamiento del pico hacia frecuencias más bajas (~30–80 Hz), lo cual podría sugerir inicio de fatiga muscular leve, ya que la frecuencia media tiende a disminuir con el tiempo.

La tercera contracción presenta una reducción en la amplitud máxima y un patrón más irregular, posiblemente asociado al desgaste fisiológico del músculo o a la pérdida de sincronización en las fibras musculares.

<img width="1500" height="900" alt="EMG_20251024_142002_contraccion_3" src="https://github.com/user-attachments/assets/73ec9016-ec56-4dc4-b68f-bcaed058a20a" />

El espectro de frecuencia evidencia una mayor concentración de energía en frecuencias bajas (<70 Hz), confirmando una tendencia descendente en la frecuencia media típica de la aparición de fatiga muscular.

En la cuarta contracción se acentúa la caída de amplitud y se observa una recuperación más lenta del tono basal, lo que indica menor capacidad de contracción y mayor esfuerzo neuromuscular.

<img width="1500" height="900" alt="EMG_20251024_142002_contraccion_4" src="https://github.com/user-attachments/assets/296c60ad-64d1-411e-b797-3d6ae5e1f36e" />

El espectro se aplana progresivamente y pierde componentes de alta frecuencia (>150 Hz), lo que refuerza el indicio de progresión de la fatiga y menor reclutamiento de unidades motoras rápidas.

La quinta contracción muestra la menor amplitud de todas y una forma de onda más dispersa. El músculo ha alcanzado un estado avanzado de fatiga, evidenciado por la reducción significativa en la fuerza generada.

<img width="1500" height="900" alt="EMG_20251024_142002_contraccion_5" src="https://github.com/user-attachments/assets/825e526b-ec65-469f-a885-7c90425071d9" />

El espectro confirma una dominancia de bajas frecuencias (20–60 Hz), con pérdida casi total de los componentes de alta frecuencia.
Esta condición refleja un descenso claro en la frecuencia media (f_med), lo cual es un marcador clásico de fatiga muscular.

## Comparación de la Señal Filtrada y Suavizada

En esta etapa la señal cruda se sometió a un filtrado pasaaltas de 20 Hz y un pasabajas de 450 Hz para eliminar interferencias de baja frecuencia (movimiento) y ruido de red.
Posteriormente, se aplicó un suavizado por media móvil para destacar las zonas de mayor actividad muscular.

<img width="1800" height="600" alt="EMG_20251024_142002_filtrada_vs_suavizada" src="https://github.com/user-attachments/assets/a41b4bf7-2025-4293-9ee3-5959cc9a4bc0" />

En la figura se observa cómo la señal suavizada (naranja) mantiene la forma general de la señal filtrada (azul), pero con una reducción de ruido. Las zonas resaltadas en gris representan las ventanas de contracción muscular detectadas automáticamente por el algoritmo. Estas ventanas corresponden a momentos donde la amplitud RMS supera un umbral relativo, indicando activación muscular.
El procesamiento permitió obtener un registro más limpio y estable para el análisis espectral posterior.

## Evolución de la Frecuencia Mediana

La frecuencia mediana (f_med) es un indicador clásico del nivel de fatiga muscular. A medida que el músculo se fatiga, la frecuencia mediana del espectro EMG tiende a desplazarse hacia valores más bajos, debido al reclutamiento de fibras más lentas y a la reducción de la velocidad de conducción muscular.

<img width="1500" height="600" alt="EMG_20251024_142002_fmed_global" src="https://github.com/user-attachments/assets/219def45-1efe-40c3-85f3-6cb0f330094f" />

El gráfico muestra la evolución temporal de la frecuencia mediana calculada en ventanas deslizantes de 2 s con un traslape del 50 %.
Se observa que la frecuencia media oscila alrededor de los 43–45 Hz, sin una tendencia descendente significativa (pendiente = -0.04 Hz/s, p = 0.737).
Esto sugiere que, durante los 60 s de contracciones intermitentes, no se evidencia una fatiga muscular considerable, posiblemente por la corta duración del esfuerzo o por el tiempo de recuperación entre contracciones.

## Prueba de Hipótesis entre la Primera y Última Contracción

Para evaluar cuantitativamente la presencia de fatiga, se compararon las frecuencias medias espectrales de la primera y la última contracción usando una prueba t de Student para muestras independientes.

<img width="1200" height="750" alt="EMG_20251024_142002_prueba_t_1_vs_ultima" src="https://github.com/user-attachments/assets/315b8397-645f-4c88-9cce-30f4738dce34" />

El valor calculado de t = -0.4525 se encuentra dentro de la región de no rechazo (líneas grises), indicando que no hay diferencias estadísticamente significativas entre ambas contracciones (α = 0.05).
Esto confirma los resultados observados en la figura anterior: la señal EMG mantiene su contenido frecuencial a lo largo del ensayo, evidenciando una ausencia de fatiga muscular relevante.



# CONCLUSIONES

La señal EMG adquirida con la DAQ y los electrodos presenta buena calidad y permite diferenciar claramente las contracciones musculares.

El filtrado y suavizado fueron esenciales para eliminar artefactos de movimiento y ruido de línea.

El análisis espectral mediante FFT y la aplicación de la ventana de Hanning permitieron observar el contenido de frecuencia de cada contracción, encontrando componentes principales entre 50 Hz y 150 Hz.

La frecuencia mediana no mostró disminución significativa con el tiempo, lo que indica ausencia de fatiga evidente durante el protocolo.

La metodología es válida para implementar un sistema de evaluación electromiográfica de fatiga muscular en tiempo real, útil en rehabilitación y ergonomía.

