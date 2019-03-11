---
title: stdext, espace de noms
ms.date: 09/06/2017
f1_keywords:
- stdext
helpviewer_keywords:
- _DEFINE_DEPRECATED_HASH_CLASSES symbol
- stdext namespace
ms.assetid: 3e94fc89-0584-424f-bc09-081b73379545
ms.openlocfilehash: d40f3f7a99db72784cc9a32a9c37064228597d34
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750531"
---
# <a name="stdext-namespace"></a>stdext, espace de noms

Membres de la [ \<hash_map >](../standard-library/hash-map.md) et [ \<hash_set >](../standard-library/hash-set.md) fichiers d’en-tête ne sont pas actuellement partie de la norme ISO C++. Par conséquent, ces types et ces membres ont été déplacés de l’espace de noms `std` vers l’espace de noms `stdext`, de façon à rester conforme à la norme C++.

Lors de la compilation avec [/Ze](../build/reference/za-ze-disable-language-extensions.md), qui est la valeur par défaut, le compilateur vous avertit de l’utilisation de `std` pour les membres de la \<hash_map > et \<hash_set > fichiers d’en-tête. Pour désactiver l’avertissement, utilisez le pragma [warning](../preprocessor/warning.md) .

Pour que le compilateur génère une erreur pour l’utilisation de `std` pour les membres de la \<hash_map > et \<hash_set > avec les fichiers d’en-tête **/Ze**, ajoutez la directive suivante avant de vous `#include` les fichiers d’en-tête de bibliothèque C++ Standard.

```cpp
#define _DEFINE_DEPRECATED_HASH_CLASSES 0
```

Lors de la compilation avec **/Za**, le compilateur génère une erreur.

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la bibliothèque standard C++](../standard-library/cpp-standard-library-overview.md)
