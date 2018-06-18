<?xml version="1.0"?>
<xliff version="1.2" xmlns="urn:oasis:names:tc:xliff:document:1.2" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="urn:oasis:names:tc:xliff:document:1.2 xliff-core-1.2-transitional.xsd">
  <file datatype="xml" original="markdown" source-language="en-US" target-language="zh-CN">
    <header>
      <tool tool-id="mdxliff" tool-name="mdxliff" tool-version="1.0-e3f239f" tool-company="Microsoft"/>
    </header>
    <body>
      <group id="content" extype="content">
        <trans-unit id="101" translate="yes" xml:space="preserve" restype="x-metadata">
          <source>Clasificación de imágenes con CNTK en Azure Machine Learning Workbench | Microsoft Docs</source>
        </trans-unit>
        <trans-unit id="102" translate="yes" xml:space="preserve" restype="x-metadata">
          <source>Use Azure ML Workbench para probar, evaluar e implementar un modelo personalizado de clasificación de imágenes.</source>
        </trans-unit>
        <trans-unit id="103" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="image-classification-using-azure-machine-learning-workbench"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Clasificación de imágenes con Azure Machine Learning Workbench</source>
        </trans-unit>
        <trans-unit id="104" translate="yes" xml:space="preserve">
          <source>Se pueden usar distintos métodos de clasificación de imágenes para resolver un gran número de problemas de Computer Vision.</source>
        </trans-unit>
        <trans-unit id="105" translate="yes" xml:space="preserve">
          <source>Esto incluye la creación de modelos que respondan preguntas del tipo <bpt id="p1">*</bpt>¿Hay un OBJETO en la imagen?<ept id="p1">*</ept>, donde OBJETO puede ser, por ejemplo, un <bpt id="p2">*</bpt>perro<ept id="p2">*</ept>, un <bpt id="p3">*</bpt>coche<ept id="p3">*</ept> o un <bpt id="p4">*</bpt>barco<ept id="p4">*</ept>.</source>
        </trans-unit>
        <trans-unit id="106" translate="yes" xml:space="preserve">
          <source>O a preguntas más complejas, como <bpt id="p1">*</bpt>¿Qué gravedad de enfermedad ocular revela el escáner de retina de este paciente?<ept id="p1">*</ept></source>
        </trans-unit>
        <trans-unit id="107" translate="yes" xml:space="preserve">
          <source>En este tutorial se abordan estos problemas.</source>
        </trans-unit>
        <trans-unit id="108" translate="yes" xml:space="preserve">
          <source>En él explicamos cómo entrenar, evaluar e implementar su propio modelo de clasificación de imágenes usando <bpt id="p1">[</bpt>Microsoft Cognitive Toolkit (CNTK)<ept id="p1">](https://docs.microsoft.com/cognitive-toolkit/)</ept> para el aprendizaje profundo.</source>
        </trans-unit>
        <trans-unit id="109" translate="yes" xml:space="preserve">
          <source>Se incluyen imágenes de ejemplo, si bien el lector puede aportar su propio conjunto de datos y entrenar modelos personalizados de su cosecha.</source>
        </trans-unit>
        <trans-unit id="110" translate="yes" xml:space="preserve">
          <source>Las soluciones de Computer Vision solían requerir un conocimiento de experto para identificar e implementar manualmente las llamadas <bpt id="p1">*</bpt>características<ept id="p1">*</ept>, que resaltan la información deseada en imágenes.</source>
        </trans-unit>
        <trans-unit id="111" translate="yes" xml:space="preserve">
          <source>Este método manual cambió en 2012 con el famoso artículo de <bpt id="p1">[</bpt>AlexNet<ept id="p1">](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)</ept> [1] sobre aprendizaje profundo y, en la actualidad, se usan redes neuronales profundas (DNN) para encontrar estas características automáticamente.</source>
        </trans-unit>
        <trans-unit id="112" translate="yes" xml:space="preserve">
          <source>Las DNN supusieron una notable mejora en el campo no ya de la clasificación de imágenes, sino también para acabar con diversos problemas de Computer Vision como la detección de objetos y la similitud de imágenes.</source>
        </trans-unit>
        <trans-unit id="113" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="link-to-the-gallery-github-repository"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Vínculo al repositorio de GitHub de la galería</source>
        </trans-unit>
        <trans-unit id="114" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="overview"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Información general</source>
        </trans-unit>
        <trans-unit id="115" translate="yes" xml:space="preserve">
          <source>Este tutorial se divide en tres partes:</source>
        </trans-unit>
        <trans-unit id="116" translate="yes" xml:space="preserve">
          <source>En la parte 1 se muestra cómo entrenar, evaluar e implementar un sistema de clasificación de imágenes, usando para ello una DNN ya entrenada para la captura de características y probando un SVM en la salida.</source>
        </trans-unit>
        <trans-unit id="117" translate="yes" xml:space="preserve">
          <source>En la parte 2 siguiente se indica cómo mejorar la precisión, por ejemplo, perfeccionando la DNN en lugar de usarla para la captura de características.</source>
        </trans-unit>
        <trans-unit id="118" translate="yes" xml:space="preserve">
          <source>En la parte 3 se describe cómo puede usar un conjunto de datos de su cosecha en lugar de las imágenes de ejemplo suministradas y, si es necesario, cómo generar su propio conjunto de datos extrayendo imágenes de Internet.</source>
        </trans-unit>
        <trans-unit id="119" translate="yes" xml:space="preserve">
          <source>No se requiere experiencia previa de aprendizaje automático y CNTK, pero sí resulta útil para comprender los principios subyacentes.</source>
        </trans-unit>
        <trans-unit id="120" translate="yes" xml:space="preserve">
          <source>La precisión de los números, la duración del entrenamiento y otras cuestiones reflejadas en el tutorial se incluyen exclusivamente a modo de referencia; de igual modo, los valores reales que se obtengan al ejecutar el código variarán casi con toda seguridad.</source>
        </trans-unit>
        <trans-unit id="121" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="prerequisites"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>requisitos previos</source>
        </trans-unit>
        <trans-unit id="122" translate="yes" xml:space="preserve">
          <source>Los requisitos previos para ejecutar este ejemplo son los siguientes:</source>
        </trans-unit>
        <trans-unit id="123" translate="yes" xml:space="preserve">
          <source>Una <bpt id="p1">[</bpt>cuenta de Azure<ept id="p1">](https://azure.microsoft.com/free/)</ept> (hay disponibles versiones gratuitas de prueba).</source>
        </trans-unit>
        <trans-unit id="124" translate="yes" xml:space="preserve">
          <source>Una instalación de <bpt id="p1">[</bpt>Azure Machine Learning Workbench<ept id="p1">](../service/overview-what-is-azure-ml.md)</ept> siguiendo la <bpt id="p2">[</bpt>Guía de instalación de inicio rápido<ept id="p2">](../service/quickstart-installation.md)</ept> para instalar el programa y crear un área de trabajo.</source>
        </trans-unit>
        <trans-unit id="125" translate="yes" xml:space="preserve">
          <source>Un equipo Windows.</source>
        </trans-unit>
        <trans-unit id="126" translate="yes" xml:space="preserve">
          <source>Se necesita un sistema operativo Windows porque Workbench admite únicamente Windows y Mac OS, mientras que Microsoft Cognitive Toolkit (que usaremos como biblioteca de aprendizaje profundo) solo es compatible con Windows y Linux.</source>
        </trans-unit>
        <trans-unit id="127" translate="yes" xml:space="preserve">
          <source>No se necesita una GPU dedicada para ejecutar el entrenamiento de SVM en la parte 1, pero sí para el proceso de perfeccionamiento de la DNN descrito en la parte 2.</source>
        </trans-unit>
        <trans-unit id="128" translate="yes" xml:space="preserve">
          <source>Si no tiene una GPU en condiciones, quiere entrenar en varias GPU o no tiene un equipo con Windows, considere la posibilidad de usar máquina de virtual de aprendizaje profundo de Azure con un sistema operativo Windows.</source>
        </trans-unit>
        <trans-unit id="129" translate="yes" xml:space="preserve">
          <source>Vaya <bpt id="p1">[</bpt>aquí<ept id="p1">](https://azuremarketplace.microsoft.com/marketplace/apps/microsoft-ads.dsvm-deep-learning)</ept> para obtener una guía de implementación con un solo clic.</source>
        </trans-unit>
        <trans-unit id="130" translate="yes" xml:space="preserve">
          <source>Una vez implementada, conéctese a la máquina virtual a través de una conexión de Escritorio remoto, instale Workbench y ejecute el código localmente en ella.</source>
        </trans-unit>
        <trans-unit id="131" translate="yes" xml:space="preserve">
          <source>Es necesario instalar varias bibliotecas de Python, como OpenCV.</source>
        </trans-unit>
        <trans-unit id="132" translate="yes" xml:space="preserve">
          <source>Haga clic en <bpt id="p1">*</bpt>Abrir símbolo del sistema<ept id="p1">*</ept> en el menú <bpt id="p2">*</bpt>Archivo<ept id="p2">*</ept> de Workbench y ejecute los siguientes comandos para instalar estas dependencias:</source>
        </trans-unit>
        <trans-unit id="133" translate="yes" xml:space="preserve">
          <source><ph id="ph1">`pip install opencv_python-3.3.1-cp35-cp35m-win_amd64.whl`</ph> después de descargar OpenCV de <ph id="ph2">http://www.lfd.uci.edu/~gohlke/pythonlibs/</ph> (la versión y el nombre de archivo exactos pueden variar).</source>
        </trans-unit>
        <trans-unit id="134" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="troubleshooting--known-bugs"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Solución de problemas/Errores conocidos</source>
        </trans-unit>
        <trans-unit id="135" translate="yes" xml:space="preserve">
          <source>Se necesita una GPU para la parte 2.</source>
        </trans-unit>
        <trans-unit id="136" translate="yes" xml:space="preserve">
          <source>Si no hay una, cuando trate de perfeccionar la DNN aparecerá un error que indica que el aprendizaje de normalización por lotes todavía no se ha implementado.</source>
        </trans-unit>
        <trans-unit id="137" translate="yes" xml:space="preserve">
          <source>Los errores de memoria insuficiente durante el entrenamiento de DNN se pueden soslayar si se reduce el tamaño del minilote (variable <ph id="ph1">`cntk_mb_size`</ph> en <ph id="ph2">`PARAMETERS.py`</ph>).</source>
        </trans-unit>
        <trans-unit id="138" translate="yes" xml:space="preserve">
          <source>El código se probó con CNTK 2.2 y debería poder ejecutarse tanto en versiones anteriores (hasta 2.0) como en versiones más recientes sin cambios (o solo con cambios mínimos).</source>
        </trans-unit>
        <trans-unit id="139" translate="yes" xml:space="preserve">
          <source>En el momento de redactar este artículo, Azure Machine Learning Workbench generaba problemas a la hora de mostrar blocs de notas superiores a 5 MB.</source>
        </trans-unit>
        <trans-unit id="140" translate="yes" xml:space="preserve">
          <source>Puede haber blocs de notas con este tamaño si se guardan mostrando todas las salidas de celda.</source>
        </trans-unit>
        <trans-unit id="141" translate="yes" xml:space="preserve">
          <source>Si este error se produce, abra un símbolo del sistema en el menú Archivo de Workbench, ejecute <ph id="ph1">`jupyter notebook`</ph>, abra el bloc de notas, borre todas las salidas y guárdelo.</source>
        </trans-unit>
        <trans-unit id="142" translate="yes" xml:space="preserve">
          <source>Una vez hecho esto, el bloc de notas volverá a abrirse correctamente en Azure Machine Learning Workbench.</source>
        </trans-unit>
        <trans-unit id="143" translate="yes" xml:space="preserve">
          <source>Todos los scripts que se proporcionan en este ejemplo tienen que ejecutarse de forma local y no en entornos como, por ejemplo, un entorno remoto de docker.</source>
        </trans-unit>
        <trans-unit id="144" translate="yes" xml:space="preserve">
          <source>Todos los blocs de notas tienen que ejecutarse con el kernel establecido como un kernel del proyecto local denominado "PROJECTNAME local" (por ejemplo, "myImgClassUsingCNTK local").</source>
        </trans-unit>
        <trans-unit id="145" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="create-a-new-workbench-project"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Creación de un nuevo proyecto de Workbench</source>
        </trans-unit>
        <trans-unit id="146" translate="yes" xml:space="preserve">
          <source>Para crear un proyecto usando este ejemplo como plantilla:</source>
        </trans-unit>
        <trans-unit id="147" translate="yes" xml:space="preserve">
          <source>Abra Azure Machine Learning Workbench.</source>
        </trans-unit>
        <trans-unit id="148" translate="yes" xml:space="preserve">
          <source>En la página <bpt id="p1">**</bpt>Proyectos<ept id="p1">**</ept>, haga clic en el signo <bpt id="p2">**</bpt><ph id="ph1">+</ph><ept id="p2">**</ept> y seleccione <bpt id="p3">**</bpt>Nuevo proyecto<ept id="p3">**</ept>.</source>
        </trans-unit>
        <trans-unit id="149" translate="yes" xml:space="preserve">
          <source>En el panel <bpt id="p1">**</bpt>Crear nuevo proyecto<ept id="p1">**</ept>, rellene la información del proyecto nuevo.</source>
        </trans-unit>
        <trans-unit id="150" translate="yes" xml:space="preserve">
          <source>En el cuadro de búsqueda <bpt id="p1">**</bpt>Buscar plantillas de proyecto<ept id="p1">**</ept>, escriba "Image Classification" (Clasificación de imágenes) y seleccione la plantilla.</source>
        </trans-unit>
        <trans-unit id="151" translate="yes" xml:space="preserve">
          <source>Haga clic en <bpt id="p1">**</bpt>Create<ept id="p1">**</ept>(Crear).</source>
        </trans-unit>
        <trans-unit id="152" translate="yes" xml:space="preserve">
          <source>Cuando realice estos pasos, se creará la estructura del proyecto descrita abajo.</source>
        </trans-unit>
        <trans-unit id="153" translate="yes" xml:space="preserve">
          <source>El directorio del proyecto tiene una limitación de tamaño máximo de 25 MB, ya que Azure Machine Learning Workbench crea una copia de esta carpeta después de cada ejecución (para habilitar el historial de ejecución).</source>
        </trans-unit>
        <trans-unit id="154" translate="yes" xml:space="preserve">
          <source>Por lo tanto, todos los archivos temporales y de imagen se guardan en el directorio <bpt id="p1">*</bpt>~/Desktop/imgClassificationUsingCntk_data<ept id="p1">*</ept> (en este documento lo llamaremos <bpt id="p2">*</bpt>DATA_DIR<ept id="p2">*</ept>).</source>
        </trans-unit>
        <trans-unit id="155" translate="yes" xml:space="preserve">
          <source>Carpeta</source>
        </trans-unit>
        <trans-unit id="156" translate="yes" xml:space="preserve">
          <source>DESCRIPCIÓN</source>
        </trans-unit>
        <trans-unit id="157" translate="yes" xml:space="preserve">
          <source>aml_config/</source>
        </trans-unit>
        <trans-unit id="158" translate="yes" xml:space="preserve">
          <source>Directorio que contiene los archivos de configuración de Azure Machine Learning Workbench</source>
        </trans-unit>
        <trans-unit id="159" translate="yes" xml:space="preserve">
          <source>libraries/</source>
        </trans-unit>
        <trans-unit id="160" translate="yes" xml:space="preserve">
          <source>Directorio que contiene todas las funciones auxiliares de Python y Jupyter</source>
        </trans-unit>
        <trans-unit id="161" translate="yes" xml:space="preserve">
          <source>notebooks/</source>
        </trans-unit>
        <trans-unit id="162" translate="yes" xml:space="preserve">
          <source>Directorio que contiene todos los blocs de notas</source>
        </trans-unit>
        <trans-unit id="163" translate="yes" xml:space="preserve">
          <source>resources/</source>
        </trans-unit>
        <trans-unit id="164" translate="yes" xml:space="preserve">
          <source>Directorio que contiene todos los recursos (por ejemplo, direcciones URL de imágenes de moda)</source>
        </trans-unit>
        <trans-unit id="165" translate="yes" xml:space="preserve">
          <source>scripts/</source>
        </trans-unit>
        <trans-unit id="166" translate="yes" xml:space="preserve">
          <source>Directorio que contiene todos los scripts</source>
        </trans-unit>
        <trans-unit id="167" translate="yes" xml:space="preserve">
          <source>PARAMETERS.py</source>
        </trans-unit>
        <trans-unit id="168" translate="yes" xml:space="preserve">
          <source>Script de Python donde se especifican todos los parámetros</source>
        </trans-unit>
        <trans-unit id="169" translate="yes" xml:space="preserve">
          <source>readme.md</source>
        </trans-unit>
        <trans-unit id="170" translate="yes" xml:space="preserve">
          <source>El presente documento Léame</source>
        </trans-unit>
        <trans-unit id="171" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="data-description"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Descripción de los datos</source>
        </trans-unit>
        <trans-unit id="172" translate="yes" xml:space="preserve">
          <source>En este tutorial se usa como ejemplo un conjunto de datos con 428 imágenes de texturas de partes de arriba de ropa.</source>
        </trans-unit>
        <trans-unit id="173" translate="yes" xml:space="preserve">
          <source>Cada imagen está anotada como perteneciente a una de tres posibles texturas distintas (lunares, rayas o leopardo).</source>
        </trans-unit>
        <trans-unit id="174" translate="yes" xml:space="preserve">
          <source>Hemos usado un número de imágenes reducido para que este tutorial sea rápido de ejecutar, pero el código está totalmente probado y funciona con miles de imágenes o más.</source>
        </trans-unit>
        <trans-unit id="175" translate="yes" xml:space="preserve">
          <source>Todas las imágenes se extrajeron con búsquedas de imágenes de Bing y se anotaron a mano tal y como se explica en la <bpt id="p1">[</bpt>parte 3<ept id="p1">](#using-a-custom-dataset)</ept>.</source>
        </trans-unit>
        <trans-unit id="176" translate="yes" xml:space="preserve">
          <source>Las direcciones URL de las imágenes aparecen en el archivo <bpt id="p1">*</bpt>/resources/fashionTextureUrls.tsv<ept id="p1">*</ept> junto con sus correspondientes atributos.</source>
        </trans-unit>
        <trans-unit id="177" translate="yes" xml:space="preserve">
          <source>El script <ph id="ph1">`0_downloadData.py`</ph> descarga todas las imágenes en el directorio <bpt id="p1">*</bpt>DATA_DIR/images/fashionTexture/<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="178" translate="yes" xml:space="preserve">
          <source>Es probable que los vínculos de algunas de las 428 direcciones URL estén rotos.</source>
        </trans-unit>
        <trans-unit id="179" translate="yes" xml:space="preserve">
          <source>Esto no supone un problema y simplemente significa que dispondremos de menos imágenes con las que entrenar y probar.</source>
        </trans-unit>
        <trans-unit id="180" translate="yes" xml:space="preserve">
          <source>Todos los scripts que se proporcionan en este ejemplo tienen que ejecutarse de forma local y no en entornos como, por ejemplo, un entorno remoto de docker.</source>
        </trans-unit>
        <trans-unit id="181" translate="yes" xml:space="preserve">
          <source>En la siguiente ilustración se muestran ejemplos de los atributos de lunares (izquierda), a rayas (centro) y leopardo (derecha).</source>
        </trans-unit>
        <trans-unit id="182" translate="yes" xml:space="preserve">
          <source>Se realizaron las anotaciones pertinentes en función de la prenda de ropa.</source>
        </trans-unit>
        <trans-unit id="183" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="part-1---model-training-and-evaluation"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Parte 1: Entrenamiento y evaluación del modelo</source>
        </trans-unit>
        <trans-unit id="184" translate="yes" xml:space="preserve">
          <source>En la primera parte de este tutorial, entrenaremos un sistema que usa (pero no modifica) una red neuronal profunda ya entrenada.</source>
        </trans-unit>
        <trans-unit id="185" translate="yes" xml:space="preserve">
          <source>Esta DNN ya entrenada se usa para la captura de características, y se entrena una SVM lineal para predecir el atributo (esto es, lunares, rayas o leopardo) de una imagen determinada.</source>
        </trans-unit>
        <trans-unit id="186" translate="yes" xml:space="preserve">
          <source>Ahora pasaremos a describir este método detalladamente y a indicar los scripts que hay que ejecutar.</source>
        </trans-unit>
        <trans-unit id="187" translate="yes" xml:space="preserve">
          <source>Es recomendable que, después de cada paso, se inspeccione qué archivos se han escrito y dónde se han escrito.</source>
        </trans-unit>
        <trans-unit id="188" translate="yes" xml:space="preserve">
          <source>Todos los parámetros importantes (además de una breve explicación) se especifican en un único lugar: el archivo <ph id="ph1">`PARAMETERS.py`</ph>.</source>
        </trans-unit>
        <trans-unit id="189" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-1-data-preparation"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 1: Preparación de los datos</source>
        </trans-unit>
        <trans-unit id="190" translate="yes" xml:space="preserve">
          <source>El bloc de notas <ph id="ph1">`showImages.ipynb`</ph> se puede usar para ver las imágenes y para corregir su anotación según sea necesario.</source>
        </trans-unit>
        <trans-unit id="191" translate="yes" xml:space="preserve">
          <source>Para ejecutar el bloc de notas, ábralo en Azure Machine Learning Workbench y haga clic en "Start Notebook Server" (Iniciar el servidor del bloc de notas) si esta opción aparece; a continuación, cambie al kernel del proyecto local denominado "PROJECTNAME local" (por ejemplo,.</source>
        </trans-unit>
        <trans-unit id="192" translate="yes" xml:space="preserve">
          <source>"myImgClassUsingCNTK local") y ejecute todas las celdas del bloc de notas.</source>
        </trans-unit>
        <trans-unit id="193" translate="yes" xml:space="preserve">
          <source>Vea la sección Solución de problemas de este documento si se produce un error que indica que el bloc de notas es demasiado grande para mostrarse.</source>
        </trans-unit>
        <trans-unit id="194" translate="yes" xml:space="preserve">
          <source>Ahora, ejecute el script <ph id="ph1">`1_prepareData.py`</ph>, que asigna todas las imágenes al conjunto de entrenamiento o al conjunto de prueba.</source>
        </trans-unit>
        <trans-unit id="195" translate="yes" xml:space="preserve">
          <source>Estas asignaciones son excluyentes entre sí; es decir, ninguna imagen de entrenamiento se usa para las pruebas y viceversa.</source>
        </trans-unit>
        <trans-unit id="196" translate="yes" xml:space="preserve">
          <source>Un 75 % de las imágenes de cada tipo se asigna de forma predeterminada y aleatoria al entrenamiento y el 25 por ciento restante, a las pruebas.</source>
        </trans-unit>
        <trans-unit id="197" translate="yes" xml:space="preserve">
          <source>Todos los datos generados por el script se guardan en la carpeta <bpt id="p1">*</bpt>DATA_DIR/proc/fashionTexture/<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="198" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-2-refining-the-deep-neural-network"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 2: Perfeccionar la red neuronal profunda</source>
        </trans-unit>
        <trans-unit id="199" translate="yes" xml:space="preserve">
          <source>Como ya hemos explicado en la parte 1 de este tutorial, la DNN ya entrenada se mantiene inamovible (es decir, no se perfecciona).</source>
        </trans-unit>
        <trans-unit id="200" translate="yes" xml:space="preserve">
          <source>Pero el script <ph id="ph1">`2_refineDNN.py`</ph> se ejecuta en la parte 1, dado que carga un modelo de <bpt id="p1">[</bpt>ResNet<ept id="p1">](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf)</ept> ya entrenado [2] y lo modifica (para, por ejemplo, permitir mayores resoluciones de imagen de entrada).</source>
        </trans-unit>
        <trans-unit id="201" translate="yes" xml:space="preserve">
          <source>Este paso es rápido (tarda apenas segundos) y no requiere una GPU.</source>
        </trans-unit>
        <trans-unit id="202" translate="yes" xml:space="preserve">
          <source>En la parte 2 del tutorial, una modificación en el archivo PARAMETERS.py hace que el script <ph id="ph1">`2_refineDNN.py`</ph> también perfeccione la DNN ya entrenada.</source>
        </trans-unit>
        <trans-unit id="203" translate="yes" xml:space="preserve">
          <source>Durante este perfeccionamiento, se ejecutan 45 tandas de entrenamiento.</source>
        </trans-unit>
        <trans-unit id="204" translate="yes" xml:space="preserve">
          <source>En uno y otro caso, el modelo final se escribe en el archivo <bpt id="p1">*</bpt>DATA_DIR/proc/fashionTexture/cntk_fixed.model<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="205" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-3-evaluate-dnn-for-all-images"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 3: Evaluar la DNN para todas las imágenes</source>
        </trans-unit>
        <trans-unit id="206" translate="yes" xml:space="preserve">
          <source>Ahora, podemos usar la DNN (posiblemente mejorada) del último paso para caracterizar nuestras imágenes.</source>
        </trans-unit>
        <trans-unit id="207" translate="yes" xml:space="preserve">
          <source>Dada una imagen como entrada de la DNN, la salida es el vector de 512 flotantes de la penúltima capa del modelo.</source>
        </trans-unit>
        <trans-unit id="208" translate="yes" xml:space="preserve">
          <source>Este vector tiene unas dimensiones mucho más pequeñas que la propia imagen.</source>
        </trans-unit>
        <trans-unit id="209" translate="yes" xml:space="preserve">
          <source>A pesar de ello, debe contener (y resaltar incluso) toda la información de la imagen que sea relevante para identificar el atributo de la imagen (esto es, si la prenda de ropa es de lunares, a rayas o con estampado de leopardo).</source>
        </trans-unit>
        <trans-unit id="210" translate="yes" xml:space="preserve">
          <source>Todas las representaciones de imagen de la DNN se guardan en el archivo <bpt id="p1">*</bpt>DATA_DIR/proc/fashionTexture/cntkFiles/features.pickle<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="211" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-4-support-vector-machine-training"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 4: Entrenamiento de una máquina de vectores de soporte</source>
        </trans-unit>
        <trans-unit id="212" translate="yes" xml:space="preserve">
          <source>La representación de 512 flotantes calculada en el último paso se usa para entrenar un clasificador de SVM: dada una imagen como entrada, la SVM genera una puntuación para cada atributo que esté presente.</source>
        </trans-unit>
        <trans-unit id="213" translate="yes" xml:space="preserve">
          <source>En nuestro conjunto de datos de ejemplo, esto significa una puntuación para "rayas", para "lunares" y para "leopardo".</source>
        </trans-unit>
        <trans-unit id="214" translate="yes" xml:space="preserve">
          <source>El script <ph id="ph1">`4_trainSVM.py`</ph> carga las imágenes de entrenamiento, entrena una SVM para los distintos valores del parámetro de regularización (margen de demora) C y mantiene la SVM con la máxima precisión.</source>
        </trans-unit>
        <trans-unit id="215" translate="yes" xml:space="preserve">
          <source>La precisión de la clasificación se imprime en la consola y se traza en Workbench.</source>
        </trans-unit>
        <trans-unit id="216" translate="yes" xml:space="preserve">
          <source>En el caso de los datos de textura proporcionados, estos valores deben rondar el 100 % y el 88 % respectivamente.</source>
        </trans-unit>
        <trans-unit id="217" translate="yes" xml:space="preserve">
          <source>Por último, la SVM entrenada se escribe en el archivo <bpt id="p1">*</bpt>DATA_DIR/proc/fashionTexture/cntkFiles/svm.np<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="218" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-5-evaluation-and-visualization"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 5: Evaluación y visualización</source>
        </trans-unit>
        <trans-unit id="219" translate="yes" xml:space="preserve">
          <source>La precisión del clasificador de imágenes entrenado se puede medir con el script <ph id="ph1">`5_evaluate.py`</ph>.</source>
        </trans-unit>
        <trans-unit id="220" translate="yes" xml:space="preserve">
          <source>El script puntúa todas las imágenes de prueba con el clasificador de SVM entrenado, asigna a cada imagen el atributo con la puntuación más alta y compara los atributos de predicción con anotaciones precisas.</source>
        </trans-unit>
        <trans-unit id="221" translate="yes" xml:space="preserve">
          <source>Aquí mostramos la salida del script <ph id="ph1">`5_evaluate.py`</ph>.</source>
        </trans-unit>
        <trans-unit id="222" translate="yes" xml:space="preserve">
          <source>Se calcula la precisión de la clasificación de cada clase individual, así como la precisión del conjunto de prueba completo ("precisión total") y el promedio de las precisiones individuales ("promedio total de precisión de clases").</source>
        </trans-unit>
        <trans-unit id="223" translate="yes" xml:space="preserve">
          <source>100 % corresponde a la mejor precisión posible y 0 %, a la peor.</source>
        </trans-unit>
        <trans-unit id="224" translate="yes" xml:space="preserve">
          <source>Una estimación aleatoria generaría un promedio total de precisión de clases de 1 sobre el número de atributos: en nuestro caso, esta precisión sería pues del 33,33 %.</source>
        </trans-unit>
        <trans-unit id="225" translate="yes" xml:space="preserve">
          <source>Estos resultados mejoran significativamente cuando se usa una mayor resolución de entrada, como <ph id="ph1">`rf_inputResoluton = 1000`</ph>, si bien esto conlleva tiempos de cálculo de DNN más prolongados.</source>
        </trans-unit>
        <trans-unit id="226" translate="yes" xml:space="preserve">
          <source>Además de la precisión, la curva ROC se traza con la correspondiente área bajo la curva (izquierda).</source>
        </trans-unit>
        <trans-unit id="227" translate="yes" xml:space="preserve">
          <source>También mostramos la matriz de confusión (derecha):</source>
        </trans-unit>
        <trans-unit id="228" translate="yes" xml:space="preserve">
          <source>Por último, se proporciona el bloc de notas <ph id="ph1">`showResults.py`</ph> para desplazarse por las imágenes de prueba y ver las correspondientes puntuaciones de clasificación.</source>
        </trans-unit>
        <trans-unit id="229" translate="yes" xml:space="preserve">
          <source>Tal como se explica en el paso 1, cada bloc de notas de este ejemplo debe usar el kernel del proyecto local denominado "PROJECTNAME local":</source>
        </trans-unit>
        <trans-unit id="230" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="step-6-deployment"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Paso 6: Implementación</source>
        </trans-unit>
        <trans-unit id="231" translate="yes" xml:space="preserve">
          <source>El sistema entrenado ya se puede publicar como una API de REST.</source>
        </trans-unit>
        <trans-unit id="232" translate="yes" xml:space="preserve">
          <source>La implementación se explica en el bloc de notas <ph id="ph1">`deploy.ipynb`</ph> y se basa en la funcionalidad de Azure Machine Learning Workbench (recuerde establecer como kernel el kernel del proyecto local denominado "PROJECTNAME local").</source>
        </trans-unit>
        <trans-unit id="233" translate="yes" xml:space="preserve">
          <source>Si quiere obtener más información detallada de la implementación, consulte también la excelente sección de implementación del <bpt id="p1">[</bpt>tutorial de IRIS<ept id="p1">](tutorial-classifying-iris-part-3.md)</ept>.</source>
        </trans-unit>
        <trans-unit id="234" translate="yes" xml:space="preserve">
          <source>Una vez implementado, el servicio web se puede llamar con el script <ph id="ph1">`6_callWebservice.py`</ph>.</source>
        </trans-unit>
        <trans-unit id="235" translate="yes" xml:space="preserve">
          <source>Cabe mencionar que la dirección IP (ya sea local o en la nube) del servicio web debe establecerse antes en el script.</source>
        </trans-unit>
        <trans-unit id="236" translate="yes" xml:space="preserve">
          <source>En el bloc de notas <ph id="ph1">`deploy.ipynb`</ph> se explica cómo encontrar esta dirección IP.</source>
        </trans-unit>
        <trans-unit id="237" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="part-2---accuracy-improvements"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Parte 2: Mejoras en la precisión</source>
        </trans-unit>
        <trans-unit id="238" translate="yes" xml:space="preserve">
          <source>En la parte 1 hemos visto cómo clasificar una imagen, entrenando para ello una máquina de vectores de soporte lineal en la salida de 512 flotantes de una red neuronal profunda.</source>
        </trans-unit>
        <trans-unit id="239" translate="yes" xml:space="preserve">
          <source>Esta DNN se entrenó previamente con millones de imágenes y la penúltima capa se devolvió como un vector de características.</source>
        </trans-unit>
        <trans-unit id="240" translate="yes" xml:space="preserve">
          <source>Este método es rápido, porque la DNN se usa tal cual y, con todo, da buenos resultados con frecuencia.</source>
        </trans-unit>
        <trans-unit id="241" translate="yes" xml:space="preserve">
          <source>Ahora nos centraremos en diversas maneras de mejorar la precisión del modelo de la parte 1.</source>
        </trans-unit>
        <trans-unit id="242" translate="yes" xml:space="preserve">
          <source>En concreto, vamos a perfeccionar la DNN en lugar mantenerla inamovible.</source>
        </trans-unit>
        <trans-unit id="243" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="dnn-refinement"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Perfeccionamiento de la DNN</source>
        </trans-unit>
        <trans-unit id="244" translate="yes" xml:space="preserve">
          <source>En lugar de en una SVM, la clasificación se puede realizar directamente en la red neuronal.</source>
        </trans-unit>
        <trans-unit id="245" translate="yes" xml:space="preserve">
          <source>Esto se logra agregando una nueva última capa a la DNN ya entrenada, que toma los 512 flotantes de la penúltima capa como entrada.</source>
        </trans-unit>
        <trans-unit id="246" translate="yes" xml:space="preserve">
          <source>La ventaja de realizar la clasificación en la DNN es que ahora la red entera se puede volver a entrenar con una nueva propagación.</source>
        </trans-unit>
        <trans-unit id="247" translate="yes" xml:space="preserve">
          <source>Con este método se suele obtener una precisión de la clasificación mucho mejor a si usáramos la DNN ya entrenada tal cual, pero conlleva unos tiempos de cálculo de DNN más prolongados (incluso con una GPU).</source>
        </trans-unit>
        <trans-unit id="248" translate="yes" xml:space="preserve">
          <source>Entrenar la red neuronal en lugar de una SVM se efectúa cambiando la variable <ph id="ph1">`classifier`</ph> en <ph id="ph2">`PARAMETERS.py`</ph> de <ph id="ph3">`svm`</ph> a <ph id="ph4">`dnn`</ph>.</source>
        </trans-unit>
        <trans-unit id="249" translate="yes" xml:space="preserve">
          <source>Luego, tal y como se describe en la parte 1, hay que volver a ejecutar todos los scripts, excepto el de preparación de los datos (paso 1) y el de entrenamiento de SVM (paso 4).</source>
        </trans-unit>
        <trans-unit id="250" translate="yes" xml:space="preserve">
          <source>El perfeccionamiento de la DNN requiere una GPU.</source>
        </trans-unit>
        <trans-unit id="251" translate="yes" xml:space="preserve">
          <source>Si no existe ninguna GPU o si la GPU está bloqueada (por ejemplo, porque haya una ejecución de CNTK anterior), el script <ph id="ph1">`2_refineDNN.py`</ph> generará un error.</source>
        </trans-unit>
        <trans-unit id="252" translate="yes" xml:space="preserve">
          <source>En algunas GPU, el entrenamiento de la DNN puede producir un error de memoria insuficiente, que se puede soslayar si se reduce el tamaño del minilote (variable <ph id="ph1">`cntk_mb_size`</ph> en <ph id="ph2">`PARAMETERS.py`</ph>).</source>
        </trans-unit>
        <trans-unit id="253" translate="yes" xml:space="preserve">
          <source>Una vez completado el entrenamiento, el modelo perfeccionado se guarda en <bpt id="p1">*</bpt>DATA_DIR/proc/fashionTexture/cntk_refined.model<ept id="p1">*</ept> y se traza un gráfico que muestra cómo varían los errores de clasificación de entrenamiento y de prueba durante el entrenamiento.</source>
        </trans-unit>
        <trans-unit id="254" translate="yes" xml:space="preserve">
          <source>Observe en ese gráfico que el error del conjunto de entrenamiento es mucho menor que el del conjunto de prueba.</source>
        </trans-unit>
        <trans-unit id="255" translate="yes" xml:space="preserve">
          <source>Este comportamiento, conocido como sobreajuste, se puede minimizar, por ejemplo, usando un valor más alto como tasa de eliminación (<ph id="ph1">`rf_dropoutRate`</ph>).</source>
        </trans-unit>
        <trans-unit id="256" translate="yes" xml:space="preserve">
          <source>Como se aprecia en el siguiente gráfico, la precisión del conjunto de datos proporcionado usando el perfeccionamiento de la DNN es del 92,35 % en comparación con el 88,92 % previo (parte 1).</source>
        </trans-unit>
        <trans-unit id="257" translate="yes" xml:space="preserve">
          <source>En concreto, las imágenes relativas a los "lunares" (dotted) mejoran considerablemente y logran un área bajo la curva de ROC de 0,98 con el perfeccionamiento, frente al 0,94 anterior.</source>
        </trans-unit>
        <trans-unit id="258" translate="yes" xml:space="preserve">
          <source>Estamos usando un conjunto de datos pequeño y, por lo tanto, las precisiones reales al ejecutar el código son diferentes.</source>
        </trans-unit>
        <trans-unit id="259" translate="yes" xml:space="preserve">
          <source>Esta discrepancia obedece a efectos estocásticos como la división aleatoria de las imágenes en los conjuntos de pruebas de entrenamiento y de prueba.</source>
        </trans-unit>
        <trans-unit id="260" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="run-history-tracking"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Ejecutar un seguimiento del historial</source>
        </trans-unit>
        <trans-unit id="261" translate="yes" xml:space="preserve">
          <source>Azure Machine Learning Workbench almacena el historial de cada ejecución en Azure para, así, permitir que se puedan comparar dos o más ejecuciones con incluso semanas de diferencia.</source>
        </trans-unit>
        <trans-unit id="262" translate="yes" xml:space="preserve">
          <source>Esto se explica con más detalle en el <bpt id="p1">[</bpt>tutorial de Iris<ept id="p1">](tutorial-classifying-iris-part-2.md)</ept>.</source>
        </trans-unit>
        <trans-unit id="263" translate="yes" xml:space="preserve">
          <source>También se ilustra en las siguientes capturas de pantalla, donde comparamos dos ejecuciones del script <ph id="ph1">`5_evaluate.py`</ph>, ya sea por medio del perfeccionamiento de la DNN, es decir, <ph id="ph2">`classifier = "dnn"`</ph> (número de ejecución 148) o del entrenamiento de la SVM, es decir, <ph id="ph3">`classifier = "svm"`</ph> (número de ejecución 150).</source>
        </trans-unit>
        <trans-unit id="264" translate="yes" xml:space="preserve">
          <source>En la primera captura de pantalla, el perfeccionamiento de la DNN lleva a unas mejores precisiones que con el entrenamiento de SVM en todas las clases.</source>
        </trans-unit>
        <trans-unit id="265" translate="yes" xml:space="preserve">
          <source>La segunda captura de pantalla muestra todas las métricas de las que se hace un seguimiento, incluido el clasificador que se usó.</source>
        </trans-unit>
        <trans-unit id="266" translate="yes" xml:space="preserve">
          <source>Este seguimiento se realiza en el script <ph id="ph1">`5_evaluate.py`</ph>, llamando al registrador de Azure Machine Learning Workbench.</source>
        </trans-unit>
        <trans-unit id="267" translate="yes" xml:space="preserve">
          <source>El script también guarda la curva de ROC y la matriz de confusión en la carpeta <bpt id="p1">*</bpt>outputs<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="268" translate="yes" xml:space="preserve">
          <source>Esta carpeta <bpt id="p1">*</bpt>outputs<ept id="p1">*</ept> es especial, en el sentido de que también se realiza un seguimiento de su contenido por medio de la característica de historial de Workbench.</source>
        </trans-unit>
        <trans-unit id="269" translate="yes" xml:space="preserve">
          <source>Por lo tanto, se puede tener acceso a sus archivos siempre que se quiera, independientemente de si las copias locales se han sobrescrito.</source>
        </trans-unit>
        <trans-unit id="270" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="parameter-tuning"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Ajuste de parámetros</source>
        </trans-unit>
        <trans-unit id="271" translate="yes" xml:space="preserve">
          <source>Como sucede en la mayoría de los proyectos de aprendizaje automático, para obtener buenos resultados en un conjunto de datos nuevo, es necesario ajustar los parámetros con mucho cuidado, así como sopesar detenidamente diversas decisiones de diseño.</source>
        </trans-unit>
        <trans-unit id="272" translate="yes" xml:space="preserve">
          <source>Para hacer estas tareas más sencillas, todos los parámetros importantes (además de una breve explicación) se especifican en un único lugar: el archivo <ph id="ph1">`PARAMETERS.py`</ph>.</source>
        </trans-unit>
        <trans-unit id="273" translate="yes" xml:space="preserve">
          <source>Estos son algunos aspectos que sin duda se traducirán en mejoras:</source>
        </trans-unit>
        <trans-unit id="274" translate="yes" xml:space="preserve">
          <source>Calidad de los datos: asegúrese de que la calidad de los conjuntos de entrenamiento y de prueba es alta.</source>
        </trans-unit>
        <trans-unit id="275" translate="yes" xml:space="preserve">
          <source>Es decir, procure que las imágenes estén correctamente anotadas, que ha quitado las imágenes ambiguas (por ejemplo, prendas de ropa que tienen tanto rayas como lunares) y que los atributos son excluyentes entre sí (dicho de otro modo, que los ha elegido de tal forma que cada imagen pertenece a exactamente un atributo).</source>
        </trans-unit>
        <trans-unit id="276" translate="yes" xml:space="preserve">
          <source>Hay constancia de que, si el objeto de interés es pequeño en la imagen, los métodos de clasificación de imágenes no funcionan bien.</source>
        </trans-unit>
        <trans-unit id="277" translate="yes" xml:space="preserve">
          <source>En tales casos, considere el uso de un método de detección de objetos, tal y como se describe en este <bpt id="p1">[</bpt>tutorial<ept id="p1">](https://github.com/Azure/ObjectDetectionUsingCntk)</ept>.</source>
        </trans-unit>
        <trans-unit id="278" translate="yes" xml:space="preserve">
          <source>Perfeccionamiento de la DNN: seguramente, el parámetro más importante para realizar esta tarea correctamente sea la velocidad de aprendizaje <ph id="ph1">`rf_lrPerMb`</ph>.</source>
        </trans-unit>
        <trans-unit id="279" translate="yes" xml:space="preserve">
          <source>Si la precisión del conjunto de entrenamiento (primera figura de la parte 2) no ronda el 0-5 %, probablemente se deba a un error en la velocidad de aprendizaje.</source>
        </trans-unit>
        <trans-unit id="280" translate="yes" xml:space="preserve">
          <source>Los demás parámetros que comienzan por <ph id="ph1">`rf_`</ph> no son tan importantes.</source>
        </trans-unit>
        <trans-unit id="281" translate="yes" xml:space="preserve">
          <source>Normalmente, el error de entrenamiento debería disminuir exponencialmente y aproximarse a 0 % después del entrenamiento.</source>
        </trans-unit>
        <trans-unit id="282" translate="yes" xml:space="preserve">
          <source>Resolución de entrada: la resolución de imagen predeterminada es 224 x 224 píxeles.</source>
        </trans-unit>
        <trans-unit id="283" translate="yes" xml:space="preserve">
          <source>Si usa una resolución de imagen mayor (parámetro: <ph id="ph1">`rf_inputResoluton`</ph>), por ejemplo, 448 x 448 o 896 x 896 píxeles, con frecuencia obtendrá una mejora significativa, pero el perfeccionamiento de la DNN tardará más en completarse.</source>
        </trans-unit>
        <trans-unit id="284" translate="yes" xml:space="preserve">
          <source><bpt id="p1">**</bpt>Usar una mayor resolución es inocuo y casi siempre aumenta la precisión<ept id="p1">**</ept>.</source>
        </trans-unit>
        <trans-unit id="285" translate="yes" xml:space="preserve">
          <source>Sobreajuste de la DNN: procure que no haya mucha diferencia entre la precisión del conjunto de entrenamiento y la del conjunto de prueba durante el perfeccionamiento de la DNN (primera figura de la parte 2).</source>
        </trans-unit>
        <trans-unit id="286" translate="yes" xml:space="preserve">
          <source>Esta diferencia se puede reducir usando tasas de eliminación (<ph id="ph1">`rf_dropoutRate`</ph>) de 0,5 o más, así como aumentando el peso del regularizador <ph id="ph2">`rf_l2RegWeight`</ph>.</source>
        </trans-unit>
        <trans-unit id="287" translate="yes" xml:space="preserve">
          <source>Usar una tasa de eliminación elevada puede ser especialmente útil si la resolución de imagen de entrada de DNN es alta.</source>
        </trans-unit>
        <trans-unit id="288" translate="yes" xml:space="preserve">
          <source>Pruebe a usar DNN un poco más profundas, cambiando para ello <ph id="ph1">`rf_pretrainedModelFilename`</ph> de <ph id="ph2">`ResNet_18.model`</ph> a <ph id="ph3">`ResNet_34.model`</ph> o a <ph id="ph4">`ResNet_50.model`</ph>.</source>
        </trans-unit>
        <trans-unit id="289" translate="yes" xml:space="preserve">
          <source>El modelo ResNet-50 no solo es más profundo, sino que, además, su salida de la penúltima capa tiene un tamaño de 2048 flotantes (frente a los 512 flotantes de los modelos ResNet-18 y ResNet 34).</source>
        </trans-unit>
        <trans-unit id="290" translate="yes" xml:space="preserve">
          <source>Esta mayor dimensión puede resultar especialmente útil al entrenar un clasificador de SVM.</source>
        </trans-unit>
        <trans-unit id="291" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="part-3---custom-dataset"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Parte 3: Conjunto de datos personalizado</source>
        </trans-unit>
        <trans-unit id="292" translate="yes" xml:space="preserve">
          <source>En las partes 1 y 2, hemos entrenado y evaluado un modelo de clasificación de imágenes usando las imágenes de texturas de partes de arriba de ropa proporcionadas.</source>
        </trans-unit>
        <trans-unit id="293" translate="yes" xml:space="preserve">
          <source>Ahora, describiremos cómo usar un conjunto de datos personalizado proporcionado por el usuario, en lugar de esas imágenes.</source>
        </trans-unit>
        <trans-unit id="294" translate="yes" xml:space="preserve">
          <source>O bien, si no hay un conjunto disponible, cómo generar y anotar uno por medio de la búsqueda de imágenes de Bing.</source>
        </trans-unit>
        <trans-unit id="295" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="using-a-custom-dataset"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Usar un conjunto de datos personalizado</source>
        </trans-unit>
        <trans-unit id="296" translate="yes" xml:space="preserve">
          <source>En primer lugar, echemos un vistazo a la estructura de carpetas de los datos de texturas de prendas de ropa.</source>
        </trans-unit>
        <trans-unit id="297" translate="yes" xml:space="preserve">
          <source>Observe cómo todas las imágenes relativas a cada atributo se encuentran en las subcarpetas correspondientes (<bpt id="p1">*</bpt>dotted<ept id="p1">*</ept>, *leopard y <bpt id="p2">*</bpt>striped<ept id="p2">*</ept>) dentro de <bpt id="p3">*</bpt>DATA_DIR/images/fashionTexture/<ept id="p3">*</ept>.</source>
        </trans-unit>
        <trans-unit id="298" translate="yes" xml:space="preserve">
          <source>Observe también cómo el nombre de la carpeta de imágenes también aparece reflejado en el archivo <ph id="ph1">`PARAMETERS.py`</ph>:</source>
        </trans-unit>
        <trans-unit id="299" translate="yes" xml:space="preserve">
          <source>Usar un conjunto de datos personalizado es tan sencillo como reproducir esta misma estructura de carpetas donde están todas las imágenes en subcarpetas según sus atributos y, luego, copiar estas subcarpetas en un nuevo directorio especificado por el usuario, <bpt id="p1">*</bpt>DATA_DIR/images/newDataSetName/<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="300" translate="yes" xml:space="preserve">
          <source>El único cambio de código necesario consiste en establecer la variable <ph id="ph1">`datasetName`</ph> en <bpt id="p1">*</bpt>newDataSetName<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="301" translate="yes" xml:space="preserve">
          <source>Tras ello, los scripts 1-5 se pueden ejecutar en orden y todos los archivos intermedios se escriben en <bpt id="p1">*</bpt>DATA_DIR/proc/newDataSetName/<ept id="p1">*</ept>.</source>
        </trans-unit>
        <trans-unit id="302" translate="yes" xml:space="preserve">
          <source>No se requiere ningún cambio de código más.</source>
        </trans-unit>
        <trans-unit id="303" translate="yes" xml:space="preserve">
          <source>Es importante que cada imagen pueda asignarse a exactamente un solo atributo.</source>
        </trans-unit>
        <trans-unit id="304" translate="yes" xml:space="preserve">
          <source>Por ejemplo, sería incorrecto usar atributos para "animal" y para "leopardo", dado que "leopardo" también pertenecería a la clasificación "animal".</source>
        </trans-unit>
        <trans-unit id="305" translate="yes" xml:space="preserve">
          <source>De igual modo, conviene eliminar las imágenes ambiguas (y, por tanto, difíciles de anotar).</source>
        </trans-unit>
        <trans-unit id="306" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="image-scraping-and-annotation"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Extracción y anotación de imágenes</source>
        </trans-unit>
        <trans-unit id="307" translate="yes" xml:space="preserve">
          <source>Recopilar un número suficientemente grande de imágenes anotadas para el entrenamiento y las pruebas puede resultar complicado.</source>
        </trans-unit>
        <trans-unit id="308" translate="yes" xml:space="preserve">
          <source>Una forma de solucionar este problema consiste en extraer imágenes de Internet.</source>
        </trans-unit>
        <trans-unit id="309" translate="yes" xml:space="preserve">
          <source>Por ejemplo, eche un vistazo a los siguientes resultados de una búsqueda de imágenes de Bing a raíz de la consulta <bpt id="p1">*</bpt>t-shirt striped<ept id="p1">*</ept> para encontrar camisetas a rayas.</source>
        </trans-unit>
        <trans-unit id="310" translate="yes" xml:space="preserve">
          <source>Como se esperaba, la mayoría de las imágenes son verdaderamente camisetas a rayas.</source>
        </trans-unit>
        <trans-unit id="311" translate="yes" xml:space="preserve">
          <source>Las pocas imágenes incorrectas o ambiguas (por ejemplo, la de la columna 1, fila 1, o la de la columna 3, fila 2) se pueden identificar y quitar fácilmente:</source>
        </trans-unit>
        <trans-unit id="312" translate="yes" xml:space="preserve">
          <source>Para generar un conjunto de datos voluminoso y diverso, hay que realizar varias consultas.</source>
        </trans-unit>
        <trans-unit id="313" translate="yes" xml:space="preserve">
          <source>Por ejemplo, si tenemos 7 <ph id="ph1">\*</ph> 3 = 21 consultas, se pueden sintetizar automáticamente usando todas las combinaciones de prendas de ropa {blusa, sudadera, sudadera con capucha, jersey, camisa, camiseta, chaleco} y atributos {rayas, lunares, leopardo}.</source>
        </trans-unit>
        <trans-unit id="314" translate="yes" xml:space="preserve">
          <source>Descargar las primeras 50 imágenes de cada consulta nos llevaría a tener un máximo de 21 x 50 = 1050 imágenes.</source>
        </trans-unit>
        <trans-unit id="315" translate="yes" xml:space="preserve">
          <source>En lugar de descargarlas manualmente desde la búsqueda de imágenes de Bing, es mucho más fácil usar en su lugar la <bpt id="p1">[</bpt>Bing Image Search API de Cognitive Services<ept id="p1">](https://www.microsoft.com/cognitive-services/bing-image-search-api)</ept>, que devuelve un conjunto de direcciones URL de imágenes correspondientes a una cadena de consulta determinada.</source>
        </trans-unit>
        <trans-unit id="316" translate="yes" xml:space="preserve">
          <source>Algunas de las imágenes descargadas son duplicados exactos o casi exactos (por ejemplo, solo se diferencian por la resolución de imagen o por anomalías del formato jpg).</source>
        </trans-unit>
        <trans-unit id="317" translate="yes" xml:space="preserve">
          <source>Estos duplicados se deben quitar para que los conjuntos de entrenamiento y de prueba no contengan las mismas imágenes.</source>
        </trans-unit>
        <trans-unit id="318" translate="yes" xml:space="preserve">
          <source>La eliminación de imágenes duplicadas puede lograrse con un método basado en hash, consistente en dos pasos: (1) en primer lugar, se calcula la cadena hash de todas las imágenes y (2) en un segundo procesamiento de las imágenes, solamente se conservan aquellas que tengan una cadena hash que aún no se haya visto.</source>
        </trans-unit>
        <trans-unit id="319" translate="yes" xml:space="preserve">
          <source>Todas las demás imágenes se descartan.</source>
        </trans-unit>
        <trans-unit id="320" translate="yes" xml:space="preserve">
          <source>Hemos constatado que el método <ph id="ph1">`dhash`</ph> de la biblioteca de Python <ph id="ph2">`imagehash`</ph> (descrito en este <bpt id="p1">[</bpt>blog<ept id="p1">](http://www.hackerfactor.com/blog/index.php?/archives/529-Kind-of-Like-That.html)</ept>) funciona bien con el parámetro <ph id="ph3">`hash_size`</ph> establecido en 16.</source>
        </trans-unit>
        <trans-unit id="321" translate="yes" xml:space="preserve">
          <source>No pasa nada si se quitan algunas imágenes no duplicadas por error, siempre y cuando se quiten la mayoría de los duplicados reales.</source>
        </trans-unit>
        <trans-unit id="322" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="conclusion"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Conclusión</source>
        </trans-unit>
        <trans-unit id="323" translate="yes" xml:space="preserve">
          <source>Algunos aspectos destacados de este ejemplo son:</source>
        </trans-unit>
        <trans-unit id="324" translate="yes" xml:space="preserve">
          <source>El código usado para entrenar, evaluar e implementar un modelo personalizado de clasificación de imágenes.</source>
        </trans-unit>
        <trans-unit id="325" translate="yes" xml:space="preserve">
          <source>El uso de las imágenes de demostración suministradas, aunque esto es fácilmente adaptable (solo habría que cambiar una línea) para usar un conjunto de datos de imágenes propio.</source>
        </trans-unit>
        <trans-unit id="326" translate="yes" xml:space="preserve">
          <source>Las características modernas y de nivel de experto implementadas para entrenar modelos de alta precisión basados en el aprendizaje de transferencia.</source>
        </trans-unit>
        <trans-unit id="327" translate="yes" xml:space="preserve">
          <source>El desarrollo de modelos interactivos con Azure Machine Learning Workbench y Jupyter Notebook.</source>
        </trans-unit>
        <trans-unit id="328" translate="yes" xml:space="preserve">
          <source><bpt id="p1">&lt;a name="references"&gt;</bpt><ept id="p1">&lt;/a&gt;</ept>Referencias</source>
        </trans-unit>
        <trans-unit id="329" translate="yes" xml:space="preserve">
          <source>[1] Alex Krizhevsky, Ilya Sutskever y Geoffrey E. Hinton.</source>
        </trans-unit>
        <trans-unit id="330" translate="yes" xml:space="preserve">
          <source><bpt id="p1">[</bpt><bpt id="p2">_</bpt>ImageNet Classification with Deep Convolutional Neural Networks<ept id="p2">_</ept><ept id="p1">](https://papers.nips.cc/paper/4824-imagenet-classification-with-deep-convolutional-neural-networks.pdf)</ept> (Clasificación de ImageNet con redes neuronales profundas de convolución).</source>
        </trans-unit>
        <trans-unit id="331" translate="yes" xml:space="preserve">
          <source>NIPS 2012.</source>
        </trans-unit>
        <trans-unit id="332" translate="yes" xml:space="preserve">
          <source>[2] Kaiming He, Xiangyu Zhang, Shaoqing Ren y Jian Sun.</source>
        </trans-unit>
        <trans-unit id="333" translate="yes" xml:space="preserve">
          <source><bpt id="p1">[</bpt><bpt id="p2">_</bpt>Deep Residual Learning for Image Recognition<ept id="p2">_</ept><ept id="p1">](https://www.cv-foundation.org/openaccess/content_cvpr_2016/papers/He_Deep_Residual_Learning_CVPR_2016_paper.pdf)</ept> (Aprendizaje residual profundo para el reconocimiento de imágenes).</source>
        </trans-unit>
        <trans-unit id="334" translate="yes" xml:space="preserve">
          <source>CVPR 2016.</source>
        </trans-unit>
      </group>
    </body>
  </file>
</xliff>
