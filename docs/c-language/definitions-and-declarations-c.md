---
title: Définitions et déclarations (C)
ms.date: 11/04/2016
helpviewer_keywords:
- export functions
ms.assetid: d150395a-89d4-4298-9ac4-08f84fe1261c
ms.openlocfilehash: 0e39832f942eb1473be913112fde1d37ddf05674
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226364"
---
# <a name="definitions-and-declarations-c"></a>Définitions et déclarations (C)

**Spécifique à Microsoft**

L’interface DLL fait référence à tous les éléments (fonctions et données) qui sont connus pour être exportés par un programme du système. autrement dit, tous les éléments déclarés comme **`dllimport`** ou `dllexport` . Toutes les déclarations incluses dans l’interface DLL doivent spécifier l' **`dllimport`** `dllexport` attribut ou. Toutefois, la définition peut spécifier uniquement l'attribut `dllexport`. Par exemple, la définition de fonction suivante génère une erreur de compilation :

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int func()    /* Error; dllimport prohibited in */
                        /* definition. */
{
   return 1;
}
```

Le code suivant génère aussi une erreur :

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllImport int i = 10;      /* Error; this is a definition. */
```

Mais voici la syntaxe correcte :

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

DllExport int i = 10;      /* Okay: this is an export definition. */
```

L’utilisation de `dllexport` implique une définition, tandis que **`dllimport`** implique une déclaration. Vous devez utiliser le **`extern`** mot clé avec `dllexport` pour forcer une déclaration ; sinon, une définition est implicite.

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllImport int k;   /* These are correct and imply */
Dllimport int j;          /* a declaration. */
```

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Fonctions d’importation et d’exportation de DLL](../c-language/dll-import-and-export-functions.md)
