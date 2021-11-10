# Configuración de OpenCV con GPU en Anaconda con Windows

Como configurar el OpenCV con GPU e instalarlo en un ambiente de Anaconda sobre la plataforma de Windows.
## Requerimiento Iniciales:

## Pasos a seguir:

- Primero debes de crear la carpeta donde vas a descargar el OpenCV, yo lo voy a crear en C: y se llama "opencv-gpu".

- Luego descargar dentro de la carpeta creada las versiones source de opencv, en mi caso la he descargado de la página de opencv https://opencv.org/releases/ la versión 4.5.3:
  ![image](https://user-images.githubusercontent.com/31372472/140824898-047988e4-e6d6-4b3b-99b5-c84e4435d910.png)

- Además decargar dentro de la misma carpeta el opencv-contribution para la versión de opencv que haz descargado, en mi caso la he bajado del github https://github.com/opencv/opencv_contrib la versión 4.x:
  ![image](https://user-images.githubusercontent.com/31372472/140872837-355aa33b-cfa0-419f-991e-70d7ee6342d1.png)

- Descomprimir ambos zip y creamos una carpeta adicional llamada "build", al final debe de quedar en el siguiente formato:
  ![image](https://user-images.githubusercontent.com/31372472/140826316-1e91f286-9fdc-4a20-a1a6-0b0470ca07a5.png)
  
- Luego abrimos el prompt de Anaconda y creamos un ambiente (yo recomiendo instalar opencv en un ambiente nuevo debido a que las librerias ya instaladas en un ambiente existente puede causar conflictos en la configuración e instalación), llamare mi ambiente con "pythonGPU" y lo voy a crear con la versión de python 3.8.5 utilizando el comando "conda create -n pythonGPU python=3.8.5":
  ![image](https://user-images.githubusercontent.com/31372472/141039733-effd5142-c26a-4dc2-9ae9-bd423a3eb17e.png)

- Ingresamos al ambiente creado e instalamos el numpy con el comando "conda install numpy" y cerramos:
  ![image](https://user-images.githubusercontent.com/31372472/141039859-3cf61ac2-bdce-499f-9835-955f1a2210c0.png)

- Luego abrimos el CMake y realizamos configurar las siguientes configuraciones de carpetas:
  ![image](https://user-images.githubusercontent.com/31372472/140827697-0b1963e9-939d-4474-b79e-4a46dee8b8c3.png)

- Luego agregamos las variable con rutas del python del ambiente que creamos, y donde queremos instalar el opencv; en mi caso las entradas con las rutas son:
  * PYTHON3_EXECUTABLE         = C:/Users/WIN/anaconda3/envs/pythonGPU/python.exe
  * PYTHON3_INCLUDE_DIR        = C:/Users/WIN/anaconda3/envs/pythonGPU/include
  * PYTHON3_LIBRARY            = C:/Users/WIN/anaconda3/envs/pythonGPU/libs/python38.lib
  * PYTHON3_LIBRARIES          = C:/Users/WIN/anaconda3/envs/pythonGPU/libs/python38.lib
  * PYTHON3_NUMPY_INCLUDE_DIRS = C:/Users/WIN/anaconda3/envs/pythonGPU/Lib/site-packages/numpy/core/include
  * PYTHON3_PACKAGES_PATH      = C:/Users/WIN/anaconda3/envs/pythonGPU/Lib/site-packages
  
  La forma de agregar las variable es de la siguiente manera, y lo debes de hacer con las 6 variables mostradas arriba:
  ![image](https://user-images.githubusercontent.com/31372472/141041406-d85b67a1-ac1b-459f-aa19-97b1c85e8a7c.png)

- Luego dar click en "Configure", donde saldrá otra ventana pop up y donde se debe de configurar de la siguiente manera y finalmente darle finish:
  ![image](https://user-images.githubusercontent.com/31372472/140828744-5fb4cc0a-80b5-4459-919f-8a3805a2833b.png)

- Configuramos la variable "BUILD_opencv_world" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140833162-9b6b40f3-c0f4-4e3f-9522-89d1810f2d2d.png)

- Configuramos la variable "WITH_CUDA" y "OPENCV_DNN_CUDA", a ambas le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140833972-20f9228a-1564-4223-b411-e164a329ce37.png)

- Configuramos la variable "OPENCV_ENABLE_NONFREE" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140834467-1aacfcc8-6381-4c51-a2d3-72cb21a139c9.png)

- Configuramos la variable "ENABLE_FAST_MATH" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140834953-bf84979c-ed9b-4552-b730-2b43e7a14f9e.png)

- Configuramos las variables "INSTALL_PYTHON_EXAMPLES", "INSTALL_C_EXAMPLES" y "BUILD_EXAMPLES" , a todas le quitamos el check.
  ![image](https://user-images.githubusercontent.com/31372472/140835620-5c1d1f02-fb07-4c5f-9e9f-bf765fabbace.png)
  
- Configuramos la variable "OPENCV_EXTRA_MODULES_PATH" y allí colocamos la ruta del modulo del opencv_contrib (en mi caso es C:\opencv-gpu\opencv_contrib-4.x\modules):

  ![image](https://user-images.githubusercontent.com/31372472/140843017-58e0bc33-0f5f-48ec-8773-0b8881804dd7.png)

- Damos click en "Configure" y esperamos a las siguientes configuraciones:
  ![image](https://user-images.githubusercontent.com/31372472/140836326-e49bf59c-fb2e-4a3a-a5bc-f4b44501dc1d.png)
  
- El proceso va a generar un error, el cual le damos ok y empezamos a configurar nuevamente:
  ![image](https://user-images.githubusercontent.com/31372472/140836596-8339ecfb-1d40-4303-9bbf-fa1d01a163ef.png)

- Verificamos que la variable "WITH_CUDNN" este con check, si no tiene le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140837001-0128ce2d-d97c-447b-8473-ec7b7f3dd4c6.png)

- Verificamos que la variable "WITH_CUBLAS" este con check, si no tiene le damos chech:
  ![image](https://user-images.githubusercontent.com/31372472/140837488-ac193bc0-01dc-48ab-9206-808fb9ba70fb.png)

- Configuramos la variable "CUDA_FAST_MATH" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140837626-eddff181-c23a-4d27-b7e8-1bad06565ca4.png)

- Para configurar la variable "CUDA_ARCH_BIN" primero debes de conocer el producto de nvidea que tienes en tu pc, esste lo puedes buscar en administrador de dispositivo:
  ![image](https://user-images.githubusercontent.com/31372472/140841750-0bf335e4-1912-404b-a5df-5c7a73c9a8b0.png)

  Luego verificamos la capacidad del producto (https://developer.nvidia.com/cuda-gpus), en mi caso tengo un GeForce 940 MX, como en la página existe 940 M, utilizare su capacidad de 5.0 para las configuraciones:
  ![image](https://user-images.githubusercontent.com/31372472/140633626-37af1847-ab9e-42f1-8e47-d63b965f8302.png)
  
  Finalmente configuramos la variable "CUDA_ARCH_BIN".
  ![image](https://user-images.githubusercontent.com/31372472/140841568-6c41739a-fa5e-4495-9c4e-b81da64bbba9.png)

- Damos click en "Configure" y esperamos:
  ![image](https://user-images.githubusercontent.com/31372472/140843894-781e5ba4-63c6-49a3-bcd7-a99261ec566a.png)

- Se va a generar el siguiente error, en este caso para evitarlo hay que quitarle el check a la variale OPENCV_GENERATE_SETUPVARS.

  ![image](https://user-images.githubusercontent.com/31372472/140845110-0cdc7e3d-6fc3-4548-987e-b8870735ef0e.png)
  
  ![image](https://user-images.githubusercontent.com/31372472/140845212-9f5206aa-a7c5-4469-b5a4-64ba39074d6f.png)

- Damos click en configurar y verificamos que no se de ningún mensaje en rojo, y verificamos las configuraciones más importantes, python y cuda:

  ![image](https://user-images.githubusercontent.com/31372472/141039346-e0719cef-3b9b-49bd-90e3-5e48e03a4217.png)
  
  ![image](https://user-images.githubusercontent.com/31372472/140869366-a957ff29-f2f8-4fc7-81a5-b4d0d977e741.png)
  
- Luego de ver que no exista ningún error o mensaje en rojo en la configuración, damos click en "Generate":
  ![image](https://user-images.githubusercontent.com/31372472/140873468-1af93146-df6f-455b-929a-9c1b2e797936.png)

- Cerramos CMake y vamos a la carpeta del Build de Opencv, damos click derecho en "ALL_BUILD" y abrimos con Visual Studio 2019:
  ![image](https://user-images.githubusercontent.com/31372472/140874369-51071696-3ede-43f0-b817-dd329bd4816d.png)

- Damos click derecho en ALL_BUILD y compilar (el proceso tarda aproximadamente 5 horas):
  ![image](https://user-images.githubusercontent.com/31372472/140610569-54ca4014-89c5-4489-a451-325b817f95f2.png)

  ![image](https://user-images.githubusercontent.com/31372472/140610622-14cb59a9-01f0-402f-a372-185cdf8d76eb.png)

- Cuando finaliza la compilación sale este resultado:
  ![image](https://user-images.githubusercontent.com/31372472/141052868-7aee5dc5-2e92-49c6-80cd-a76d4f68d2df.png)

- Damos click derecho en INSTALL y compilar (demora unos segundos)
  ![image](https://user-images.githubusercontent.com/31372472/140618123-b003bc68-ec60-46c7-85b9-fca17560903f.png)

  ![image](https://user-images.githubusercontent.com/31372472/140618146-38e5d562-8881-47cb-9ed1-5a2f3ee3c27b.png)

- Cuando finaliza la compilación de la instlación sale el siguiente resultado:
  ![image](https://user-images.githubusercontent.com/31372472/141053112-fb19a0e2-fa54-49ae-b48d-72a5ed7af5b2.png)
  
- Para verifica la instalación ingresamos a Python e importamos opencv y vemos la informaci+on de Cuda Instalado

  ![image](https://user-images.githubusercontent.com/31372472/141053402-480770fb-0f28-48be-a5a4-c81e938986ac.png)
  
  ![image](https://user-images.githubusercontent.com/31372472/141053625-dcbf1ceb-dbd3-4ccd-9890-8fc22a21e267.png)
