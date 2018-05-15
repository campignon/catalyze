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

### Créer un exporteur personnalisé

La deuxième étape après l'intégration des deux fichiers cités précédemment est de créer un exporteur personnalisé dans lequel sera défini les champs qui apparaîtront dans le fichier final ainsi que leur contenu.

Par exemple, imaginons que l'on souhaite exporter la liste des utilisateurs de l'application au format CSV. On créé alors une classe `UserCsvExporter` qui hérite de la classe abstraite `AbsCsvExporter` et on implémente la méthode abstraite `getLine` qui définit les champs que l'on retrouvera dans le fichier CSV.

Voici un exemple de ce à quoi pourrait ressembler l'exporteur :

```java
package <basepackage>.web.rest.util.csv;

import java.util.ArrayList;
import java.util.List;

import <basepackage>.domain.User;

public class UserCsvExporter extends AbsCsvExporter<User> {

	@Override
	public List<String> getLine(User user) {
		List<String> fields = new ArrayList<>();
		fields.add(String.valueOf(user.getId()));
		fields.add(user.getFirstName());
		fields.add(user.getLastName());
		fields.add(user.getEmail());
		return fields;
	}

}
```

Dans l'exemple ci-dessus, le fichier CSV final contiendra pour chaque utilisateur 4 champs : l'id de l'utilisateur, son prénom, son nom et son e-mail.

On a donc quelque chose qui ressemble à ceci :

```
1,System,System,system@localhost
2,Anonymous,User,anonymous@localhost
3,Administrator,Administrator,admin@localhost
4,User,User,user@localhost

```

### Créer un point d'entrée dans l'API pour télécharger le fichier CSV