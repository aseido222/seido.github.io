# Julia en las Universidades

***

**AUTOR:** Msc. Alexey Seisdedo Losa

**Fecha:** 08 de julio de 2024

***

### Resumen

Presentación de las principales características del lenguaje de programación Julia y las ventajas de su introducción como herramienta de procesamiento, análisis y desarrollo en la carrera de ingeniería en telecomunicaciones y electrónica.

***


## La ingeniería en Telecomunicaciones

La ingeniería en telecomunicaciones como especialidad técnica conlleva
el estudio constante de un volumen considerable de asignaturas, cálculo
matemático, física, química y otras en la etapa básica. Electrónica
analógica y digital, teoría de circuitos y radio propagación son algunas
de ellas en la etapa avanzada.

En todas, es inherente un sentido de abstracción profundo en el
desarrollo del marco teórico que se lleva a las aulas por parte del
profesorado y que muchas veces, incide negativamente en la puesta en
práctica de aquellos conocimientos que previamente debían ser asimilados
en los laboratorios y trabajos extracurriculares. La imbricación de la
teoría con la utilización de las nuevas tecnologías debe ir más allá de
la simple utilización del ordenador como herramienta de estudio en la
lectura de materiales y la confección de reportes de investigaciones o
trabajos realizados. Debe constituir el medio para incrementar la
capacidad de análisis, la experimentación y la manera que ese marco
teórico precedente, se manifiesta en la vida cotidiana y permita al
futuro ingeniero afrontar, con una sólida base el reto del mercado
laboral moderno sin que por ello pierda la capacidad y la habilidad de
trabajo con elementos no digitales.

## Por qué Julia?

Julia es un lenguaje de programación de alto nivel, diseñado
específicamente para el cómputo científico y la estadística. Fué creado
en el año 2009 por un grupo de investigadores (Jeff Bezanson, Stefan
Karpinski, Viral Shah, y Alan Edelman(Mira 2020)) en la Universidad de
California, Berkeley, y se lanzó oficialmente en el año 2012.

Julia combina la facilidad de uso de lenguajes como Python y R con el
rendimiento de lenguajes de bajo nivel como C y Fortran. Utiliza una
sintaxis clara y concisa, similar a la de MATLAB, y cuenta con una
amplia variedad de paquetes y librerías especializadas para estadística,
ciencias de datos y otros.

Julia tiene varias ventajas que lo hacen especialmente útil:

-   Rendimiento: Julia se ejecuta muy rápidamente gracias a su
    compilación *just-in-time* (JIT) y a la capacidad de definir tipos
    de datos específicos para mejorar el rendimiento. Esto significa que
    se puede trabajar con grandes conjuntos de datos y cálculos
    complejos de manera eficiente.

-   Sintaxis clara y expresiva: Julia tiene una sintaxis intuitiva y
    fácil de aprender, que se asemeja a la de otros lenguajes populares
    como MATLAB o Python. Esto hace que sea fácil para los nuevos
    usuarios comenzar a trabajar con él.

-   Interoperabilidad: Julia es capaz de integrarse fácilmente con otros
    lenguajes como Python, R y C. Esto significa que los usuarios pueden
    aprovechar las bibliotecas y paquetes de otros lenguajes y
    combinarlos con Julia para obtener el mejor rendimiento posible.

-   Paquetes especializados: Julia cuenta con una amplia variedad de
    paquetes especializados para estadástica y ciencias de datos, como
    DataFrames.jl, Plots.jl, StatsModels.jl y muchas otras. Esto
    facilita mucho el trabajo con datos y cálculos estadísticos(Santos
    2023).

Todas estas características lo hacen muy interesante para su inclusión
como herramienta en la especialidad de telecomunicaciones.

Julia es, por lo anterior, junto a R, Python y C/C++ la opción que
muchos profesionales de este ámbito deberían tener dentro de su espectro
de conocimientos, aunque existan opiniones controvertidas (Fischer
2020),(Moura 2021), lo más importante es tener siempre a mano la
herramienta más útil para el *caso de uso* específico.

