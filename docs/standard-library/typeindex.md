---
title: '&lt;typeindex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <typeindex>
ms.assetid: a9551137-f74b-4f02-af64-ff00214cea1f
ms.openlocfilehash: 237356a0862ec3fc591264b482b23e62ef2c51cb
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68455063"
---
# <a name="lttypeindexgt"></a>&lt;typeindex&gt;

Incluez l’en-tête standard \<typeindex> pour définir une classe et une fonction qui prennent en charge l’indexation des objets de la classe [type_info](../cpp/type-info-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
#include <typeindex>
```

## <a name="remarks"></a>Notes

La [structure hash](../standard-library/hash-structure.md) définit une `hash function` appropriée pour mapper des valeurs de type [type_index](../standard-library/type-index-class.md) à une distribution de valeurs d’index.

La classe `type_index` encapsule un pointeur vers un objet `type_info` pour faciliter l’indexation.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
