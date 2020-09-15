---
title: /headerUnit (utiliser l’unité d’en-tête IFC)
description: Utilisez l’option du compilateur/headerUnit pour spécifier une unité d’en-tête IFC existante à importer dans la compilation actuelle.
ms.date: 09/13/2020
f1_keywords:
- /headerUnit
helpviewer_keywords:
- /headerUnit
- Use header unit IFC
ms.openlocfilehash: 2734df728b188dcfbbe5f475cfc67715a070975d
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079092"
---
# <a name="headerunit-use-header-unit-ifc"></a>`/headerUnit` (Utiliser l’unité d’en-tête IFC)

Indique au compilateur de convertir les `#include` directives pour un nom d’en-tête importable en une `import header-name;` directive, plutôt que d’utiliser l’inclusion textuelle.

## <a name="syntax"></a>Syntaxe

> **`/headerUnit`** *`header-filename`*=*`ifc-filename`*

### <a name="arguments"></a>Arguments

*`header-filename`*\
Nom d’un fichier sur lequel le compilateur résout un `header-name` . Pendant `import header-name ;` que le compilateur se résout `header-name` en un fichier sur le disque. Utilisez *`header-filename`* pour spécifier ce fichier. Une fois qu’il a été mis en correspondance, le compilateur ouvre le IFC correspondant nommé par *`ifc-filename`* pour l’importation.

*`ifc-filename`*\
Nom d’un fichier qui contient des *données IFC*, informations de module prégénérées. Pour importer plusieurs unités d’en-tête, incluez une **`/headerUnit`** option distincte pour chaque fichier.

## <a name="remarks"></a>Notes

L' **`/headerUnit`** option de compilateur requiert l’activation de la prise en charge des modules expérimentaux à l’aide de l' [`/experimental:module`](experimental-module.md) option du compilateur, avec l’option [/std : c + + latest](std-specify-language-standard-version.md) . Cette option est disponible à partir de Visual Studio 2019 version 16,8.

Le compilateur ne peut pas mapper un seul *`header-name`* à plusieurs fichiers IFC. Bien qu' *`header-name`* il soit possible de mapper plusieurs arguments à une même IFC, nous ne le recommandons pas. Le contenu du IFC est importé comme s’il s’agissait uniquement de l’en-tête spécifié par *`header-name`* .

### <a name="examples"></a>Exemples

À partir d’un projet qui fait référence à deux fichiers d’en-tête et à leurs unités d’en-tête, listés dans ce tableau :

| Fichier d’en-tête | Fichier IFC |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

Les options du compilateur permettant de référencer les unités d’en-tête de ces fichiers d’en-tête peuvent ressembler à cet exemple :

```CMD
cl ... /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour ajouter les *`/headerUnit`* options et les arguments. Ensuite, cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[`/experimental:module` (Activer la prise en charge des modules)](experimental-module.md)\
[`/module:exportHeader` (Créer des unités d’en-tête)](module-exportheader.md)\
[`/module:reference` (Utilisez le module nommé IFC)](module-reference.md)\
[`/translateInclude` (Traduire les directives include en directives Import)](translateinclude.md)\
