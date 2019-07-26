---
title: Conteneur Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: ccf4ae6ebc3ca13a42ca950310a60e30dbb27034
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450768"
---
# <a name="container-classswap"></a>Conteneur Class::swap

> [!NOTE]
> Cette rubrique se trouve dans la C++ documentation de Microsoft comme un exemple non fonctionnel de conteneurs utilisés dans C++ la bibliothèque standard. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../standard-library/stl-containers.md).

Échange les séquences contrôlées entre **\*this** et son argument.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Notes

Si **\*this.get\_allocator ==** _right_ **.get_allocator**, l’échange est effectué en temps constant. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.

## <a name="see-also"></a>Voir aussi

[Sample Container, classe](../standard-library/sample-container-class.md)
