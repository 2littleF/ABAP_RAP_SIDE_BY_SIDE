# Metadaten anpassen und Managed Szenario einführen<br>
<br>
** Änderung der Felder<br>
Aktuell sind noch alle Felder eingabebereit und es wird keine Inventory-ID automatisch vergeben. <br>
<br>
- Füge eine neue Determination NewInventoryID beim Speichern im Create-Vorgang ein und füge sie per Quickfix zum Pool dazu.<br>
- Lese im Pool die Entität mit den übergebenen Schlüssel per EML und entferne alle Datensätze aus der Liste, die bereits eine ID haben.<br>
- Selektiere die maximale ID aus der Tabelle und zähle per Update die ID hoch in der Entität.<br>
<br>


