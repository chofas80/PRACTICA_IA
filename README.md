# Planificador de Menús Personalizado con IA (RAG)

## Descripción del Proyecto

Este proyecto es una herramienta inteligente diseñada para generar planes alimenticios personalizados, especialmente para mujeres con resistencia a la insulina. 

Surge por la necesidad de obtener nuevas ideas para evita comer siempre lo mismo y "pecar" en alimentos prohibidos pero muy antojables. 

El objetivo es proporcionar menús adaptados a necesidades específicas como: el propósito del plan, la duración, el número de porciones y/o la exclusión de alimentos por el usuario (sea por alergias o por desagrado). 

La salida es un plan detallado con recetas, ingredientes, instrucciones e información nutricional. Para facilidad del usuario dicho plan se puede exportar a formatos PDF y/o HTML.

Utiliza un enfoque de RAG combinando información local (PDFs de menús preexistentes) y con conocimiento externo (búsquedas en DuckDuckGo y Arxiv).

### Requisitos Previos

* Una clave API de OpenAI.
* Dentro de la carpeta `./data` existen 3 documentos con menús semanales, puedes agregar más si lo deseas. Deben ser en formato PDF.

### Estructura de archivos

        ```
        .
        ├── data/
        │   └── tu_menu_1.pdf
        │   └── tu_menu_2.pdf
        │   └── ...
        ├── faiss_index/ (sino existe, se creará automáticamente)
        ├── rag_sofia_gabian.ipynb
        └── requirements.txt
        ```

### Pasos a seguir
        
1.  **Ejecuta las celdas de instalación y reinicia:**
    * Ejecuta las primeras celdas del notebook que contiene los comandos de instalación (`!sudo apt-get`, `!pip install -r requirements.txt`).
    * **IMPORTANTE:** Después de que la celda de instalación termine, necesitas Reiniciar Sesión.
2.  **Ingresa tu API Key:**
3.  **Ejecuta el resto del código:** 
4.  **Interactúa con el planificador:** La función `main()` te guiará a través de las preguntas para generar tu plan.

### Ejemplo de Interacción

    ```
        --- ¡Generador de Plan Alimenticio Personalizado! ---
        📝 Selecciona el propósito de tu plan alimenticio:
         1.  Resistencia a la insulina
         2.  Pérdida de peso
         3.  Ganancia muscular
         4.  Dieta equilibrada
         5.  Control de glucosa
         6.  Reducción de inflamación
          Introduce el número de tu elección (1-6): 1
          📅 ¿De cuántos días quieres tu plan? (1-7 días): 3
          🚫 ¿Hay algún alimento que quieras descartar del plan? Indícalos separándos por comas (ejemplo: 'lácteos, gluten, fruta') o simplemente presiona 'enter': lácteos, gluten
          👨‍👩‍👧‍👦 ¿Para cuántas porciones deseas las recetas receta? (1, 2, 3): 2

          Generando plan personalizdo para 'Resistencia a la insulina' de 3 días, descartando: lácteos, gluten, para 2 porción(es)
          ⏳ Esto puede tomar un momento.
        ```    

        
### Ejemplo de Salida

```
📄 Respuesta generada:

# Plan Alimenticio Personalizado

## Día 1

### Desayuno: Huevos Revueltos con Aguacate y Tomate Cherry
- **Ingredientes**:
  - 2 huevos
  - 5ml de aceite de oliva
  - 40g de aguacate
  - 70g de tomates cherry
  - Sal y pimienta al gusto
- **Instrucciones**:
  1. Bate los huevos con sal y pimienta.
  2. Cocina los huevos revueltos en una sartén con el aceite de oliva.
  3. Sirve con el aguacate en rodajas y los tomates cherry cortados por la mitad.
- **Información Nutricional**:
  - Calorías: 273kcal
  - Proteínas: 13.4g
  - Carbohidratos: 7.5g
  - Grasas: 20.7g
- **Número de porciones**: 1

### Snack de Media Mañana: Batido de Proteína con Leche Vegetal
- **Ingredientes**:
  - 1 scoop de proteína en polvo (sin azúcares añadidos)
  - 200ml de leche vegetal sin azúcar (almendra, soja o avena)
- **Instrucciones**:
  1. Mezcla la proteína en polvo con la leche vegetal en una licuadora.
  2. Bate hasta obtener una mezcla homogénea.
- **Información Nutricional**:
  - Calorías: 256kcal
  - Proteínas: 16.3g
  - Carbohidratos: 12.4g
  - Grasas: 15.32g
- **Número de porciones**: 1

### Comida: Ensalada de Pollo y Quinoa
- **Ingredientes**:
  - 100g de pechuga de pollo
  - 50g de quinoa cocida
  - 50g de espinacas frescas
  - 30g de pimiento rojo
  - 10ml de aceite de oliva
  - Jugo de medio limón
  - Sal y pimienta al gusto
- **Instrucciones**:
  1. Cocina la pechuga de pollo a la plancha y córtala en tiras.
  2. Mezcla la quinoa con las espinacas, el pimiento rojo picado y el pollo.
  3. Aliña con el aceite de oliva, el jugo de limón, sal y pimienta.
- **Información Nutricional**:
  - Calorías: 420kcal
  - Proteínas: 35g
  - Carbohidratos: 30g
  - Grasas: 18g
- **Número de porciones**: 1

### Snack de la Tarde: Yogur Griego con Almendras
- **Ingredientes**:
  - 150g de yogur griego natural
  - 15g de almendras
- **Instrucciones**:
  1. Sirve el yogur griego en un bol.
  2. Añade las almendras por encima.
- **Información Nutricional**:
  - Calorías: 200kcal
  - Proteínas: 15g
  - Carbohidratos: 10g
  - Grasas: 12g
- **Número de porciones**: 1

### Cena: Tacos de Lechuga con Pollo
- **Ingredientes**:
  - 100g de pechuga de pollo
  - 2 hojas grandes de lechuga
  - 30g de cebolla
  - 30g de tomate
  - 10g de queso rallado bajo en grasa
  - 5ml de aceite de oliva
  - Sal y pimienta al gusto
- **Instrucciones**:
  1. Cocina el pollo en una sartén con el aceite de oliva, sal y pimienta.
  2. Corta la cebolla y el tomate en cubos pequeños.
  3. Rellena las hojas de lechuga con el pollo, la cebolla, el tomate y el queso.
- **Información Nutricional**:
  - Calorías: 310kcal
  - Proteínas: 32g
  - Carbohidratos: 8g
  - Grasas: 18g
- **Número de porciones**: 1

 ```  

### Ejemplo de Interacción para la Exportación

```
       ¿En qué formatos te gustaría descargar tu plan alimenticio?
       ¿Exportar a PDF? (s/n): s
       ¿Exportar a HTML? (s/n): s
```  

Si respondes 's' a ambas, se generarán dos archivos en la misma carpeta que tu notebook (o en el entorno de Colab):

* `plan_alimenticio_YYYYMMDD_HHMMSS.pdf`
* `plan_alimenticio_YYYYMMDD_HHMMSS.html`
