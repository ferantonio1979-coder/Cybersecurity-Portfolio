Fase de Post-Explotación
Tras obtener acceso inicial al sistema a través del panel de comandos, el principal desafío técnico fue la restricción de comandos de lectura estándar (cat, less, head, tail), los cuales estaban inhabilitados como medida de seguridad.

Para superar estas limitaciones y proceder con la enumeración de archivos y la extracción de los ingredientes, se implementaron las siguientes técnicas de evasión de filtros:

Enumeración mediante ls -la: Se realizó un reconocimiento exhaustivo de los directorios del usuario y del directorio /root/, identificando archivos críticos como 3rd.txt.

Técnicas de Lectura Alternativa: Ante la imposibilidad de usar comandos de visualización directa, se emplearon métodos de procesamiento de flujo y redirección:

Uso de grep: Se utilizó grep . [archivo] para forzar la salida del contenido mediante la búsqueda de patrones de caracteres.

Redirecciones de Entrada (<): Se empleó la redirección con comandos como sort < [archivo] para evadir el filtro de comandos, permitiendo que el contenido del archivo fuera procesado por sort en lugar de ser leído directamente por una herramienta restringida.

Encadenamiento de comandos (pipe |): Se utilizó la tubería junto a tr (ej. cat | tr) para transformar y visualizar el contenido, logrando bypasses efectivos en las reglas de filtrado del sistema.

Uso de base64: Se empleó la codificación de archivos (base64 [archivo]) para convertir el contenido en texto plano codificado, evitando así las restricciones de comandos de lectura de texto.

Lecciones aprendidas:
Este ejercicio demostró que un atacante no debe limitarse a los comandos habituales. La capacidad de entender cómo Linux gestiona los flujos de datos (stdin, stdout) es fundamental para navegar por entornos altamente restringidos o con seguridad reforzada.
