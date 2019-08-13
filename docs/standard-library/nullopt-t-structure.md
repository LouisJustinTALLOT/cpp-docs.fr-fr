---
title: Struct nullopt_t
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957043"
---
# <a name="nullopt_t-struct"></a>Struct nullopt_t

Le `nullopt_t` type est un type vide unique utilisé pour indiquer qu’un objet [facultatif](optional-class.md) ne contient pas de valeur.

La constante `nullopt` de type `nullopt_t` indique qu' `optional` un type a un État non initialisé. Il peut être utilisé pour initialiser un `optional` objet ou comparé à un.

## <a name="syntax"></a>Syntaxe

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>Voir aussi

[\<> facultative](optional.md)\
[classe facultative](optional-class.md)
