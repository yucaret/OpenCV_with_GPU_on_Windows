# OpenCV_with_GPU_on_Windows

- Crear una carpeta en C: llamada "opencv-gpu".

- Descargar dentro de la carpeta creada las versiones source de opencv, en mi caso la he descargado de la página de opencv https://opencv.org/releases/ la versión 4.5.3:
  ![image](https://user-images.githubusercontent.com/31372472/140824898-047988e4-e6d6-4b3b-99b5-c84e4435d910.png)

- Decargar dentro de la carpeta creada el opencv-contribution para la versión que opencv que haz descargado, en mi caso la he bajado del github https://github.com/opencv/opencv_contrib la versión 4.x:
  ![image](https://user-images.githubusercontent.com/31372472/140825775-848b900f-6758-48ca-a642-dcd7d4366985.png)

- Descomprimir los dos .zip y crear una carpeta llamada "build", debe tener el siguiente formato:
  ![image](https://user-images.githubusercontent.com/31372472/140826316-1e91f286-9fdc-4a20-a1a6-0b0470ca07a5.png)

- Abrir el CMake y configurar las siguientes rutas:
  ![image](https://user-images.githubusercontent.com/31372472/140827697-0b1963e9-939d-4474-b79e-4a46dee8b8c3.png)
  
- Luego dar click en "Configure", donde saldrá otra ventana pop up y donde se debe de configurar de la siguiente manera y finalmente darle finish:
  ![image](https://user-images.githubusercontent.com/31372472/140828744-5fb4cc0a-80b5-4459-919f-8a3805a2833b.png)
  
- Cuando culmine de configurar nos saldrá este resultado, a partir de aquí debemos de continuar la configuración, sobre todo el python donde debe de instalar, en su defecto aparecio el python que no es de anaconda:
  ![image](https://user-images.githubusercontent.com/31372472/140830463-f4d44ba7-cabf-41b1-aba5-8e916dd2b3f7.png)
  
- Configuramos el python donde quiero instalar el opencv, en mi caso lo quiero instalar en el ambiente de anaconda que he creado llamado "pythonGPU":
  ![image](https://user-images.githubusercontent.com/31372472/140833069-696c0814-8590-4f93-ae0e-66f4ca0c66d3.png)

- Configuramos la variable "BUILD_opencv_world" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140833162-9b6b40f3-c0f4-4e3f-9522-89d1810f2d2d.png)

- Configuramos la variable "WITH_CUDA" y "OPENCV_DNN_CUDA", a ambas le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140833972-20f9228a-1564-4223-b411-e164a329ce37.png)

- Configuramos la variable "OPENCV_ENABLE_NONFREE" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140834467-1aacfcc8-6381-4c51-a2d3-72cb21a139c9.png)

- Configuramos la variable "ENABLE_FAST_MATH" y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140834953-bf84979c-ed9b-4552-b730-2b43e7a14f9e.png)

- Configuramos las variables INSTALL_PYTHON_EXAMPLES, INSTALL_C_EXAMPLES y BUILD_EXAMPLES , a todas le quitamos el check.
  ![image](https://user-images.githubusercontent.com/31372472/140835620-5c1d1f02-fb07-4c5f-9e9f-bf765fabbace.png)

- Damos click en "Configure" y esperamos a las siguientes configuraciones:
  ![image](https://user-images.githubusercontent.com/31372472/140836326-e49bf59c-fb2e-4a3a-a5bc-f4b44501dc1d.png)
  
- El proceso va a generar un error, el cual le damos ok y empezamos a configurar nuevamente:
  ![image](https://user-images.githubusercontent.com/31372472/140836596-8339ecfb-1d40-4303-9bbf-fa1d01a163ef.png)

- Verificamos que la variable WITH_CUDNN este con check, si no tiene le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140837001-0128ce2d-d97c-447b-8473-ec7b7f3dd4c6.png)

- Verificamos que la variable WITH_CUBLAS este con check, si no tiene le damos chech:
  ![image](https://user-images.githubusercontent.com/31372472/140837488-ac193bc0-01dc-48ab-9206-808fb9ba70fb.png)

- Configuramos la variable CUDA_FAST_MATH y le damos check:
  ![image](https://user-images.githubusercontent.com/31372472/140837626-eddff181-c23a-4d27-b7e8-1bad06565ca4.png)

- Para configurar la siguiente variable primero debes de conocer producto de nvidea tienes en tu pc, los puedes buscar en administrador de dispositivo, luego de conocerlo buscas tu producto en la página de nvidea (https://developer.nvidia.com/cuda-gpus) y luego conociendo la capacidad la colocas en la configuración del Cmake:
 
  Aquí verificamos que tipo de producto tenemos
  ![image](https://user-images.githubusercontent.com/31372472/140841750-0bf335e4-1912-404b-a5df-5c7a73c9a8b0.png)

  Aquí verificamos la capacidad del producto (https://developer.nvidia.com/cuda-gpus), en mi caso tengo un GeForce 940 MX, como en la página existe 940 M, utilizare su capacidad de 5.0 para las configuraciones:
  ![image](https://user-images.githubusercontent.com/31372472/140633626-37af1847-ab9e-42f1-8e47-d63b965f8302.png)
  
  Aquí configuramos la capacidad en CMAKE en la variable CUDA_ARCH_BIN
  ![image](https://user-images.githubusercontent.com/31372472/140841568-6c41739a-fa5e-4495-9c4e-b81da64bbba9.png)
  
- Configuramos la variable OPENCV_EXTRA_MODULES_PATH y allí colocamos la ruta del modulo del opencv_contrib (en mi caso es C:\opencv-gpu\opencv_contrib-4.x\modules):

  ![image](https://user-images.githubusercontent.com/31372472/140843017-58e0bc33-0f5f-48ec-8773-0b8881804dd7.png)

- Damos click en "Configure" y esperamos:
  ![image](https://user-images.githubusercontent.com/31372472/140843894-781e5ba4-63c6-49a3-bcd7-a99261ec566a.png)






 
- Damos click derecho en ALL_BULD y compilar (el proceso tarda aproximadamente 6 horas):
  ![image](https://user-images.githubusercontent.com/31372472/140610569-54ca4014-89c5-4489-a451-325b817f95f2.png)

  ![image](https://user-images.githubusercontent.com/31372472/140610622-14cb59a9-01f0-402f-a372-185cdf8d76eb.png)

- Cuando finaliza la compilación sale este resultado:
  ![image](https://user-images.githubusercontent.com/31372472/140610516-358ccfea-1b20-4239-b456-156e88fd12e0.png)

- Damos click derecho en INSTALL y compilar (demora unos segundos)
  ![image](https://user-images.githubusercontent.com/31372472/140618123-b003bc68-ec60-46c7-85b9-fca17560903f.png)

  ![image](https://user-images.githubusercontent.com/31372472/140618146-38e5d562-8881-47cb-9ed1-5a2f3ee3c27b.png)

- Cuando finaliza la compilación sale este resultado:
  ![image](https://user-images.githubusercontent.com/31372472/140784906-21e049c6-5bfe-4ef0-b74f-d37bf93c2914.png)
  
- Para verifica la instalación ingresamos a Python e importamos opencv y vemos la informaci+on de Cuda Instalado

  ![image](https://user-images.githubusercontent.com/31372472/140645225-ab7ed305-a844-404a-840a-a9d77599aeb8.png)
  
  ![image](https://user-images.githubusercontent.com/31372472/140645261-5d8d7493-fcc7-4e69-961f-e3bf016114f7.png)
