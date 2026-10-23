# Aufbau eines Unit Test mit Testdouble für CDS und SQL<br>
<br>
**Unit Test anlegen<br>
Lege in der Beaviour-Klasse eine neue Testklasse an und mache sie zum Freund der Handler-Klasse<br>
Erzeuge mit den Templates einen Unit-Test für den Behaviour Pool<br>
und ordne sie über die Annotation "! @testing BDEF:ZR_XXINVENTORYSBS dem Behaviour Pool zu.<br>
<br>
**Deklarationen, Setup and Teardown in der Private Section<br>
Wir benötigen Testdouble-Frameworks für SQL und CDS und eine Dummy-Tabelle fürs Inventory<br>
Beachte die Abhängigkeiten zwischen CDS und SQL, diese werden wir direkt mittels CDS-TD lösen.<br>
    CLASS-DATA:<br>
    class_under_test     TYPE REF TO lhc_zr_xxinventorysbs,  <br>  
    cds_test_environment TYPE REF TO if_cds_test_environment,<br>
    inventory_mock type table of zxxinventorysbs<br>
Dazu die Methoden für Setup und Teardown<br>
    CLASS-METHODS:<br>
    class_setup, <br>
    class_teardown.<br>
    METHODS:<br>
    setup,    <br>
    teardown.<br>
    <br>
Lege die Methoden über den Quickfix an.<br>
<br>
Nutze cl_cds_test_environment=>create_for_multiple_cds im Class_Setup.<br>
Berücksichtige auch die Abhängigkeit zwischen den Frameworks beim SQL-TD mit ->enable_double_redirection( ).<br>
Im Setup werden doppelte Datensätze aus dem Framework mit ->clear_doubles( ) entfernt.<br>
Füge dann dort auch zwei Mock-Datensätze in die Inventory-ITAB hinzu und übergib dies an das CDS-TD mit ->insert_test_data.<br>
Ein Datensatz hat eine Inventory_ID = 10 und der andere ist ohne Inventory_ID.<br>
Teardown bekommt einen ROLLBACK ENTITIES.<br>
Class_Teardown zerstört die Environment mit ->destroy( ).<br>
<br>
**Testfall anlegen<br>
Lege zwei Testfälle an<br>
    METHODS:<br>
      test_id_for_create FOR TESTING RAISING cx_static_check,<br>
      test_create        FOR TESTING RAISING cx_static_check.<br>
Normalerweise würde man hier auch noch Update und Fehlerfälle prüfen. Wir belassen es beim Positivfall.<br>
<br>
Der Testfall test_create legt mittels EML einen neuen Datensatz an und liest ihn anschließend aus der Enität.<br>
Es sollten also 3 Datensätze vorhanden sein und kein Datensatz hat mehr eine initiale Inventory_ID.<br>
<br>
Der Testfall test_id_for_create testet direkt die Determination.
Prüfe zunächst in der Test-Methode mit Select auf die Entity ZR_XXINVENTORYSBS und Assert, ob der Mock-Datensatz gefunden werden kann.<br>
Setze hier auch einen Break-Point und prüfe im Debugger, dass die Originaltabelle diesen Datensatz nicht beinhaltet.<br>
Rufe dann in der CUT die Methode newinventoryid auf und führe im TD den Commit mittels Commit Entities aus.<br>
Übergebe dazu der CUT-Methode das Mock-Inventory für die Schlüssel.<br>
Prüfe, ob jetzt alle Datensätze eine Inventory_ID bekommen haben.<br>













