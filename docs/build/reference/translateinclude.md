---
title: /translateInclude (traduire les directives include en directives Import)
description: 'Utilisez l’option du compilateur/translateInclude pour convertir des directives #include pour un nom d’en-tête importable en une directive import-Header-Name.'
ms.date: 09/13/2020
f1_keywords:
- /translateInclude
helpviewer_keywords:
- /translateInclude
- Translate include directives into import directives
ms.openlocfilehash: 0050f2cb117e48d69cf97a587ef128b9b45790af
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079079"
---
# <a name="translateinclude-translate-include-directives-into-import-directives"></a>`/translateInclude` (Traduire les directives include en directives Import)

Indique au compilateur de convertir les `#include` directives pour un nom d’en-tête importable en une `import header-name;` directive, plutôt que d’utiliser l’inclusion textuelle.

## <a name="syntax"></a>Syntaxe

> **`/translateInclude`**

## <a name="remarks"></a>Notes

L' **`/translateInclude`** option de compilateur requiert l’activation de la prise en charge des modules expérimentaux à l’aide de l' [`/experimental:module`](experimental-module.md) option du compilateur, avec l’option [/std : c + + latest](std-specify-language-standard-version.md) . Cette option est disponible à partir de Visual Studio 2019 version 16,8.

L' **`/translateInclude`** option effectue effectivement la transformation suivante, où l’exemple `<vector>` est une unité d’en-tête importable :

```cpp
#include <vector>
```

Le compilateur remplace cette directive par :

```cpp
import <vector> ;
```

Dans MSVC, une unité d’en-tête importable est une unité nommée par une **`/headerUnit`** référence. Pour plus d’informations, consultez [ `/headerUnit` (utiliser l’unité d’en-tête IFC)](headerunit.md).

### <a name="examples"></a>Exemples

À partir d’un projet qui fait référence à deux fichiers d’en-tête et à leurs unités d’en-tête, listés dans ce tableau :

| Fichier d’en-tête | Fichier IFC |
|--|--|
| *`C:\utils\util.h`* | *`C:\util.h.ifc`* |
| *`C:\app\app.h`* | *`C:\app.h.ifc`* |

Et un *`.cpp`* fichier source qui comprend les en-têtes,

```cpp
#include "utils/util.h"
#include "app/app.h"

int main() { }
```

L' **`/translateInclude`** option permet au compilateur d’importer les unités d’en-tête au lieu de compiler à nouveau les en-têtes. Voici un exemple de ligne de commande qui traduit les directives include pour *`util.h`* et *`app.h`* en importations des unités d’en-tête à la place :

```CMD
cl /IC:\ /experimental:module /translateInclude /headerUnit C:\utils\util.h=C:\util.h.ifc /headerUnit C:\app\app.h=C:\app.h.ifc
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour ajouter l' *`/translateInclude`* option. Ensuite, cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[`/experimental:module` (Activer la prise en charge des modules)](experimental-module.md)\
[ `/headerUnit` (Utilisez l’unité d’en-tête IFC)](headerunit.md). \
[`/module:exportHeader` (Créer des unités d’en-tête)](module-exportheader.md)\
[`/module:reference` (Utilisez le module nommé IFC)](module-reference.md)
