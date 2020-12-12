---
description: 'En savoir plus sur : Container Class :: swap'
title: Conteneur Class::swap
ms.date: 11/04/2016
helpviewer_keywords:
- swap method
ms.assetid: 898c219c-bc8e-4d14-a149-6240426c693f
ms.openlocfilehash: a38dd6d14ada3ad50927060ccec1542ebf2fd4ca
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233355"
---
# <a name="container-classswap"></a>Conteneur Class::swap

> [!NOTE]
> Cette rubrique se trouve dans la documentation de Microsoft C++ comme un exemple non fonctionnel de conteneurs utilisés dans la bibliothèque standard C++. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../standard-library/stl-containers.md).

Échange les séquences contrôlées entre **\* ce** et son argument.

## <a name="syntax"></a>Syntaxe

```cpp
void swap(Container& right);
```

## <a name="remarks"></a>Notes

Si **\* this. obtenir \_ Allocator = =** _Right_**.get_allocator**, il effectue un échange en temps constant. Sinon, elle effectue un nombre d’affectations d’éléments et d’appels de constructeurs proportionnel au nombre d’éléments dans les deux séquences contrôlées.

## <a name="see-also"></a>Voir aussi

[Exemple de classe de conteneur](../standard-library/sample-container-class.md)
