## Exporter des données au format CSV
 
### Ajouter les fichiers *CsvExporter.java* et *AbsCsvExporter.java*

Ces deux fichiers sont des fichiers utilitaires qui contiennent une grosse partie de la logique nécessaire à un export au format CSV. Ils vont permettre d'écrire les données dans la réponse HTTP. 

Pour les utiliser, se placer dans le package **web.rest.util**. 

Créer un package **csv**. A l'intérieur de ce nouveau package, créer une interface *CsvExporter.java* et remplacer le code auto-généré par le suivant :

```java
package <basepackage>.web.rest.util.csv;

import java.io.IOException;
import java.io.Writer;
import java.util.List;

public interface CsvExporter<T> {

	List<String> getLine(T object);
	
	void setHeaders(List<String> headers);
	
	void setModel(List<T> model);
	
	void setSeparator(char separator);
	
	void write(Writer writer) throws IOException;
	
}

```

Créer ensuite une nouvelle classe abstraite *AbsCsvExporter.java*. Lui donner comme contenu :

```java
package <basepackage>.web.rest.util.csv;
import java.io.IOException;
import java.io.Writer;
import java.util.List;

public abstract class AbsCsvExporter<T> implements CsvExporter<T> {
	
	private static final char DEFAULT_SEPARATOR = ',';
	
	private List<String> headers;
	private List<T> model;
	private char separator;
	
	public AbsCsvExporter() {
		this.headers = null;
		this.model = null;
		this.separator = DEFAULT_SEPARATOR;
	}
	
	@Override
	public void setHeaders(List<String> headers) {
		this.headers = headers;
	}
	
	@Override
	public void setModel(List<T> model) {
		this.model = model;
	}
	
	@Override
	public void setSeparator(char separator) {
		this.separator = separator;
	}
	
	@Override
	public void write(Writer writer) throws IOException {
		if (headers != null) {
			writeLine(writer, headers);
		}
		if (model != null) {
			for (T item : model) {
				List<String> fields = getLine(item);
				writeLine(writer, fields);
			}
		}
		writer.close();
	}

	@Override
	public abstract List<String> getLine(T object);
	
	private void writeLine(Writer writer, List<String> fields) throws IOException {
		StringBuilder sb = new StringBuilder();
		boolean first = true;
		for (String field : fields) {
			if (!first) {
				sb.append(separator);
			}
			sb.append(field);
			if (first) {
				first = false;
			}
		}
		sb.append("\n");
		writer.append(sb.toString());
	}

}

```