---
title: Définitions et déclarations (C++)
ms.date: 11/04/2016
ms.assetid: 56b809c0-e602-4f18-9ca5-cd7a8fbaaf30
ms.openlocfilehash: c35c0adaa1b81e5bf9bfd9e779037bc6068b3174
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221703"
---
# <a name="definitions-and-declarations-c"></a>Définitions et déclarations (C++)

**Spécifique à Microsoft**

L’interface DLL fait référence à tous les éléments (fonctions et données) qui sont connus pour être exportés par un programme du système. autrement dit, tous les éléments déclarés comme **`dllimport`** ou **`dllexport`** . Toutes les déclarations incluses dans l’interface DLL doivent spécifier l' **`dllimport`** **`dllexport`** attribut ou. Toutefois, la définition doit spécifier uniquement l' **`dllexport`** attribut. Par exemple, la définition de fonction suivante génère une erreur de compilation :

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

L’utilisation de **`dllexport`** implique une définition, tandis que **`dllimport`** implique une déclaration. Vous devez utiliser le **`extern`** mot clé avec **`dllexport`** pour forcer une déclaration ; sinon, une définition est implicite. Les exemples suivants sont donc corrects :

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

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[dllexport, dllimport](../cpp/dllexport-dllimport.md)
