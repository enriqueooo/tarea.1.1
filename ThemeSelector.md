# Proyecto: Editor de Texto

Este proyecto es un editor de texto implementado en React, con capacidades de manejo de texto en tiempo real.

## Habilidades y Requerimientos Implementados

### Habilidad 2: Componente `ThemeSelector` para Personalización de Estilos de Texto

#### Descripción de la Habilidad
Crear un componente `ThemeSelector` que permita al usuario personalizar el texto mediante la selección de colores, y aplicar estilos de formato como negrita, cursiva y subrayado. Este componente maneja la interacción con los botones para aplicar los estilos y cambiar el color del texto.

#### Código de Implementación
```typescript
import React from 'react';

interface Props {
  onColorChange: (color: string) => void; 
  toggleBold: () => void; // Function to toggle bold
  toggleItalic: () => void; // Function to toggle italic
  toggleUnderline: () => void; // Function to toggle underline
}

const ThemeSelector: React.FC<Props> = ({ onColorChange, toggleBold, toggleItalic, toggleUnderline }) => {
  const colors = [
    '#FF5733', '#33FF57', '#3357FF', '#FF33A8', '#A833FF', 
    '#FFC300', '#FF914D', '#4DFF94', '#4D94FF', '#FF4D4D'
  ];

  return (
    <div className="theme-selector">
      {/* Buttons to change the text color */}
      <div className="color-picker">
        {colors.map((color) => (
          <button
            key={color}
            style={{ backgroundColor: color }}
            onClick={() => onColorChange(color)}
            className="color-button"
          />
        ))}
      </div>

      {/* Format buttons */}
      <div className="format-buttons">
        <button onClick={toggleBold} className="format-button">N</button>
        <button onClick={toggleItalic} className="format-button">C</button>
        <button onClick={toggleUnderline} className="format-button">S</button>
      </div>
    </div>
  );
};

export default ThemeSelector;

# Explicación Detallada

- **¿Qué hace este fragmento de código?**  
   Este fragmento de código define un componente `ThemeSelector` en React, el cual permite al usuario seleccionar un color para el texto y aplicar estilos de formato (negrita, cursiva y subrayado) mediante botones. La propiedad `onColorChange` permite cambiar el color del texto, y las propiedades `toggleBold`, `toggleItalic`, y `toggleUnderline` permiten alternar entre los estilos de formato para el texto. La lista de colores se mapea para generar un conjunto de botones, cada uno representando un color. Al hacer clic en uno de estos botones, el color del texto en el editor cambia. Los botones de formato se usan para aplicar o quitar los estilos de texto.

- **¿Cómo cumple con el requisito de la habilidad?**  
   Este código cumple con el requisito de permitir al usuario personalizar la apariencia del texto mediante la selección de colores y la aplicación de estilos de texto (negrita, cursiva y subrayado). Los botones de color permiten cambiar el color del texto de forma inmediata, y los botones de formato permiten aplicar estilos como negrita, cursiva y subrayado de manera rápida. La interfaz es interactiva y responde a las acciones del usuario en tiempo real, lo que mejora la experiencia de edición.

- **¿Por qué es la mejor forma de implementarlo?**  
   Esta implementación es eficiente porque centraliza el control del cambio de color y formato en funciones específicas (como `onColorChange` y `toggleBold`), lo que hace que el código sea más limpio y modular. El uso de una lista de colores para los botones permite un diseño sencillo y flexible para agregar o quitar colores sin modificar mucho el código. Además, al tener botones de formato dedicados, el usuario puede aplicar estilos de forma clara y directa. Esta estructura es escalable, ya que en el futuro se pueden agregar más opciones de formato sin complicar la lógica existente.
