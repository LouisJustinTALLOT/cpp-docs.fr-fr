---
title: Définitions et déclarations (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: 987e27bdf35eba7d9380fc546c15b93b3179333b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628941"
---
# <a name="definitions-and-declarations-c"></a>Définitions et déclarations (C++)

**Section spécifique à Microsoft**

L’interface DLL fait référence à tous les éléments (fonctions et données) qui sont connus pour être exportés par un programme dans le système ; Autrement dit, tous les éléments qui sont déclarés comme **dllimport** ou **dllexport**. Toutes les déclarations incluses dans l’interface DLL doivent spécifier soit le **dllimport** ou **dllexport** attribut. Toutefois, la définition doit spécifier uniquement la **dllexport** attribut. Par exemple, la définition de fonction suivante génère une erreur de compilation :

```
__declspec( dllimport ) int func() {   // Error; dllimport
                                       // prohibited on definition.
   return 1;
}
```

Le code suivant génère aussi une erreur :

```
__declspec( dllimport ) int i = 10;  // Error; this is a definition.
```

Mais voici la syntaxe correcte :

```
__declspec( dllexport ) int i = 10;  // Okay--export definition
```

L’utilisation de **dllexport** implique une définition, tandis que **dllimport** implique une déclaration. Vous devez utiliser le **extern** mot clé with **dllexport** pour forcer une déclaration ; sinon, une définition est impliquée. Les exemples suivants sont donc corrects :

```
#define DllImport   __declspec( dllimport )
#define DllExport   __declspec( dllexport )

extern DllExport int k; // These are both correct and imply a
DllImport int j;        // declaration.
```

Les exemples suivants clarifient l'exemple précédent :

```
static __declspec( dllimport ) int l; // Error; not declared extern.

void func() {
    static __declspec( dllimport ) int s;  // Error; not declared
                                           // extern.
    __declspec( dllimport ) int m;         // Okay; this is a
                                           // declaration.
    __declspec( dllexport ) int n;         // Error; implies external
                                           // definition in local scope.
    extern __declspec( dllimport ) int i;  // Okay; this is a
                                           // declaration.
    extern __declspec( dllexport ) int k;  // Okay; extern implies
                                           // declaration.
    __declspec( dllexport ) int x = 5;     // Error; implies external
                                           // definition in local scope.
}
```

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)