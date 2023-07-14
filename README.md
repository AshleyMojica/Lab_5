# Lab_5
Revista Digital
fetch('data.json')
  .then(response => response.json())
  .then(data => {
    const revistaTitulo = document.getElementById('revista-titulo');
    const articulosContainer = document.getElementById('articulos-container');
    revistaTitulo.textContent = data.titulo;

    data.articulos.forEach(articulo => {
      const articuloCard = document.createElement('div');
      articuloCard.classList.add('articulo-card');
      articuloCard.innerHTML = `
        <h3>${articulo.titulo}</h3>
        <img src="${articulo.imagen1}" alt="">
        <p>${limitarDescripcion(articulo.contenido, 10)}</p>
        <img src="${articulo.imagen2}" alt="">

      `;
      articuloCard.addEventListener('click', () => {
        mostrarModal(articulo);
      });

      articulosContainer.appendChild(articuloCard);
    });

    const imagenes = document.querySelectorAll('.articulo-card img');
    imagenes.forEach(function (imagen) {
      imagen.style.display = 'none'; // Oculta todas las imágenes al cargar la página
    });
  })
  .catch(error => {
    console.log('Error al cargar el archivo JSON:', error);
  });

function limitarDescripcion(texto, longitud) {
  const palabras = texto.split(' ');
  if (palabras.length > longitud) {
    return palabras.slice(0, longitud).join(' ') + '...' + '<br><br>Seguir leyendo...';
  }
  return texto;
}

