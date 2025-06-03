# S2.03.MongoDB.Lv1.Ex2

Aquest projecte implementa un model de dades orientat a documents per gestionar la informació d’una òptica fictícia anomenada “Cul d’Ampolla”, utilitzant MongoDB. El focus d’aquest model està centrat en les ulleres com a producte, incloent informació rellevant de cada unitat venuda, el proveïdor, el client comprador i l’empleat responsable de la venda.

### 📚 Resum del Projecte
Aquest model permet a l'òptica controlar de forma eficient:

Les característiques de les ulleres venudes

Els proveïdors associats a cada model d’ulleres

Els clients compradors

L’empleat o empleada que ha realitzat la venda

La data i hora de la venda

### 📂 Estructura del Model – Ulleres com a Centre del Disseny
Cada document a la col·lecció representa unes ulleres venudes i inclou totes les dades rellevants per a la seva traçabilitat i gestió:

```
{
  "marca": "Oakley",
  "graduacio_vidre_esquerre": 2.0,
  "graduacio_vidre_dret": 1.75,
  "tipus_muntura": "pasta",
  "color_muntura": "blau",
  "color_vidre_esquerre": "gris",
  "color_vidre_dret": "gris",
  "preu": 159.99,
  "proveidor": {
    "nom": "Òptics del Vallès",
    "telefon": "938765432",
    "fax": "938765433",
    "nif": "B98765432",
    "adreça": {
      "carrer": "C. Nou",
      "numero": "15",
      "pis": "Baixos",
      "porta": "",
      "ciutat": "Terrassa",
      "codi_postal": "08221",
      "pais": "Espanya"
    }
  },
  "client_comprador": {
    "id": "cli078",
    "nom": "Arnau Pujol",
    "adreça": "Carrer del Sol, 27, 1r 2a, Terrassa, 08221, Espanya",
    "telefon": "611223344",
    "email": "arnau@example.com",
    "data_registre": "2023-11-22T00:00:00Z",
    "recomanat_per": "cli045"
  },
  "empleat_venda": {
    "id": "emp007",
    "nom": "Sara Martínez"
  },
  "data_venda": "2024-03-01T16:45:00Z"
}
```

### 🔍 Objectius del Model
Aquest model és ideal per a:

Fer anàlisi de vendes per producte o marca

Controlar informació de proveïdors detallada

Consultar estadístiques de vendes per empleat

Fer seguiment del perfil de client comprador

Auditar vendes segons data i hora

### 🧪 Consultes d’Exemple (MongoDB)
🔸 Totes les ulleres venudes per un empleat concret:

```
db.ulleres.find({ "empleat_venda.nom": "Sara Martínez" })
```

🔸 Ulleres venudes d’una marca específica:

```
db.ulleres.find({ "marca": "Ray-Ban" })
```

🔸 Proveïdors amb informació de contacte i NIF:

```
db.ulleres.aggregate([
  {
    $group: {
      _id: "$proveidor.nif",
      nom: { $first: "$proveidor.nom" },
      telefon: { $first: "$proveidor.telefon" },
      fax: { $first: "$proveidor.fax" },
      adreça: { $first: "$proveidor.adreça" }
    }
  }
])
```

### 🛠️ Eines Utilitzades
MongoDB – Base de dades NoSQL per a l’emmagatzematge de documents

MongoDB Compass – Visualització de col·leccions i execució de consultes

JSON Schema – Definició de l’estructura dels documents

Visual Studio Code / Studio 3T – Entorns de desenvolupament

### 🔗 GitHub Repository
📂 https://github.com/ArnauAsole/S2.03.MongoDB.Lv1.Ex2.git
