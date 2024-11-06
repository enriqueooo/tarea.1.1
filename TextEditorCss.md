# Proyecto: Editor de Texto

Este proyecto es un editor de texto implementado en React, con capacidades de manejo de texto en tiempo real y personalización visual.

## Habilidades y Requerimientos Implementados

### Habilidad 1: Estilización Visual del Editor con Cambios de Tema y Formato

#### Descripción de la Habilidad
Aplicar estilos CSS al editor de texto para controlar la apariencia del área de texto, los botones de formato y el tema general (claro, oscuro y sepia). Los usuarios deben poder cambiar el color del texto, aplicar negrita, cursiva, subrayado, y cambiar el tamaño y tipo de letra.

#### Código de Implementación

```css
.editor-container {
  max-width: 800px;
  margin: 0 auto;
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.text-area {
  width: 100%;
  height: 200px;
  border: 2px solid #ccc;
  border-radius: 5px;
  padding: 10px;
  font-size: 16px;
  transition: border-color 0.3s ease;
}

.text-area:focus {
  border-color: #007bff;
  outline: none;
}

.theme-selector {
  margin-bottom: 20px;
  font-size: 16px;
}

.color-picker {
  margin-top: 10px;
  display: flex;
  gap: 10px; /* Espaciado entre botones de color */
  justify-content: center; /* Centra los botones de color */
}

.color-button {
  width: 30px;
  height: 30px;
  border: none;
  border-radius: 50%;
  margin: 0 5px;
  cursor: pointer;
  transition: transform 0.2s;
}

.color-button:hover {
  transform: scale(1.1);
}

.format-buttons {
  margin-top: 10px;
  display: flex; /* Flexbox para alinear botones */
  justify-content: center; /* Centra los botones de formato */
  gap: 10px; /* Espaciado entre botones */
}

.format-button {
  padding: 8px 16px;
  border: none;
  border-radius: 8px;
  background: linear-gradient(135deg, #6a11cb, #2575fc); /* Degradado */
  color: white;
  font-weight: bold;
  font-size: 14px;
  cursor: pointer;
  transition: all 0.3s ease; /* Transición suave */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.format-button:hover {
  background: linear-gradient(135deg, #8e44ad, #3498db); /* Cambia el degradado al hacer hover */
  transform: translateY(-3px); /* Eleva el botón al hacer hover */
  box-shadow: 0 8px 15px rgba(0, 0, 0, 0.2); /* Sombra más grande */
}

.format-button:active {
  transform: translateY(1px); /* Efecto de clic */
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1); /* Menor sombra al hacer clic */
}

.preview {
  margin-top: 20px;
  padding: 15px;
  border-radius: 5px;
  background-color: #f9f9f9;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.editor-container.light {
  background-color: #ffffff;
}

.editor-container.dark {
  background-color: #2e2e2e;
  color: white;
}

.editor-container.sepia {
  background-color: #f4ecd8;
  color: #3b2e25;
}

.text-editor {
  padding: 20px;
  border-radius: 8px;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
  background-image: url(data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAkGBxISEhUSEhIVFRUVFRUVFRUVFRUSFRUVFRUWFhUVFRUYHSggGBolHRUVITEhJSkrLi4uFx8zODMsNygtLisBCgoKDg0OFRAQFS0dFxkrLS0tKy0rLS0rLS0tLS0tLS0rKy0tLS0tLS0tLS0rLS0tLS0tKy03Ny0tLS0rNzctLf/AABEIALcBEwMBIgACEQEDEQH/xAAaAAADAQEBAQAAAAAAAAAAAAAAAQIDBAUH/8QALBABAQACAQIEBAYDAQAAAAAAAAECEQMSUSExQWEEE3HwgZGhscHRUuHxMv/EABgBAQEBAQEAAAAAAAAAAAAAAAABAgMF/8QAHxEBAQEBAAIDAQEBAAAAAAAAAAERAhIhMUFRA2Ei/9oADAMBAAIRAxEAPwD6lIaYdrbzlyntnMjg1qjkT1HEG0G0wxs9DUBUD6ofVGdxqdUTWpIlXAA2eh0ijYGj0A2R6MVPSejtKgnJNirEXEZpbPGbExa8eASaica5i1mI2N+LK42n8lfXPcvmTsGQpwn8r78VfNL5v0F/5F43Ny4a/wCOjLn+jO80vYZ68XP9+ptbyYmMZP1GOG/RrOCeq9lc5BucyH0SejPKQZclqdBbPodKoWioij0iLlBOgvQ0LhSK6U2CbA7iJiD6RT0NFCuQGCkpWCC0tluibE04qQYNpNDUiOgXA+vsMRr0UwPpGWWkdf36Ceou4+6eiDHkl8j8g9USHcfaHB1eguM8sL2xKYZdsW24Plz0E8XPy4X/ABjCz2sdnLL6MZaMdc+3PoNesKxisstgi2jS4ciJk0xFg6T6VyDpGsZ9IqqkSiVUqZACwUouQ0YsqOtUtE0WF1Cy05iCeoo0mJ9IZUHCyxZ5ctgm46IWdYXl/NXzBfKKucOe/h7IxuvejPl0Jv606fw/lNxm/wCPSe7m5PiKwyyvdcZv9J+O/Lkx9vwHzZ3eVvs04zGJ/W36ejjn4+CssnPw1qjpL6G23HyMdCUWXG/IxsF5O69i/LPpCrQJjnqbR6qVzXxxrjGcXjUbjUbRsuob1dRouteNncT5LQ6ls8wvoqmmcGSkkaTMrB0DUXKtkdlGpVWDaZn3WCMnPXRnIyyn/PUY6Z6OeArPKDAz5OzKr6RpWLtRophtrMWkxNPFz/LVON0DE1qcwuPFroYw0dJExXy6D2LkLLjnui5aaTXf9NiYT/L9Az8YXP3DonDj/lQJ4VzzA8cCl8KvEZkPQitFYNYVqLDpwRllanqdG0ZYQZsTOS9xcyuEPGB7PqacOXmMJPb8m2GhvmCYnYeyo6FRMitRchNXZE5bisMVXUDGGWX4e/8AUR1a9y58vp+7HQ5dde20z9h9WU20nH3E3SthSNLgV8PUML77C/fgUvaGBWqxqKueARrKTPi3/bbQ3PY0YKilSxO4iQRcA2Btz5T0XgnQg5NZU5UorQ1qQdTjdiApKuYqkDGXivXt+p2eLXGDUiMMWlioBucpGj0YqMsS6Wuj0GIxxZ/E43TXOX0RnyTysEuZjj1eyph9+Lo0Uncc/BlONfy6vqkReUXJCvH3t/YtSeURlzz6/Rl8/fl4DF6jbLJMlvkjCXvHZw4+H/oOZ5MMeJphxd3TcPv7rK3fgOnhIV15RXSrHDQuI1jKwpb2a3BF

### Explicación Detallada

- **¿Qué hace este fragmento de código?**  
   Este fragmento de código define los estilos visuales para el editor de texto, específicamente para la estructura del contenedor, el área de texto y los botones de cambio de tema. El `.editor-container` establece el diseño del editor, haciendo uso de flexbox para centrar los elementos. La clase `.text-area` se aplica al área de texto, proporcionando un tamaño de fuente y bordes estilizados. Además, los botones dentro de `.theme-selector` permiten cambiar entre temas de color (claro, oscuro, sepia), con transiciones suaves al interactuar. Los temas cambian el fondo del editor y el área de texto, ofreciendo tres opciones: `light`, `dark` y `sepia`.

- **¿Cómo cumple con el requisito de la habilidad?**  
   Este código cumple con el requisito de la habilidad de cambiar el tema visual del editor de texto y personalizar su apariencia. La funcionalidad de cambiar entre tres temas (claro, oscuro y sepia) está soportada por las clases dinámicas (`light`, `dark`, `sepia`) aplicadas al contenedor del editor y al área de texto. Además, los botones permiten a los usuarios seleccionar un tema sin tener que recargar la página, lo que proporciona una experiencia fluida. Los estilos CSS se aplican de manera eficiente para permitir que el área de texto reaccione a los cambios de tema con transiciones suaves, mejorando la experiencia visual.

- **¿Por qué es la mejor forma de implementarlo?**  
   Este enfoque es ideal porque aprovecha las capacidades de CSS para manejar el diseño y los estilos de manera eficiente. Usar clases CSS para manejar los temas permite cambiar fácilmente la apariencia del editor sin necesidad de JavaScript adicional. La estructura basada en flexbox asegura que los elementos estén correctamente alineados y respondan de manera flexible al tamaño de la pantalla. Las transiciones suaves mejoran la experiencia de usuario, haciendo que el cambio entre temas se sienta fluido. Además, la separación de las reglas de estilo por tema (claro, oscuro, sepia) facilita el mantenimiento y la escalabilidad del proyecto, ya que se pueden agregar más temas o estilos sin modificar el código del editor en sí.
