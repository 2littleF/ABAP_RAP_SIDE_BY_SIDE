# Paket und Tabelle anlegen, RAP aus Tabelle generieren

## Paket anlegen

Lege das Paket ZXXRAPSIDEBYSIDE als Unterpaket in den lokalen Objekten an

## Tabelle anlegen
Lege die Tabelle ZXXINVENTORYSBS im Paket an

## Generate ABAP Repository Objects
Nutze den Generator um das Framework einer RAP-Anwendung für die Inventory-Tabelle zu erzeugen

<details><summary>Generator</summary><img width="1492" height="1139" alt="image" src="https://github.com/user-attachments/assets/f1db3ec7-ec70-40e9-88c2-35dbce5d4e2e" /></details>

Die allgemeinen Prefix und Suffix können leer bleiben, außer auf dem System sind die Namen bereits vergeben.
Gib dem CDS den Alias Inventory.
Prüfe die restlichen Vorschläge für das Business Object, ob sie so in Ordnung sind.

<details><summary>Generator Zusammenfassung</summary><img width="1267" height="1493" alt="image" src="https://github.com/user-attachments/assets/210df0b9-b5c2-4575-aa02-88a18aa26c04" /></details>

Füge in die CDS einen semantischen Schlüssel für InventoryID dazu

## Preview
Publishing des Services Bindings.<br>
Teste die APP mit der Anlage eines Datensatzes.<br>
Gültige Produkt-IDs oder vorhandene Mengen aus dem S/4 System sind (noch) nicht bekannt.<br>
<br>
<br>
## Business Object Type pflegen
Unser Business Object Type wurde zwar richtig als Business Objekt angelegt. Es fehlt aber ein Code.<br>
<details><summary>Object Type Code</summary><img width="1528" height="353" alt="image" src="https://github.com/user-attachments/assets/c5b05401-304b-41ee-825c-f4be67b9404a" /></details><br>
Lege einen Code für das Object fest. Prüfe es im Relation Explorer.<br>



