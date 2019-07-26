---
title: Conteneur Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 1463a854c314884f0b3b6bffa5d37dfb7fec4a6f
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454512"
---
# <a name="container-classerase"></a>Conteneur Class::erase

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Efface un élément.

## <a name="syntax"></a>Syntaxe

```

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

[Sample Container, classe](../standard-library/sample-container-class.md)