function mostrarModal(articulo) {
  const modal = document.getElementById('modal');
  const modalTitulo = document.getElementById('modal-titulo');
  const modalImagen1 = document.getElementById('modal-imagen1');
  const modalContenido = document.getElementById('modal-contenido');
  const modalImagen2 = document.getElementById('modal-imagen2');

  modalTitulo.textContent = articulo.titulo;
  modalContenido.innerHTML = articulo.contenido.replace(/\n/g, '<br>');
  modalContenido.classList.add('modal-abierto');

  modal.style.display = 'block';

  modalImagen1.style.display = 'none'; // Oculta la imagen inicialmente
  modalImagen2.style.display = 'none'; // Oculta la imagen inicialmente

  modalImagen1.onload = function () {
    modalImagen1.style.display = 'block'; // Muestra la imagen cuando se carga
  };

  modalImagen1.src = articulo.imagen1;

  modalImagen2.onload = function () {
    modalImagen2.style.display = 'block'; // Muestra la imagen cuando se carga
  };
  modalImagen2.src = articulo.imagen2;

  const closeBtn = document.getElementsByClassName('close')[0];
  closeBtn.addEventListener('click', () => {
    modalContenido.classList.add('modal-cerrado');

    setTimeout(() => {
      modalContenido.classList.remove('modal-cerrado');
      modal.style.display = 'none';
    }, 300);
  });

  window.addEventListener('click', event => {
    if (event.target === modal) {
      modalContenido.classList.remove('modal-abierto');
      modal.style.display = 'none';
    }
    {
    "titulo":"Ambiente y Sociedad",
    "articulos": [
    {
    "titulo": "Introducción",
    "imagen1": "imagenes/flyer2.jpg",
    "contenido": "En el siguiente trabajo informativo “Seguridad Vial” se encontrarán diferentes segmentos y artículos informativos enfocados en la reducción de accidentes de tránsito.\n \n La revista es creada con el propósito de informar sobre diferentes temas relacionados a la educación vial, en cada uno de sus artículos encontraras información, consejería, tips, opiniones y testimonios enfocados en la prevención de accidentes de tránsito, debido a su gran incremento en lo que va del año 2023.\n \n Convirtiéndose en un problema de salud pública de gran importancia.El proyecto es llevado a cabo por 5 estudiantes universitarios de la UNAN- Farem Chontales, y cada uno tendrá la oportunidad de dar a conocer un tema en específico, con un rol muy importante en el desarrollo de la revista. De esta forma facilitar al lector la comprensión de tal problemática.",
    "imagen2":"imagenes/flyer.jpg"
    },
    {
    "titulo": "El agua como fuente de vida.",
    "imagen1": "imagenes/Paja.jpg",
    "contenido": "El cuido del agua: No hay vida sin agua. \n \n El agua es elemento fundamental para la vida y la supervivencia de nuestro planeta y nuestra biodiversidad. Como señala Naciones Unidas, el agua es fuente de vida, pero el impacto de la actividad humana en el cambio climático está mermando las reservas de agua y especialmente de agua potable, ya de por sí escasas, a las que tenemos acceso. Por este motivo, nuestro objetivo fundamental debe ser el cuidado del agua.\n Evitar el despilfarro de agua, controlar su consumo o su reutilización es clave para garantizar el cuidado del agua. Sin embargo, no contaminar el agua es también resulta esencial.\n El cuidado del agua es vital para proteger uno de los recursos naturales más amenazados de nuestro planeta. El agua nos ayuda a mantener un clima estable y es un recurso esencial para procesos vitales de los seres vivos.\n Algunas de las recomendaciones para el cuido del agua son muchas, pero aquí tenemos unas cuantas de muchas que existen, por ejemplo: Tener una ducha de 5 minutos, cerrar el grifo cuando te lavas los dientes, cerrar el grifo cuando te estés afeitando, utiliza la lavadora con carga completa, usa sistemas de control del agua en el inodoro, cuando te laves las manos mientras las enjabonas cerrar el grifo, etc.\n En conclusión, el cuido del agua nos beneficia en todos los aspectos de la vida ya que sin ella no podríamos sobrevivir todos los seres vivos. El implementar medidas para el cuido del agua en el hogar y en muchas empresas ayuda a reducir el mal gaste del vital líquido.\n Según en el sitio web, (Aque,2013). Evitar el despilfarro de agua, controlar su consumo o su reutilización es clave para garantizar el cuidado del aguay permitir así una mejor calidad de este recurso tan valioso para la vida en el planeta.\n \n Agua en las Comunidades: El agua limpia significa salud.\n \n Contar con sistemas de agua potable y saneamiento significa evitar exponerse a innumerables enfermedades. Cada año mueren miles de personas de enfermedades provocadas por sistemas de agua, saneamiento e higiene inadecuados. Aparte de la neumonía, la diarrea es la principal causa de muerte en niños menores de 5 años. Los beneficios de contar con una fuente de agua potable en una comunidad son muy importantes. Si las mujeres y las niñas ya no tienen que caminar kilómetros para ir a buscar agua cada día, disponen de más tiempo para estudiar. Con ello aumentan los índices de alfabetización. Y si las escuelas construyen instalaciones sanitarias adecuadas, las chicas pasan más tiempo en la escuela y menos en casa. El agua potable y una mejor higiene ayudan a reducir la carga que suponen las enfermedades para las familias y dejan más tiempo a las mujeres para obtener sus propios ingresos. Terminar con las disposiciones al aire libre significa aumentar la seguridad de las personas particularmente de noche, además de mantener la tierra más limpia y las cosechas más sanas. La educación también ha formado parte esencial de esta iniciativa. Así, desde 2007 se han establecido más de 200 comités de agua y saneamiento comunitarios y 93 clubs escolares de higiene. Sus miembros promueven la higiene en sus comunidades. Enseñan a las personas a almacenar agua de forma segura, a construir instalaciones sanitarias adecuadas y a que los niños se laven las manos correctamente. A veces, las medidas más simples son las que logran los mejores resultados. En conclusión, la importancia de agua potable en las comunidades, Es indispensable porque de ello dependen tantas familias. En una comunidad la falta de agua sería un impacto social negativo ya que de ella dependemos todas las personas.\n \n Aguas Residuales: El agua sucia no se puede lavar.\n \nLas Aguas Residuales son cualquier tipo de agua cuya calidad está afectada negativamente por la influencia antropogénica. Se trata de agua que no tiene valor inmediato para el fin para el que se utilizó ni para el propósito para el que se produjo debido a su calidad, cantidad o al momento en que se dispone de ella. Según la UNESCO (2017), el 80% de las aguas residuales retornan al ecosistema sin ser tratadas o reutilizadas, siendo uno de los grandes desafíos del agua. \n \n Existen diferentes tipos de aguas residuales según su origen. Los principales tipos de aguas residuales son: Aguas residuales urbanas, Aguas residuales domésticas, Aguas residuales industriales y la ganadería. \n \n El tratamiento de aguas residuales, o depuración de aguas residuales, consiste en una serie de procesos físicos, químicos y biológicos que buscan eliminar los contaminantes presentes en el agua resultante del uso humano o de otros usos. La depuración comienza recogiendo las aguas de los núcleos urbanos y sectores industriales, y busca devolverla al ciclo del agua, ya sea vertiéndola en el mismo mar o reutilizándola. \n \n Las aguas residuales se pueden clasificar según su cantidad y el tipo de sustancias químicas que contienen; según sus características bacteriológicas; según la relación entre agua y materia en suspensión y materia disuelta; o según su procedencia. \n \n La descarga de aguas residuales domésticas, industriales, agrícolas y pecuarias sin tratamiento provoca la contaminación de los cuerpos de agua disminuyendo la calidad de las aguas. \n \n En resumen, Las aguas residuales pueden ser utilizadas para la población porque hacen una función tan importante porque después de ser tratadas pueden utilizarse para reemplazar el agua dulce para riego, procesos industriales o fines recreativos. También pueden usarse para mantener el flujo ambiental, y los productos derivados de su tratamiento pueden generar energía y nutrientes. ",
    "imagen2":"imagenes/vaso.jpg"
    },
    {
    "titulo": "Aire puro: Un compromiso colectivo.",
    "imagen1": "imagenes/aire.jpg",
    "contenido": "La vitalidad del aire.\n \n El aire es un elemento esencial para el desarrollo de la vida en la tierra. Su función principal es proporcionar oxígeno para respirar. Sin ellos, las plantas, los animales y los humanos no pueden existir. Sus principales componentes son nitrógeno, oxígeno, dióxido de carbono, neón, helio, etc. Todos ellos son muy importantes y necesarios para que los organismos realicen funciones importantes. \n \n Como opina UNICEF (2021), La contaminación del aire debe entenderse, al igual que otras problemáticas ambientales, en el marco de la justicia ambiental. La injusticia ambiental se refiere a la distribución injusta de las cargas ambientales o las consecuencias negativas producidas por la contaminación (del aire, del agua o del suelo), generalmente atribuidas a poblaciones menos favorecidas. \n \n Podemos respirar gracias al oxígeno de la atmósfera. El dióxido de carbono es la base de la fotosíntesis. El aire permite la existencia del fuego, el sonido, el viento, las nubes, la lluvia, etc. Las funciones del aire están relacionadas con: \n \n Viento: Surge del fenómeno de expansión y movimiento del aire en la atmósfera. \n \n Clima y sensación de calor: fenómenos relacionados con la tendencia al enfriamiento del aire, su movilidad, presión y humedad. \n \n Atmósfera: Es todo el aire que rodea a la Tierra. \n \n Capa de Ozono: Ayuda a filtrar los rayos ultravioletas del sol de efectos nocivos sobre el planeta. \n \n Riesgos naturales: Ciertas condiciones del aire en la atmósfera pueden causar huracanes y tornados. \n \n Su importancia también radica en que es una fuente de energía renovable, como la eólica, el calor, el agua, los procesos industriales o de producción, el efecto invernadero, el equilibrio del mundo natural, y existencia. Viento, fuego, nubes, lluvia y otros fenómenos naturales. El aire es sin duda fundamental y juega un papel importante por sus funciones, usos y beneficios que posibilitan la vida en la Tierra.\n \n Metales pesados: Minimizando los riesgos para la salud.\n \n Como dijo UNICEF (2021). La contaminación del aire y el cambio climático tienen un origen en común y, por tanto, pueden tener soluciones comunes. Las emisiones de GEI como resultado de la quema de combustibles fósiles favorecen el cambio climático, al mismo tiempo que se liberan contaminantes que provocan la contaminación del aire. \n \n La contaminación del aire provoca graves problemas ambientales, como el smog, el efecto invernadero, la lluvia ácida y el agotamiento de la capa de ozono, y tiene un gran impacto en los seres humanos, los animales y las plantas. \n \n Monóxido de carbono (CO) \n \n El CO es un gas producido por una combustión con bajas concentraciones de oxígeno. Según la literatura, el de las emisiones proviene del transporte, seguido de la combustión de combustibles industriales y los procesos industriales. Puede tener efectos adversos para la salud porque compite con el O2 en el torrente sanguíneo y reduce la capacidad de la sangre para transportar oxígeno a varios órganos. Las personas sensibles, especialmente aquellas con problemas cardíacos, pueden experimentar un suministro reducido de oxígeno. Sin embargo, las concentraciones de CO rara vez exceden los límites establecidos para mantener una buena salud. \n \n Óxidos de nitrógeno (NO, NO2, NOx). \n \n Se ha encontrado que las concentraciones de NO2 pueden ser significativamente más altas cerca de las principales rutas de transporte, por lo que es importante considerar el impacto en las poblaciones vulnerables. \n \n La presencia excesiva de estos gases hace que el planeta se caliente más de lo necesario, impulsando el cambio climático global y alterando los procesos físicos y químicos del planeta, afectando a las especies que allí habitan, por lo que este es un delicado equilibrio. Aunque comúnmente se piensa que el efecto invernadero es un efecto adverso de la contaminación del aire, en realidad es importante para la vida en la Tierra.\n \n Aire puro, futuro seguro.\n \n La contaminación del aire ha cobrado reconocimiento y prominencia en las agendas globales. En septiembre del 2015, la Asamblea General de las Naciones Unidas adoptó la Agenda 2030 para el Desarrollo Sostenible. \n \n De acuerdo a la Organización Mundial de la Salud (OMS), alrededor de 249 mil muertes prematuras fueron atribuibles a la contaminación del aire exterior y alrededor de 83 mil muertes prematuras fueron atribuibles a la contaminación del aire debido al uso de combustibles sólidos en la vivienda en las Américas en 2016. Además, los contaminantes climáticos de vida corta, como el carbono negro, son poderosos forzadores del clima con posibles consecuencias negativas sobre el calentamiento global y su impacto en la salud. \n \n El cambio climático y la contaminación del aire, tienen relación entre sí. En primer lugar, el cambio climático se produce por la emisión de gases de efecto invernadero (GEI), principalmente por el dióxido de carbono (CO2), pero también por otros gases como el metano (CH4) o el óxido nitroso (N2O), y provoca el aumento de la temperatura global del planeta. Por su parte, la contaminación del aire es la presencia en el aire de sustancias o partículas que implican riesgo, daño o molestia para el ser humano, la flora o la fauna. \n \n¿Cómo se conectan? El incremento de la emisión de CO2 provoca el calentamiento global que deriva en el cambio climático y por consiguiente provoca los efectos climáticos adversos como olas de calor, sequía, inundaciones, etc. Los contaminantes climáticos de vida corta (CCVC) son agentes atmosféricos que contribuyen al cambio climático y deterioran la calidad del aire. \n \n Se les llama así porque tienen una vida útil relativamente corta en la atmósfera, entre estos se encuentran el carbono negro, metano y ozono troposférico, afectando el aire y aumentando el riesgo de padecer enfermedades respiratorias y cardiovasculares.",
    "imagen2":"imagenes/aire2.jpg"
    },
    {
    "titulo": "El futuro de la energía, nuevos horizontes.",
    "imagen1": "imagenes/gas.jpg",
    "contenido": "Gas natural licuado: GNL.\n \nSe trata de un gas combustible que proviene de formaciones geológicas, por lo que constituye una fuente de energía no renovable. \n \n El gas natural licuado (GNL) es gas natural en fase liquida a una temperatura de -160°c, por lo que se considera un liquida criogénico. La ventaja de su estado líquido es su menor volumen, pues por cada litro de GNL se obtiene aproximadamente 540 litros de gas natural gaseoso a temperatura ambiente. \n \n El GNL está formado en un 95% por metano (CH4) y contiene proporciones menores de etano, propano, butano nitrógeno y dióxido de carbono. Es un combustible inoloro e incoloro que no es toxico ni corrosivo y en un hipotético derrame en la tierra o agua, se evaporará y se elevaría a la atmosfera, sin dejar residuos, gracias a que es un 35-40% más liviano que el aire, este experimenta una creciente demanda global debido a su eficiencia, menor impacto ambiental y amplio uso.  \n \n Destacar también el importante ahorro que permite el GNL, ya que se trata de un combustible más económico que el resto de los que podemos encontrar en el mercado. El GNL se está convirtiendo en una alternativa real y valorada en el sector marítimo, tanto en el transporte como en el de mercancías. \n \n Un estudio realizado por el DTI (2010), analiza que la presencia de Nitrógeno (NO2) a determinadas concentraciones en el gas natural podría generar un incremento en la formación de foto-oxidantes tales como los óxidos nitrosos (NOx), dañinos a la salud humana y al ecosistema. \n \n Por otra parte, este gas es menos inflamable que los otros combustibles. Para que se produzca la combustión, debe de haber presencia de oxígeno, concentración de gas natural entre un 4.5% y el 14,5% y un elemento que produzca calor, capaz de provocar la ignición. \n \n Gas natural puro: GNP\n \nComo dijo Arévalo Uribe (2018). Cualquier materia presente en el universo puede estar en el sistema de tres fases: sólido, líquido o gaseoso. Por ejemplo: hielo, agua líquida y vapor de agua, son tres fases, cada una físicamente distinta y homogénea, claramente separadas. \n \n El gas natural es un hidrocarburo en estado gaseoso que proviene, en su mayoría, de la descomposición orgánica de animales o vegetales en depósitos subterráneos que pueden estar ubicados tanto en tierra firme como bajo mares. \n \n Diferentes grupos de petrofísicos y geólogos se encargan del estadio, hallazgo, extracción y procesamiento del gas natural, una vez se perfora el pozo, este recurso sale por flujo natural a la superficie para luego ser transparente hasta una planta de tratamiento. \n \n Una vez los fluidos llegan a la planta, se someten a varios procesos: \n \nFase inicial: Separación primaria, en donde el agua de formación y los hidrocarburos líquidos se separan de los fluidos gaseosos. \n \n Etapa de deshidratación: En esta fase se separan las moléculas gaseosas del agua con el fin de evitar la corrosión (oxidación) dentro de las tuberías. \n \n Proceso de condensación: Aquí se retiran las partículas de hidrocarburos que pueden generar que el gas se vuelva líquido en el proceso de transporte y llegue a ser perjudícales para el usuario final. \n \n De esta manera se obtiene gas natural puro. Sin embargo, es importante darle ese olor   distintivo antes de ponerlo en producción. Así es, Este gas natural también se considera una fuente de energía segura. Los sistemas de gas actuales son muy seguros y se aplican procedimientos estrictos a cada equipo. \n \n El gas natural es una importante fuente de energía fósil y tiene el menor impacto   ambiental en comparación con otros combustibles fósiles, ya que su combustión no produce partículas sólidas ni azufre y produce emisiones mínimas de CO2. Además, el gas natural estará disponible en cantidades suficientes durante las próximas décadas. \n \n Gas natural comprimido: GNC \n \n El gas natural comprimido es una alternativa real a los combustibles derivando del petróleo, mucho más caros y contaminantes. El GNC se compone, entre un 80-90% de metano (CH$) y el resto se constituye por adicciones de dióxido de carbono, nitrógeno e hidrogeno. No contiene azufre, partículas, tranzas de plomo, metales pesados, aditivos tóxicos de plomo orgánico ni benceno. \n \n Según Wesley Guedes (2015), Básicamente la magnitud de desviación de los gases reales con respecto a los gases naturales incrementa cuando incrementamos la presión y temperatura, variando también con la composición del gas. El comportamiento de un gas real es diferente a un gas natural. \n \n El gas natural comprimido puede ser utilizado directamente como combustible, sin modificación químicas, lo que supone una importante ventaja de costes en comparación con otros combustibles, pero dependiendo de dónde proceda de gas natural, es necesario sometería a un ciclo de depuración o deshidratación. \n \n Los vehículos que utilizan gas natural comprimido tienen un menor impacto medioambiental al reducir la emisión de monóxido de carbono, la de óxidos nitrosos, la de hidrocarburos, los óxidos de nitrógeno y el dióxido de carbono. \n \n Al tratarse de un combustible no toxico o corrosivo, el gas natural comprimido no tiene ningún riesgo ambiental en caso de fuga. Gracias a que es más ligero que el aire y que se disipa fácilmente hacia arriba, en lugares ventilados, es seguro de suministrar, almacenar y consumir. \n \n El GNC es más económico que los combustibles tradicionales derivados del petróleo cuyo precio es más inestable. El gas natural tiene un precio más estable, especialmente gracias a que su precio está protegido antes factores externos. El gas natural comprimido es un combustible abundante, respetuoso con el medio ambiente y viable económicamente, que cuenta con la infraestructura necesaria para poder abastecer a toda la flota mundial automotriz durante los próximos 40 años.",
    "imagen2":"imagenes/gas2.jpg"
    },
    {
    "titulo": "El combustible: El impulso hacia el futuro.",
    "imagen1": "imagenes/combus.jpg",
    "contenido": "El exceso de velocidad y la falta de responsabilidad.\n \n Altas cifras de victimas mortales.\n \n Se han reportado tristemente cifras considerables de víctimas mortales debidas al exceso de velocidad y al estado de ebriedad. En este sentido, es necesario un análisis y una evaluación exhaustiva para tomar medidas en pro de la seguridad y la prevención de accidentes en las carreteras.En lo que va del año, la cantidad de fallecidos en accidentes de tránsito es muy alta. Según reportes policiales, en la primera semana del 2023 se perdieron 23 vidas, y entre el 9 y el 15 de enero sesumaron 16 fallecimientos más. Estos números se incrementaron en el mes de febrero, en donde se registraron 960 accidentes que dejaron 20 personas muertas. Hasta el momento, la cantidad de personas fallecidas asciende a 39 y se han reportado 70 personas lesionadas.Cada vez es más evidente la relación entre la velocidad y los accidentes de tráfico, especialmente en las vías urbanas. La imprudencia al volante, la falta de conocimiento y el uso de dispositivos móviles mientras seconduce, que puede acabar con la vida de inocentes. En ese sentido, es importante promover campañas de concientización que hagan hincapié en la necesidad de respetar las normas de tránsito y las velocidades máximas permitidas.\n \n También se destaca la importancia de aplicar medidas más rigurosas en cuanto a la alcoholemia, tanto en los conductores de automóviles como en los ciclistas y motoristas. La implementación de sistemas rigurosos de control y sanciones efectivas a los infractores podría ser un primer paso en el camino hacia una reducción significativa de las víctimas de accidentes de tránsito.Es responsabilidad de todos los miembros de la sociedad mantener un compromiso firme con la seguridad vial, y trabajar juntos en la prevención de accidentes, que lamentablemente ha venido en aumento en los primeros meses del año (Swissinfo.ch, 2023).\n \n PORCENTAJES DE ACCIDENTES EN CHONTALES 2023.\n \n El número de víctimas mortales y daños causados por accidentes de tránsitos.\n \n El año 2023 ha sido un período bastante complicado según la Policía en cuanto a la circulación del tránsito se refiere. Los accidentes en carretera y en las calles de la ciudad han ido en aumento, se han registrado un alarmante número de accidentes automovilísticos que han dejado a su paso pérdidas materiales, y lo peor, pérdidas humanas. A continuación, se detallarán las cifras de los accidentes registrados en los últimos meses, con la intención de concientizar sobre la importancia de respetar las normativas viales.\n \n En los últimos meses se han presentado 312 accidentes vehiculares en diferentes partes de la ciudad. De estos, 61 han sido en automóviles, con una cantidad de daños materiales variados. Además, se han registrado seis víctimas, entre ellas, un fallecido, tres heridos de gravedad y dos leves.En cuanto a las camionetas, se reportaron 15 víctimas, seis de ellas fallecidas, siete en estado grave y diez leves.\n \n Los accidentes más comunes en estos casos son las colisiones por la parte trasera de los vehículos, así como también el exceso de velocidad en la conducción.\n \n Por otro lado, las motocicletas se han convertido en otro foco de accidentes viales.En total, se registraron 73 accidentes, dejando como resultado 35 víctimas, seis de ellas fallecidas, 32 en estado grave y diez leves. Muchos de estos accidentes involucran la falta de uso de elementos de seguridad para el conductor, como el casco protector.\n \n Estos números son alarmantes y deberían preocupar a toda la sociedad, pues reflejan la amenaza constante que representa la circulación vehicular. Es por ello que es necesario que se implementen campañas preventivas para la disminución de las cifras de accidentes y se refuercen las medidas de seguridad vial. Conducir de manera responsable es una responsabilidad de todos, y una ayuda para evitar pérdidas humanas y económicas.\n \n LOS DATOS NO MIENTEN.\n \n Estadísticas de vehículos involucrados en accidentes de tránsito.\n \n De enero a mayo del presente año, se han registrado un total de 312 accidentes de tránsito en el país, según información de la Policía Nacional de Tránsito. Estos accidentes han provocado daños materiales, víctimas, muertos y graves consecuencias.\n \n En un análisis detallado, se determinó que los vehículos más involucrados en estos accidentes son las camionetas y las motocicletas. En primer lugar, encontramos las camionetas que han causado 102 accidentes, dejando como saldo 15 víctimas, 6 muertos, 7 graves y 10 con lesiones leves.\n \n En segundo lugar, las motocicletas con 73 accidentes registrados, con un impactante número de 35 víctimas, 6 muertos, 32 graves y 10 lesionados leves.Los camiones ocupan el tercer lugar de la lista, con un total de 6 accidentes con víctimas, 4 muertos y 3 graves; mientras que los buses y cabezales registraron 16 y 11 accidentes, respectivamente, con un total de 3 víctimas, 1 muerto y 2 graves.\n \n Cabe resaltar que, además de los vehículos mencionados, también se han presentado 6 accidentes protagonizados por unidades desconocidas, con 2 víctimas y 2 muertos.\n \n Además de estos vehículos antes mencionados, existen otros que han provocado accidentes mínimos; entre ellos las bicicletas que han dejado 2 accidentes con 2 víctimas y 2 lesionados, uno más añadido a la lista son los microbuses contando con 4 accidentes, ningún muerto y ningún lesionado.\n \n Es importante recalcar que, detrás de cada accidente hay una historia que involucra a personas que sufren las consecuencias de estas situaciones, y en muchos casos, sus vidas se ven afectadas de manera irreversible.",
    "imagen2":"imagenes/combus2.jpg"
    },
    {
    "titulo": "Cuido y preservación: Recursos Naturales.",
    "imagen1": "imagenes/cuido2.jpg",
    "contenido": "Reciclaje: Un amino hacia la sostenibilidad y la conservación del planeta. \n \n El reciclaje es una de las practicas que se realizan para la conservación y salud del medio ambiente, así como también una manera de conservar la diversidad natural, la conservación de nuestros recursos naturales y la vida que nos rodea. \n \n Según, Roberto Pérez (recolector de botellas plásticas, originario de la ciudad de Juigalpa), lleva ejerciendo este oficio 10 años y más que una forma de ganar dinero, es un oficio en el cual el contribuye con el bienestar ambiental, es una manera de contribuir a que estos recursos se reutilicen para distintos fines, él nos cuenta que, en su día a día en el basurero de la ciudad, recolecta en cinco días alrededor de cincuenta kg en botellas plásticas.Doña Juanita Suarez, recolectora de botellas p \n \n lásticas comenta que ella lleva veinte años en la recolección de botellas plásticas, en su rutina de recolección ella suele recoger en algunas zonas, dura un mes en recoger varios kilos de botellas para posteriormente venderlas a un camión que viene directamente de la ciudad de Managua a comprar esta materia prima reciclada. \n \n Don José García, guarda de seguridad del basurero municipal nos comentaba que uno de los beneficios del reciclaje, es el ahorro de energía en la producción de papel reciclado como también en la producción de botellas, además de eso, es de suma importancia ya que al tener materia prima reciclada se contribuye al ahorro de recursos naturales. \n \n Uno de los beneficios que se puede obtener mediante el reciclaje es que se reduce la cantidad de residuos que se pueden producir y así reducir la contaminación del suelo, agua y aire, que son los principales componentes para poder subsistir, es nuestro deber como seres humanos reciclar y evitar la deterioración de nuestros recursos y nuestro planeta. \n \n Beneficio del ahorro energético: Cuidando el planeta y nuestros bolsillos. \n \n Según el sitio web, (electry consulting, 2023), El ahorro energético es una práctica que consiste en reducir el consumo de energía eléctrica en nuestros hogares y lugares de trabajo. Esta práctica tiene una serie de beneficios tanto para el medio ambiente como para nuestra economía personal. \n \n En primer lugar, el ahorro energético es beneficioso para el medio ambiente. La energía que utilizamos en nuestros hogares y lugares de trabajo proviene principalmente de fuentes no renovables como el petróleo, el gas natural y el carbón. Estas fuentes de energía emiten gases de efecto invernadero que contribuyen al cambio climático. Al reducir nuestro consumo de energía, estamos ayudando a disminuir la cantidad de gases de efecto invernadero que se emiten a la atmósfera, además, esto incide directamente en nuestra salud, por lo que es importante saber que también nos ayuda a una mejor calidad de nuestra salud física. Además, el ahorro energético también puede ayudarnos a ahorrar dinero. Al reducir nuestro consumo de energía eléctrica, estamos disminuyendo nuestras facturas de luz. A largo plazo, esto puede suponer un ahorro significativo en nuestra economía personal, Otro beneficio del ahorro energético es que puede aumentar la durabilidad de los electrodomésticos. Al reducir el consumo de energía, estamos disminuyendo la cantidad de estrés que ponemos en nuestros aparatos eléctricos. Esto puede hacer que nuestros electrodomésticos duren más tiempo y que necesitemos repararlos con menos frecuencia. \n \n La señora María Josefa Centeno, nos cuenta que en su hogar practica el ahorro energético desconectado algunos electrodomésticos que no estén en uso y así con esto poder reducir el consumo innecesario de energía, ya que, el tener los conectores pegados al toma corriente estos se sobrecargan, así como también reducir los costos de las facturas de energía, lo cual le ha ayudado mucho en su economía. \n \n Aprovechamiento de los recursos: Clave para un Futuro Sostenible. \n \nSegún el sitio web, (atecé, 2023), Los recursos renovables y los recursos no renovables son recursos naturales usados por el ser humano para la producción de energía, bienes o servicios y se diferencian entre sí por su poder de regeneración. \n \n Los recursos no renovables. Son aquellos que una vez que los utilizó para el consumo no es posible su renovación o requiere miles o millones de años. Por ejemplo: el petróleo. \n \n Los recursos renovables. Son aquellos que se desgastan por su consumo, pero se regeneran rápidamente de forma natural o por acción humana. Además, estos recursos se caracterizan por ser sustentables. Por ejemplo: el agua dulce o el aire. \n \n En Nicaragua el aprovechamiento de los recursos naturales es indispensable para la producción de granos básicos, ganadería, pesca etc. Don Julio Picado ganadero de la zona de carcas, Juigalpa, nos cuenta, que en el ámbito de crianza de bovinos es de vital importancia contar con un suministro de agua, ya que los animales necesitan del vital líquido para su sano desarrollo y posteriormente su crecimiento, por lo cual es indispensable que en cualquier hato ganadero haya este valioso recurso, el cual repercute en los productos finales ya sea en la producción de carne, así como también en la producción de leche. \n \n De esta manera el aprovechamiento de recursos renovables y no renovables son la clave para garantizar un futuro que sea sostenible, también para poder proteger al medio ambiente, así que es de suma importancia cuidar nuestros recursos ya que son la base para el desarrollo, una forma de hacerlo son los viveros estos contribuyen a la restauración ecológica de manera segura, como un motor positivo de cambio, porque disminuimos la contaminación hacia nuestros recursos naturales y ayuda a generar un cambio muy positivo para la sociedad." ,
    "imagen2":"imagenes/cuido1.jpg"
    }
    ]
   }
   <!DOCTYPE html>
<html>
<head>
 <title>Ambiente y Sociedad</title>
 <link rel="stylesheet" type="text/css" href="estilos.css">
 <link rel="shortcut icon" href="favicon.ico" type="image/x-icon">
</head>

<body>
    <img class="logo" src="imagenes/logo.png" alt="" width=20px>
 <h1 id="revista-titulo"></h1>
 <head>
  <style>
    .search-button {
      text-align: right;
      margin: 30px;
    }
    
    .search-button input[type="text"] {
      padding: 5px;
    }
    
    .search-button button[type="submit"] {
      background-color: #0c8d00;
      color: white;
      padding: 5px 10px;
      border: none;
    }
  </style>
</head>
<body>
  <div class="search-button">
    <input type="text" placeholder="Buscar">
    <button type="submit">Buscar</button>
  </div>
 <div id="articulos-container"></div>
 <div id="modal" class="modal">
 <div class="modal-content">
 <span class="close">&times;</span>
 <h2 id="modal-titulo"></h2>
 <img id="modal-imagen1" src="" alt="" class="modal-imagen">
      <p id="modal-contenido"></p>
      <img id="modal-imagen2" src="" alt="" class="modal-imagen">
    </div>
  </div>
  <a href="https://youtu.be/CyfPQ3HooLs" class="button">Reportaje</a>  <script src="app.js"></script>
  <a href="https://drive.google.com/file/d/1UzBswfj2ZtE4W9faKGg6yVgQBLepEDXK/view?usp=sharing" class="button">Revista Digital</a>
  <a href="https://sites.google.com/view/ambienteysociedad1/documentos" class="button">Portafolio Digital</a>
  

</body>

</html>
