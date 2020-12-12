---
description: 'En savoir plus sur : conteneur Class :: Erase'
title: Conteneur Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 7e9d7747237a38c42bfb7a39c5d5e66cc8a44608
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324865"
---
# <a name="container-classerase"></a>Conteneur Class::erase

> [!NOTE]
> Cette rubrique se trouve dans la documentation de Microsoft C++ comme un exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../standard-library/stl-containers.md).

Efface un élément.

## <a name="syntax"></a>Syntaxe

```cpp
iterator erase(
    iterator _Where);

iterator erase(
    iterator first,
    iterator last);
```

## <a name="remarks"></a>Notes

La première fonction membre supprime l’élément de la séquence contrôlée pointée par *_WHERE*. La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Les deux fonctions retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [end](../standard-library/container-class-end.md) si aucun élément de ce genre n’existe.

Les fonctions membres lèvent une exception uniquement si une opération de copie lève une exception.

## <a name="see-also"></a>Voir aussi

[Exemple de classe de conteneur](../standard-library/sample-container-class.md)