A los estudiantes Julia brinda un nuevo enfoque tanto en el desarrollo
de software como para la ciencia de datos y la interpretación de los
mismos. Todo lo que se hace en Python o en R, puede hacerse en Julia con
la ventaja de poder escribir código legible, rápido y potente. Está
pensado para ser rápido, generar código optimizado para la máquina de
forma automática y evitar tener que emplear cosas como Python + Fortran
(Problema de los dos lenguajes)(Maldonado 2023),(s. f.a).

Julia con una gran comunidad y desarrollo sostenido se ha ido
posicionando como un lenguaje clave en el presente y futuro (s. f.b).

## Manos a la obra con Julia

El universo de paquetes de Julia aumenta día a día con el apoyo de la
comunidad y otros interesados al respecto. Ejemplo del desarrollo de
elementos que se vinculan directamente a la especialidad que se trata,
está en ACME.jl.

ACME.jl es un paquete para la simulación de circuitos eléctricos,
enfocado en los de efectos de audio. Este permite describir de forma
programática, muy clara, un circuito en término de sus elementos y las
conexiones entre ellos, derivándose automáticamente en un modelo de
dicho circuito. Este modelo puede ser corrido computacionalmente con
diferentes datos de entrada («ACME.Jl», s. f.),(«ACME.Jl - Analog
Circuit Modeling and Emulation for Julia», s. f.).

ACME está basado en el método descrito en M. Holters, U. Zölzer, *“A
Generalized Method for the Derivation of Non-Linear State-Space Models
from Circuit Schematics”*(Holters y Zolzer, s. f.).

Ejemplo:

    using ACME
    circ = @circuit begin
        j_in = voltagesource()
        r1 = resistor(1e3)
        c1 = capacitor(47e-9)
        d1 = diode(is=1e-15)
        d2 = diode(is=1.8e-15)
        j_out = voltageprobe()
        j_in[+] ⟷ r1[1]
        j_in[-] ⟷ gnd
        r1[2] ⟷ c1[1] ⟷ d1[+] ⟷ d2[-] ⟷ j_out[+]
        gnd ⟷ c1[2] ⟷ d1[-] ⟷ d2[+] ⟷ j_out[-]
    end
    model = DiscreteModel(circ, 1/44100)
    y = run!(model, [sin(2π*1000/44100*n) for c in 1:1, n in 0:44099])

Otro ejemplo con aplicación específica es PETLION.jl (M. D. Berliner
et al. 2021). Este permite realizar simulaciones de alto rendimiento del
modelo teórico de electrodos porosos (PET) *pseudo-2D* en Julia («Readme
· PETLION.Jl», s. f.).

Existen muchos casos de uso y paquetes útiles, pero el análisis de estos
se sale del alcance de este artículo, no obstante, pueden ser
consultados varios de los ejemplos en línea. (M. Berliner, s. f.)

En la red abundan los ejemplos de la utilización cada vez más grande de
Julia en múltiples ramas del del conocimiento humano y a ello no escapan
las especialidades técnicas como las telecomunicaciones.

Difundir la utilización del mismo por parte de los profesores dentro de
las propias materias a tratar, en la resolución de problemas y
simulaciones de eventos, fenómenos etc, por parte de los estudiantes
durante el curso de sus estudios, dotarían a estos de una potente
herramienta en las investigaciones, aspecto importante en la vinculación
de las universidades a los elementos productivos, y en el desafiante
mundo laboral al que se enfrentaran los futuros ingenieros.

### Y cómo lo hacemos..?

