[Zurück](../README.md)
# Einrichten von Documents-ext
Mit Pre- und PostResources im Tomcat lassen sich externe Ressourcen einbinden. Dies ist eine Vorraussetzung für Konzepte wie etwa GenTable oder UserExits.

## 1. documents.xml
Die Datei `documents.xml` muss - je nach Tomcat-Version - im conf-Verzeichnis abgelegt werden.

* **Tomcat 8.x:** `{documents-install-dir}\tomcat{8}\conf\Documents\localhost`  
* **Tomcat 9.x:** `{documents-install-dir}\tomcat9\conf\Catalina\localhost`

Eine exemplarische Konfiguration ist im [example-Ordner](./example/tomcat/documents.xml) zu finden; weiterführende Hinweise finden sich in der [Apache Tomcat Referenz](https://tomcat.apache.org/tomcat-9.0-doc/config/resources.html).

Anschließend muss der Documents Tomcat Dienst neu gestartet werden. Die Ressourcen werden als DirResourceSet eingebunden. Das bedeutet, dass Änderungen innerhalb dieser Verzeichnisse nicht von einem Neustart begleitet werden müssen; auch ein Aus- und wieder einloggen des Benutzers ist nicht notwendig. Ein Neuladen der Seite - mit eventuellem leeren des Caches - ist ausreichend.

## 2. Externe Ressourcen einbinden
Um beispielsweise zusätzliche Javascript- oder CSS-Dateien in das Frontend einzubinden, müssen diese in einer `script.jsp` im Verzeichnis `{path-to-documents-ext}\jsp` entsprechend verlinkt sein.  
Hierzu sind die Dokumentationen der [script-](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script) und [link-Elemente](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link) hilfreich.  
Auch Inline-Code ist möglich. Alle Elemente, die im head-Element des HTML-Dokuments Wirkung zeigen können hier angewendet werden.

Eine beispielhafte `script.jsp` ist im [example-Ordner](./example/documents-ext/jsp/script.jsp) zu finden.