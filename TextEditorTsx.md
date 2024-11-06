# Proyecto: Editor de Texto

Este proyecto es un editor de texto implementado en React, con capacidades de manejo de texto en tiempo real y personalización avanzada del estilo.

---

## Habilidades y Requerimientos Implementados

### Habilidad 1: Componente `TextEditor` con Personalización de Texto y Estilo

#### Descripción de la Habilidad
Crear un editor de texto que permita personalizar el color, la fuente, el tamaño de la fuente, y aplicar estilos como negrita, cursiva y subrayado. El área de texto debe ser editable, y los cambios deben reflejarse en tiempo real, tanto en el área de texto como en una vista previa del contenido.

#### Código de Implementación
```typescript
import React, { useState, useRef, useEffect } from 'react';
import ThemeSelector from './ThemeSelector'; 
import './TextEditor.css'; // Asegúrate de que este archivo CSS exista

const TextEditor: React.FC = () => {
  const [text, setText] = useState('');
  const [color, setColor] = useState('#000000'); // Color inicial
  const [isBold, setIsBold] = useState(false);
  const [isItalic, setIsItalic] = useState(false);
  const [isUnderline, setIsUnderline] = useState(false);
  const [fontFamily, setFontFamily] = useState('Arial'); // Fuente inicial
  const [fontSize, setFontSize] = useState('16px'); // Tamaño de fuente inicial
  const [background, setBackground] = useState('#FFFFFF'); // Color de fondo

  const textAreaRef = useRef<HTMLDivElement>(null); // useRef para el área editable

  // Funciones para manejar cambios de estilo
  const toggleBold = () => setIsBold((prev) => !prev);
  const toggleItalic = () => setIsItalic((prev) => !prev);
  const toggleUnderline = () => setIsUnderline((prev) => !prev);

  // Cambiar el color del texto
  const onColorChange = (color: string) => {
    setColor(color);
  };

  // Cambiar la fuente del texto
  const onFontChange = (font: string) => {
    setFontFamily(font);
  };

  // Cambiar el tamaño de la fuente
  const onFontSizeChange = (size: string) => {
    setFontSize(size);
  };

  useEffect(() => {
    if (textAreaRef.current) {
      textAreaRef.current.focus(); // Enfocar el área de texto al cargar
    }
  }, []);

  // Función para colocar el cursor al final del contenido
  const moveCursorToEnd = () => {
    const element = textAreaRef.current;
    if (element) {
      const range = document.createRange();
      const selection = window.getSelection();
      range.selectNodeContents(element);
      range.collapse(false); // Colapsa el rango al final del contenido
      selection?.removeAllRanges();
      selection?.addRange(range);
    }
  };

  return (
    <div className="text-editor" style={{ backgroundColor: background }}>
      <ThemeSelector
        onColorChange={onColorChange}
        toggleBold={toggleBold}
        toggleItalic={toggleItalic}
        toggleUnderline={toggleUnderline}
      />

      {/* Selector de Fuente */}
      <div className="font-selector">
        <label>Font Family: </label>
        <select value={fontFamily} onChange={(e) => onFontChange(e.target.value)}>
          <option value="Arial">Arial</option>
          <option value="Courier New">Courier New</option>
          <option value="Georgia">Georgia</option>
          <option value="Times New Roman">Times New Roman</option>
          <option value="Verdana">Verdana</option>
        </select>
      </div>

      {/* Selector de Tamaño de Fuente */}
      <div className="font-size-selector">
        <label>Font Size: </label>
        <select value={fontSize} onChange={(e) => onFontSizeChange(e.target.value)}>
          <option value="12px">12px</option>
          <option value="14px">14px</option>
          <option value="16px">16px</option>
          <option value="18px">18px</option>
          <option value="24px">24px</option>
          <option value="32px">32px</option>
        </select>
      </div>

      <div
        ref={textAreaRef} // Referencia al área de texto editable
        contentEditable
        suppressContentEditableWarning
        style={{
          color: color,
          fontWeight: isBold ? 'bold' : 'normal',
          fontStyle: isItalic ? 'italic' : 'normal',
          textDecoration: isUnderline ? 'underline' : 'none',
          fontFamily: fontFamily, // Fuente seleccionada
          fontSize: fontSize, // Tamaño de fuente seleccionado
          border: '1px solid #ccc',
          padding: '10px',
          minHeight: '200px',
          borderRadius: '5px',
          marginTop: '10px',
        }}
        onInput={(e) => {
          setText(e.currentTarget.textContent || '');
          moveCursorToEnd(); // Mueve el cursor al final
        }}
      >
        {text}
      </div>

      {/* Vista previa del texto */}
      <div className="preview" style={{ color: color, fontWeight: isBold ? 'bold' : 'normal', fontStyle: isItalic ? 'italic' : 'normal', textDecoration: isUnderline ? 'underline' : 'none', fontFamily: fontFamily, fontSize: fontSize }}>
        <h3>Preview:</h3>
        <p>{text || "Type something to see the preview..."}</p>
      </div>
    </div>
  );
};

export default TextEditor;

# Explicación Detallada

- **¿Qué hace este fragmento de código?**  
   Este fragmento de código define los estilos visuales para el editor de texto, específicamente para la estructura del contenedor, el área de texto y los botones de cambio de tema. El `.editor-container` establece el diseño del editor, haciendo uso de flexbox para centrar los elementos. La clase `.text-area` se aplica al área de texto, proporcionando un tamaño de fuente y bordes estilizados. Además, los botones dentro de `.theme-selector` permiten cambiar entre temas de color (claro, oscuro, sepia), con transiciones suaves al interactuar. Los temas cambian el fondo del editor y el área de texto, ofreciendo tres opciones: `light`, `dark` y `sepia`.

- **¿Cómo cumple con el requisito de la habilidad?**  
   Este código cumple con el requisito de la habilidad de cambiar el tema visual del editor de texto y personalizar su apariencia. La funcionalidad de cambiar entre tres temas (claro, oscuro y sepia) está soportada por las clases dinámicas (`light`, `dark`, `sepia`) aplicadas al contenedor del editor y al área de texto. Además, los botones permiten a los usuarios seleccionar un tema sin tener que recargar la página, lo que proporciona una experiencia fluida. Los estilos CSS se aplican de manera eficiente para permitir que el área de texto reaccione a los cambios de tema con transiciones suaves, mejorando la experiencia visual.

- **¿Por qué es la mejor forma de implementarlo?**  
   Este enfoque es ideal porque aprovecha las capacidades de CSS para manejar el diseño y los estilos de manera eficiente. Usar clases CSS para manejar los temas permite cambiar fácilmente la apariencia del editor sin necesidad de JavaScript adicional. La estructura basada en flexbox asegura que los elementos estén correctamente alineados y respondan de manera flexible al tamaño de la pantalla. Las transiciones suaves mejoran la experiencia de usuario, haciendo que el cambio entre temas se sienta fluido. Además, la separación de las reglas de estilo por tema (claro, oscuro, sepia) facilita el mantenimiento y la escalabilidad del proyecto, ya que se pueden agregar más temas o estilos sin modificar el código del editor en sí.

