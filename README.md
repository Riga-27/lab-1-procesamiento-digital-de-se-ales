primero se importan las liberias wfdb para la utilizacion de las señales descargadas desde PhysioNet
importar matplotlib para desarrollar los graficos
importar numpy para la manipulacion numerica
declara las variables pertinentes
cargar la señal obtenida la cual en este caso fue una deteccion de frecuencia cardiaca fetal por ultrasonico
mediante el codigo signal= wfdb('nombrearchivo') se carga la señal
se sacan los calculos y funcion de la media
donde la media es igual media=suma/cont donde suma es la suma de los valores obtenidos y cont es la cantidad de los valores totales
Media con funcion es igual a media=np.mean(valores)
se plotean ambas graficas donde se indican los ejes donde el eje x es muestra y el eje y es amplitud
se calcula la desviacion estandar donde ya con la media se calcula el cuadrado de la distancia y se divide sobre cont
la funcion de desviacion es igual desv=np.std(valores)
para el coeficiente de variacion se divide la desviacion sobre la media y se multiplica por 100
se plotean cada una de los datos obtenidos tanto formula como con funcion
histograma se usa para encontrarun rango y definir los intervalos con max y min y se crea una lista para guardar las frecuencias, se cuenta los limites de los intervalos y se plotea
para la obtencion de la funcion de probabilidad donde es una funcion que devuelve la probabilidad de que una variable aleatoria discreta sea exactamente igual a algun valor, se uso que es igual a la frecuencia dividido el cont por los intervalos
funcion plt.plot(bins[:-1], probabilidad, label='Función de Probabilidad')
para la obtencion de la SNR debemos saber primero que es, es un indicador de la señal,donde un mayor valor sugiere una menor calidad de la informacion obtenida y un menor valor podria indicar una dificultad para discernir la señal de interes
se genera un ruido gaussiano mediante 
vectores = valores.flatten()
ruido_gaussiano = np.random.normal(0, 1, len(vectores))
se normaliza el ruido para que se ajustar el nivel del volumen
se saca el ruido impulso es un sonido que se caracteriza por picos repentinos y de corta duracion en la presion de sonido
impulsos = int(0.0002*len(valores))# Número de impulsos, ajusta este valor según sea necesario
indices = np.random.choice(len(valores), impulsos, replace=False)
ruido_impulso = np.copy(vectores)
ruido_impulso[indices] = np.max(vectores)