[Julia](https://julialang.org/downloads/) se obtiene directamente desde
su sitio y siguiendo las indicaciones dadas por sus desarrolladores, es
posible tenerlo rápidamente funcional en el ordenador. Existen varios
entornos de desarrollo utilizados por la comunidad, es desición personal
adoptar aquel que mejor se ajuste a las necesidades propias. No
obstante, una sabia desición sería:

-   el REPL (*Read-Eval-Print Loop*), de sus siglas en Inglés. Una
    interfaz de línea de comando llena de facilidades para interactuar
    con el lenguaje y gestionar la paquetería o módulos necesarios.

-   y [Pluto.jl](https://plutojl.org/), todo un ambiente de programación
    reactivo para Julia que permite la edición de código al estilo de
    *Notebooks*, con características especiales como la inmutabilidad de
    los espacios de trabajo y la integración de un gestor de paquetería.
    Además de la perfecta reproducibilidad de sus *Notebooks* por
    defecto.

La documentación existente tanto para principantes como para proyectos
más avanzados no es tan fácil de encontrar en español, en inglés existen
varios libros y [videos](https://www.youtube.com/@doggodotjl) al
respecto, además siempre está el sitio oficial del proyecto.

## Conclusiones

En un mundo donde las competencias definen el futuro de los
profesionales, es primordial el papel de los facilitadores del
aprendizaje, llevando a los estudiantes las más variadas y actualizadas
herramientas que le permitan crear habilidades profesionales de amplio
espectro, en algunos casos definitorias.

Es tarea de estos facilitadores imbricar la utilización de estas
herramientas en los programas clásicos de enseñanza, promoviendo las
buenas prácticas en el desarrollo de nuevas ideas y a la postre de
mejores profesionales.

El universo de Julia, en constante expansión, es un excelente ejemplo de
como se puede vincular no solo la computación científica desde el punto
de vista del desarrollador de software sino también como científico de
datos, analista, desarrollador de inteligencia artificial, aprendizaje
automático, controladores de sistemas automatizados, interfaces,
documentadores de procesos y otros.

Aprender Julia, sin dudas, podría marcar la diferencia en un tiempo no
muy lejano.

## Referencias

s. f.a. <https://theirstack.com/es/technology/julia>.

———. s. f.b.
<https://www.intel.com/content/dam/www/public/us/en/documents/presentation/julia-in-parallel-and-high-performance-computing.pdf>.

«ACME.Jl». s. f. <https://hsu-ant.github.io/ACME.jl/dev/>.

«ACME.Jl - Analog Circuit Modeling and Emulation for Julia». s. f.

Berliner, Marc. s. f. «examples at master · MarcBerliner/PETLION.jl».

Berliner, Marc D, Daniel A Cogswell, Martin Z Bazant, y Richard D
Braatz. 2021. «Methods—PETLION: Open-Source Software for
Millisecond-Scale Porous Electrode Theory-Based Lithium-Ion Battery
Simulations». *Journal of The Electrochemical Society* 168 (9): 090504.

Fischer, Daniel. 2020. «Comparativa entre Julia, Python y R».
<https://www.geekosas.com/index.php/2020/04/07/comparativa-entre-julia-python-y-r/>.

Holters, Martin, y Udo Zolzer. s. f. «A generalized method for the
derivation of non-linear state-space models from circuit schematics».
<https://www.eurasip.org/Proceedings/Eusipco/Eusipco2015/papers/1570103545.pdf>.

Maldonado, Josué Acevedo. 2023. «Julia para la ciencia de datos. - Josué
Acevedo Maldonado».
<https://josueacevedo.medium.com/julia-para-la-ciencia-de-datos-be04a25b592c>.

Mira, Adrián Rodrı́guez. 2020. «Lenguaje de programacion Julia: ideal
para Machine Learning».
<https://www.tokioschool.com/noticias/lenguaje-programacion-julia/>.

Moura, Daniel. 2021. «R vs Python vs Julia: Efficient code».
<https://towardsdatascience.com/r-vs-python-vs-julia-90456a2bcbab>.

«Readme · PETLION.Jl». s. f.
<https://docs.juliahub.com/General/PETLION/stable/>.

Santos, Franklin. 2023. «JULIA: Lenguaje de programación del futuro».
<https://www.franklinsantosm.com/posts/julia/>.
