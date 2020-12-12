---
description: 'En savoir plus sur : renommer l’attribut d’importation'
title: renommer l’attribut d’importation
ms.date: 08/29/2019
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 3003300887dadbab5cf05396ff3fa38b6dd29026
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97176598"
---
# <a name="rename-import-attribute"></a>renommer l’attribut d’importation

**Section spécifique à C++**

Offre une solution de contournement pour les problèmes de collisions de noms.

## <a name="syntax"></a>Syntaxe

> renommage de la *bibliothèque de types* **#import** **(** «*OldName*» **,** «*NewName*» **)**

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

Par exemple, supposons qu'une propriété nommée `MyParent` existe dans une bibliothèque de types et qu'une macro `GetMyParent` est définie dans un fichier d'en-tête et utilisée avant `#import`. Étant donné que `GetMyParent` est le nom par défaut d’une fonction wrapper pour la propriété de gestion des erreurs `get` , une collision de nom se produit. Pour contourner le problème, utilisez l'attribut suivant dans l'instruction `#import` :

```cpp
#import MyTypeLib.tlb rename("MyParent","MyParentX")
```

ce qui renomme le nom `MyParent` dans la bibliothèque de types. Une tentative de changement du nom du wrapper `GetMyParent` échoue :

```cpp
#import MyTypeLib.tlb rename("GetMyParent","GetMyParentX")
```

Cela est dû au fait que le nom `GetMyParent` ne se produit que dans le fichier d’en-tête de la bibliothèque de types résultant.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[attributs #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import directive](../preprocessor/hash-import-directive-cpp.md)
