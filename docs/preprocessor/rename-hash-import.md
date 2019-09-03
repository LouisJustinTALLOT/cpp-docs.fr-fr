---
title: renommer l’attribut d’importation
ms.date: 08/29/2019
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: ef1f64e0c268f850899efe499f7b1ad3991dd570
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216663"
---
# <a name="rename-import-attribute"></a>renommer l’attribut d’importation

**C++Plus**

Offre une solution de contournement pour les problèmes de collisions de noms.

## <a name="syntax"></a>Syntaxe

> **#import** *bibliothèque de types* **Rename (** «*OldName*» **,** «*NewName*» **)**

### <a name="parameters"></a>Paramètres

*OldName*\
Ancien nom dans la bibliothèque de types.

*NewName*\
Nom à utiliser au lieu de l'ancien nom.

## <a name="remarks"></a>Notes

Lorsque l’attribut **Rename** est spécifié, le compilateur remplace toutes les occurrences de *OldName* dans la *bibliothèque de types* par le *NewName* fourni par l’utilisateur dans les fichiers d’en-tête résultants.

L’attribut **Rename** peut être utilisé lorsqu’un nom dans la bibliothèque de types coïncide avec une définition de macro dans les fichiers d’en-tête système. Si cette situation n’est pas résolue, le compilateur peut émettre diverses erreurs de syntaxe, telles que l' [Erreur du compilateur C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) et l' [Erreur du compilateur C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Le remplacement concerne un nom utilisé dans la bibliothèque de types et pas un nom utilisé dans le fichier d'en-tête résultant.

Par exemple, supposons qu'une propriété nommée `MyParent` existe dans une bibliothèque de types et qu'une macro `GetMyParent` est définie dans un fichier d'en-tête et utilisée avant `#import`. Étant `GetMyParent` donné que est le nom par défaut d’une fonction wrapper pour la `get` propriété de gestion des erreurs, une collision de nom se produit. Pour contourner le problème, utilisez l'attribut suivant dans l'instruction `#import` :

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

ce qui renomme le nom `MyParent` dans la bibliothèque de types. Une tentative de changement du nom du wrapper `GetMyParent` échoue :

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Cela est dû au fait `GetMyParent` que le nom ne se produit que dans le fichier d’en-tête de la bibliothèque de types résultant.

**Spécifique C++ à la fin**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
