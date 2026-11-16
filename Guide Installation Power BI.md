# Avant de commencer : connecter Power BI à vos fichiers Excel

Le fichier Power BI utilise un paramètre Power Query nommé **`SourceFolder`**
pour localiser les fichiers Excel. Le chemin enregistré correspond à un autre
ordinateur : après le téléchargement, vous devez le remplacer par le chemin
du dossier contenant les fichiers Excel sur **votre ordinateur**.

## 1. Préparez les fichiers sur votre ordinateur

Téléchargez le fichier Power BI et le dossier **Excel_Sources**.
Si les fichiers sont dans une archive ZIP, extrayez-la avant de commencer.

Le dossier Excel_Sources doit contenir les cinq fichiers suivants, sans les renommer :

- Customers.xlsx
- Products.xlsx
- Sales.xlsx
- Stores.xlsx
- Targets.xlsx

Dans l’Explorateur de fichiers Windows, ouvrez ce dossier, puis cliquez dans
la barre d’adresse pour copier son chemin complet.

Exemple de chemin à adapter à votre ordinateur :

```text
C:\Users\VotreNom\Documents\Mission_Contoso\Excel_Sources
```

**Copiez le chemin du dossier contenant directement les cinq fichiers Excel,
pas celui d’un fichier Excel ni celui du dossier parent.**

## 2. Modifiez le paramètre dans Power BI Desktop

1. Ouvrez le fichier Power BI (.pbix) dans **Power BI Desktop**.
2. Dans l’onglet **Accueil**, cliquez sur **Transformer les données** pour ouvrir l’éditeur Power Query.
3. Dans l’éditeur, ouvrez **Accueil > Gérer les paramètres**.
4. Sélectionnez le paramètre **`SourceFolder`**.
5. Remplacez sa **Valeur actuelle** par le chemin copié à l’étape précédente, **sans guillemets et sans barre oblique inverse (`\`) à la fin**.
6. Validez avec **OK**, puis cliquez sur **Fermer et appliquer**.

Il n’est pas nécessaire de modifier séparément les sources des cinq tables :
elles utilisent toutes ce même paramètre.

## 3. Actualisez et enregistrez

Dans Power BI Desktop, cliquez sur **Accueil > Actualiser** et attendez la fin
du chargement. Vérifiez qu’aucune erreur de source n’apparaît, puis
**enregistrez votre fichier Power BI** pour conserver le nouveau chemin.

## Si un message indique qu’un fichier est introuvable

Vérifiez que la valeur de `SourceFolder` correspond bien au dossier sur votre
ordinateur, que les cinq fichiers Excel s’y trouvent et que leurs noms
n’ont pas été modifiés.

Si une erreur apparaît dès l’ouverture ou dans Power Query, configurez
d’abord le paramètre comme indiqué ci-dessus, puis relancez l’actualisation.

**Si vous déplacez le dossier Excel_Sources ou changez d’ordinateur,
vous devrez à nouveau mettre à jour `SourceFolder`.**
