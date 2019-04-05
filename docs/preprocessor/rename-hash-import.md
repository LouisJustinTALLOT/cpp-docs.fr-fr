---
title: rename (#import)
ms.date: 10/18/2018
f1_keywords:
- Rename
helpviewer_keywords:
- rename attribute
ms.assetid: 5c5c6153-1087-4b7b-87fb-fc59b90b9975
ms.openlocfilehash: 0fbed04f040a47b5b389f40eeb15254da4a7940b
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59037055"
---
# <a name="rename-import"></a>Renommer (\#importer)

**Section spécifique à C++**

Offre une solution de contournement pour les problèmes de collisions de noms.

## <a name="syntax"></a>Syntaxe

```
rename("OldName","NewName")
```

### <a name="parameters"></a>Paramètres

*OldName*<br/>
Ancien nom dans la bibliothèque de types.

*NouveauNom*<br/>
Nom à utiliser au lieu de l'ancien nom.

## <a name="remarks"></a>Notes

Si cet attribut est spécifié, le compilateur remplace toutes les occurrences de *OldName* dans une bibliothèque de types avec fournie par l’utilisateur *NewName* dans les fichiers d’en-tête qui en résulte.

Cet attribut peut être utilisé lorsqu'un nom de la bibliothèque de types coïncide avec une définition de macro dans les fichiers d'en-tête du système. Si cette situation n’est pas résolue, diverses erreurs de syntaxe seront générées, tel que [erreur du compilateur C2059](../error-messages/compiler-errors-1/compiler-error-c2059.md) et [erreur du compilateur C2061](../error-messages/compiler-errors-1/compiler-error-c2061.md).

> [!NOTE]
> Le remplacement concerne un nom utilisé dans la bibliothèque de types et pas un nom utilisé dans le fichier d'en-tête résultant.

Par exemple, supposons qu'une propriété nommée `MyParent` existe dans une bibliothèque de types et qu'une macro `GetMyParent` est définie dans un fichier d'en-tête et utilisée avant `#import`. Dans la mesure où `GetMyParent` est le nom par défaut d’une fonction wrapper pour la gestion des erreurs `get` propriété, une collision de nom se produit. Pour contourner le problème, utilisez l'attribut suivant dans l'instruction `#import` :

```cpp
rename("MyParent","MyParentX")
```

ce qui renomme le nom `MyParent` dans la bibliothèque de types. Une tentative de changement du nom du wrapper `GetMyParent` échoue :

```cpp
rename("GetMyParent","GetMyParentX")
```

Cela provient du fait que le nom `GetMyParent` se produit uniquement dans le fichier d'en-tête de bibliothèque de types résultant.

**FIN de la section spécifique à C++**

## <a name="see-also"></a>Voir aussi

[Attributs #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import, directive](../preprocessor/hash-import-directive-cpp.md)