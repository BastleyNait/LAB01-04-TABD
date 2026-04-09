## 🎓 Sistema de Recomendación de Cursos - EPIS

Este proyecto implementa un **Sistema de Recomendación de Cursos** utilizando una base de datos vectorial (**ChromaDB**) para realizar búsquedas semánticas basadas en intereses, habilidades y perfiles académicos.

## 📝 Información del Proyecto
- **Laboratorio:** LAB 01 - Bases de Datos Vectoriales
- **Ejercicio:** Proyecto Integrador
- **Docente:** Mg. Antonio Arroyo Paz
- **Estudiante:** Chirinos Negron Sebastian Arley

## 🚀 Funcionalidades
1.  **Recomendación por Intereses:** Filtra cursos por afinidad semántica y semestre específico.
2.  **Búsqueda de Similitud:** Encuentra cursos con contenidos temáticos similares a uno dado.
3.  **Búsqueda por Perfil:** Recomienda cursos basados en una lista de habilidades técnicas o blandas.
4.  **Persistencia:** Los datos se almacenan localmente en `./cursos_epis_db` usando el motor persistente de ChromaDB.

## 🛠️ Tecnologías Utilizadas
- **Python 3.x**
- **ChromaDB:** Base de datos vectorial para el almacenamiento y recuperación de embeddings.
- **Sentence-Transformers:** Generación de embeddings vectoriales a partir de descripciones de texto.

## 📋 Estructura de Datos
Cada curso en el sistema cuenta con los siguientes metadatos:
- Nombre del curso, Descripción, Créditos, Semestre (I al X), Área, Prerrequisitos.

## ⚙️ Instrucciones de Ejecución
El sistema está diseñado para manejar la persistencia automáticamente:
1. **Primera ejecución:** El script detecta que la base de datos no existe, crea la colección e inserta los 20 cursos base.
2. **Ejecuciones posteriores:** El script reconoce la carpeta `./cursos_epis_db` y carga los datos existentes sin duplicarlos.

## 🔍 Análisis de Limitaciones y Mejoras

### Limitaciones Observadas
- **Dependencia de Embeddings Genéricos:** El modelo `all-MiniLM-L6-v2` es excelente pero general; podría no captar tecnicismos muy específicos de la malla curricular local sin un ajuste fino.
- **Filtros Estrictos:** El filtrado por semestre es exacto (`$eq`), lo que impide recomendar cursos de semestres adyacentes que podrían interesar al alumno.
- **Interfaz Limitada:** La interacción actual es por consola, lo que dificulta la visualización de grandes volúmenes de datos.

### Posibles Mejoras
- **Búsqueda Híbrida:** Combinar la búsqueda vectorial con filtros de palabras clave (BM25) para mejorar la precisión en nombres de cursos específicos.
- **Sistema de Feedback:** Permitir que el usuario califique la recomendación para ajustar los pesos de los vectores en el tiempo.
- **Interfaz Web:** Implementar un frontend con Streamlit o Flask para una experiencia de usuario más intuitiva.