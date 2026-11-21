# PeerFlow-AI-3.4
Entrega 3.4
### PeerFlow AI-V2F.json
Es la versión final del prototipo de flujo de trabajo propuesto en n8n.
### PeerFlow
AI-v1 es la primera versión, antes de detectar errores y corregirlos.

### PeerFlow_AI_Registro_de_errores.json

Flujo auxiliar de manejo de errores de PeerFlow AI. Se activa automáticamente
cuando cualquier nodo del flujo principal falla en una ejecución de producción
(chat público). Registra la falla y avisa al editor para que intervenga.

**Nodos:**
1. **Error en PeerFlow AI** (Error Trigger): recibe los datos de la ejecución fallida.
2. **Preparar registro de error**: extrae fecha, flujo, nodo que falló, mensaje de error e ID de ejecución.
3. **Registrar error** (Google Sheets): agrega una fila en la pestaña *Errores*.
4. **Avisar al editor** (Gmail): envía un correo con el nodo, el error y la ejecución, para intervención humana.

**Cómo se conecta:** en el flujo principal, *Settings → Error Workflow →
PeerFlow AI – Registro de errores*. Requiere credenciales propias de Google Sheets y Gmail.

**Limitación:** n8n solo lo activa en ejecuciones de producción, no en las
pruebas del editor. Las fallas de OpenAlex se registran además dentro del flujo
principal (nodo *¿Falló OpenAlex?*), lo que funciona también en pruebas.
