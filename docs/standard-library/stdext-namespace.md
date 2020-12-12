---
description: 'En savoir plus sur : espace de noms stdext'
title: Espace de noms stdext
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: bb81dde22014ec91f7212ce4313c21a8410f30a9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97153783"
---
# <a name="stdext-namespace"></a>Espace de noms stdext

Les membres des [\<hash_map>](../standard-library/hash-map.md) [\<hash_set>](../standard-library/hash-set.md) fichiers d’en-tête et ne font pas partie de la norme ISO C++. Par conséquent, ces types et ces membres ont été déplacés de l’espace de noms `std` vers l’espace de noms `stdext`, de façon à rester conforme à la norme C++.

Lors de la compilation avec [/Ze](../build/reference/za-ze-disable-language-extensions.md), qui est la valeur par défaut, le compilateur vous avertit de l’utilisation de `std` pour les membres des \<hash_map> fichiers d' \<hash_set> en-tête et. Pour désactiver l’avertissement, utilisez le pragma [warning](../preprocessor/warning.md) .

Pour que le compilateur génère une erreur pour l’utilisation de `std` pour les membres des \<hash_map> \<hash_set> fichiers d’en-tête et avec **/Ze**, ajoutez la directive suivante avant `#include` tous les fichiers d’en-tête de bibliothèque standard C++.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Lors de la compilation avec **/za**, le compilateur génère une erreur.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)
