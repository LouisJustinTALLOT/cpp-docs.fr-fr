---
title: '/module : référence (utilisez le module IFC)'
description: 'Utilisez l’option de compilateur/module : Reference pour créer des unités d’en-tête de module pour le nom d’en-tête ou les fichiers include spécifiés.'
ms.date: 09/13/2020
f1_keywords:
- /module:reference
helpviewer_keywords:
- /module:reference
- Use named module IFC
ms.openlocfilehash: 5f40f6b700c38f3238cc7a621313621085fbc289
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079088"
---
# <a name="modulereference-use-named-module-ifc"></a>`/module:reference` (Utilisez le module nommé IFC)

Indique au compilateur d’utiliser un IFC ( *`.ifc`* ) existant pour la compilation en cours.

## <a name="syntax"></a>Syntaxe

> **`/module:reference`** *`module-name=filename`*\
> **`/module:reference`** *`filename`*

### <a name="arguments"></a>Arguments

*`filename`*\
Nom d’un fichier qui contient des *données IFC*, informations de module prégénérées. Pour importer plusieurs modules, incluez une option distincte **`/module:reference`** pour chaque fichier.

*`module-name`*\
Nom valide d’un nom d’unité d’interface de module principal exporté ou d’un nom de partition de module complet.

## <a name="remarks"></a>Notes

L' **`/module:reference`** option de compilateur requiert l’activation de la prise en charge des modules expérimentaux à l’aide de l' [`/experimental:module`](experimental-module.md) option du compilateur, avec l’option [/std : c + + latest](std-specify-language-standard-version.md) . Cette option est disponible à partir de Visual Studio 2019 version 16,8.

Si l' **`/module:reference`** argument est un *`filename`* sans *`module-name`* , le fichier est ouvert au moment de l’exécution pour vérifier que l' *`filename`* argument nomme une importation spécifique. Cela peut entraîner une baisse des performances du runtime dans les scénarios qui ont de nombreux **`/module:reference`** arguments.

*`module-name`* Doit être un nom d’unité d’interface de module principal valide ou un nom de partition de module complet. Voici des exemples de noms d’interface de modules primaires :

- `M`
- `M.N.O`
- `MyModule`
- `my_module`

Voici quelques exemples de noms de partition de modules complets :

- `M:P`
- `M.N.O:P.Q`
- `MyModule:Algorithms`
- `my_module:algorithms`

Si une référence de module est créée à l’aide d’un *`module-name`* , les autres modules sur la ligne de commande ne sont pas recherchés si le compilateur rencontre une importation de ce nom. Par exemple, à partir de la ligne de commande suivante :

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m=n.ifc
```

Dans le cas ci-dessus, si le compilateur voit `import m;` alors *`m.ifc`* n’est pas recherché.

### <a name="examples"></a>Exemples

À partir de trois modules comme indiqué dans le tableau suivant :

| Module | Fichier IFC |
|--|--|
| *`M`* | *`m.ifc`* |
| *`M:Part1`* | *`m-part1.ifc`* |
| *`Core.Networking`* | *`Networking.ifc`* |

Les options de référence à l’aide d’un *`filename`* argument peuvent ressembler à ceci :

```cmd
cl ... /experimental:module /module:reference m.ifc /module:reference m-part.ifc /module:reference Networking.ifc
```

Les options de référence à l’aide de *`module-name=filename`* peuvent ressembler à ceci :

```cmd
cl ... /experimental:module /module:reference m=m.ifc /module:reference M:Part1=m-part.ifc /module:reference Core.Networking=Networking.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour ajouter l' *`/module:reference`* option et ses arguments. Ensuite, cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[`/experimental:module` (Activer la prise en charge des modules)](experimental-module.md)\
[`/headerUnit` (Utiliser l’unité d’en-tête IFC)](headerunit.md)\
[`/module:exportHeader` (Créer des unités d’en-tête)](module-exportheader.md)\
[`/translateInclude` (Traduire les directives include en directives Import)](translateinclude.md)
