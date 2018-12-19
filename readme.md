# d3 bundle

La v4.0 de d3.js modularizo todo el código. Así que aprovechando el sistema de modulos de ES2015 podemos generar un bundle que solamente contenga los módulos que vamos a utilizar. 

Para crear el bundle necesitamos rollup. Una vez creado usamos uglify para minificar el código.

La configuración para rollup, en entry le indicamos el archivo que contendra todos los módulos que queremos incluir en el bundle. En dest la ruta donde generar el bundle.

Así quedaría el archivo `rollup.config.js`

```
import node from "rollup-plugin-node-resolve";

export default {
  entry: "index.js",
  format: "umd",
  moduleName: "d3",
  plugins: [node()],
  dest: "d3.js"
};
```

El index.js con los módulos que necesitamos

```
export {
    select,
    selectAll
} from "d3-selection";

export {
    area
} from "d3-shape";

export {
    scaleTime,
    scaleLinear
} from "d3-scale";

export {
    axisBottom,
    axisLeft
} from "d3-axis";

export {
    csv
} from "d3-request";

export {
    easeLinear
} from "d3-ease";

export {
    format
} from "d3-format";

import "d3-transition";
```

Todos estos módulos los tenemos que instalar como paquetes de npm.

Ahora lanzaremos con npm el ```build:d3``` que primero creara un bundle y a continuación uglify se encargara de minificar el código y servirlo en la carpeta de js.

```
"build:d3": "rollup -c && uglifyjs d3.js -c -m -o js/d3.min.js"
```

El bundle para hacer la gráfica de area ocupa 84kb. El tamaño de la v4.11.0 de d3 es de 220kb. La diferencia es bastante notable.

## Modulos

A continuación todos los módulos de d3. 

[d3-array](https://github.com/d3/d3-array)   
[d3-axis](https://github.com/d3/d3-axis)   
[d3-brush](https://github.com/d3/d3-brush)   
[d3-chord](https://github.com/d3/d3-chord)   
d3-collection > Deprecation notice   
[d3-color](https://github.com/d3/d3-color)   
[d3-dispatch](https://github.com/d3/d3-color)   
[d3-drag](https://github.com/d3/d3-drag)   
[d3-dsv](https://github.com/d3/d3-dsv)   
[d3-ease](https://github.com/d3/d3-ease)   
[d3-force](https://github.com/d3/d3-force)   
[d3-format](https://github.com/d3/d3-format)   
[d3-geo](https://github.com/d3/d3-geo)   
[d3-hierarchy](https://github.com/d3/d3-hierarchy)   
[d3-interpolate](https://github.com/d3/d3-interpolate)   
[d3-path](https://github.com/d3/d3-path)   
[d3-polygon](https://github.com/d3/d3-polygon)   
[d3-quadtree](https://github.com/d3/d3-quadtree)   
[d3-queue](https://github.com/d3/d3-queue)   
[d3-random](https://github.com/d3/d3-random)   
[d3-request](https://github.com/d3/d3-request)   
[d3-scale](https://github.com/d3/d3-scale)   
[d3-selection](https://github.com/d3/d3-selection)   
[d3-shape](https://github.com/d3/d3-shape)   
[d3-time](https://github.com/d3/d3-time)   
[d3-time-format](https://github.com/d3/d3-time-format)   
[d3-timer](https://github.com/d3/d3-timer)   
[d3-transition](https://github.com/d3/d3-transition)   
[d3-voronoi](https://github.com/d3/d3-voronoi)   
[d3-zoom](https://github.com/d3/d3-zoom)   
