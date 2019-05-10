---
title: Conteneur Class::erase
ms.date: 11/04/2016
helpviewer_keywords:
- erase method
ms.assetid: abc091c5-5a80-4bd8-93a8-a2d9bde2efec
ms.openlocfilehash: 0ef4db1c14942fc896f10095ff2331648d27c820
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221636"
---
# <a name="container-classerase"></a>Conteneur Class::erase

> [!NOTE]
> Cette rubrique se trouve dans le Microsoft C++ documentation comme exemple non fonctionnel de conteneurs utilisés dans le C++ bibliothèque Standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

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

La première fonction membre supprime l’élément de la séquence contrôlée vers lequel pointé *_Where*. La deuxième fonction membre supprime l’élément de la séquence contrôlée dans la plage [`first`, `last`). Les deux fonctions retournent un itérateur qui désigne le premier élément restant après tous les éléments supprimés, ou [end](../standard-library/container-class-end.md) si aucun élément de ce genre n’existe.

Les fonctions membres lèvent une exception uniquement si une opération de copie lève une exception.

## <a name="see-also"></a>Voir aussi

[Sample Container, classe](../standard-library/sample-container-class.md)<br/>
