# Lab-4-Se-ales-Se-ales-EMG
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










