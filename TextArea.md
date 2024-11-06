# Proyecto: Editor de Texto

Este proyecto es un editor de texto implementado en React, con capacidades de manejo de texto en tiempo real

## Habilidades y Requerimientos Implementados

### Habilidad 1: Componente `TextArea` con Personalización de Texto

#### Descripción de la Habilidad
Crear un componente `TextArea` que reciba como propiedades el contenido de texto, un manejador de cambios y estilos personalizados para adaptar el aspecto del texto en el editor.

#### Código de Implementación
```typescript
import React from 'react';

interface Props {
  texto: string;
  onTextoChange: (event: React.ChangeEvent<HTMLTextAreaElement>) => void;
  textoEstilizado: React.CSSProperties; // Propiedad para aplicar estilos al texto
}

const TextArea: React.FC<Props> = ({ texto, onTextoChange, textoEstilizado }) => {
  return (
    <textarea
      className="text-area"
      value={texto}
      onChange={onTextoChange}
      placeholder="Escribe algo..."
      style={textoEstilizado} // Aplica estilos personalizados al área de texto
    />
  );
};

export default TextArea;

### Explicación Detallada

- **¿Qué hace este fragmento de código?**  
   Este fragmento de código define un componente `TextArea` en React que recibe tres propiedades: `texto`, `onTextoChange` y `textoEstilizado`. La propiedad `texto` contiene el contenido del área de texto, que se actualiza a medida que el usuario escribe. La propiedad `onTextoChange` es una función que maneja el evento de cambio de texto (`onChange`) para actualizar el valor de `texto` en el estado del componente padre. La propiedad `textoEstilizado` es un objeto de estilo en línea (`CSSProperties`) que permite aplicar diferentes estilos visuales al área de texto, tales como color, tamaño, tipo de fuente, y estilos de texto como negrita, cursiva y subrayado.

- **¿Cómo cumple con el requisito de la habilidad?**  
   Este código cumple con los requisitos del proyecto al permitir la personalización dinámica del área de texto en un editor. El uso de `textoEstilizado` permite a los usuarios aplicar múltiples estilos al texto sin necesidad de escribir estilos adicionales en el código base. Además, al utilizar la propiedad `onTextoChange`, el componente puede reaccionar a cambios en el texto, lo cual es esencial para un editor de texto en tiempo real.

- **¿Por qué es la mejor forma de implementarlo?**  
   Este enfoque es eficiente porque utiliza las capacidades de React para manejar cambios en el estado del componente (`texto`) y aplicar estilos a través de una propiedad (`textoEstilizado`). Al emplear el objeto `CSSProperties`, se consigue un control total sobre los estilos sin necesidad de manipular el DOM directamente. Esto no solo mejora la reutilización del componente, sino que también facilita la escalabilidad del proyecto, ya que se pueden agregar más propiedades o funcionalidades a la misma estructura sin complicar el código ni la lógica del componente.

