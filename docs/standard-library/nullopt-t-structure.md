---
description: 'En savoir plus sur : struct nullopt_t'
title: Struct nullopt_t
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 7a597dcc5f15843f125dc7572dc4c5694320f0bb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97338111"
---
# <a name="nullopt_t-struct"></a>Struct nullopt_t

Le `nullopt_t` type est un type vide unique utilisé pour indiquer qu’un objet [facultatif](optional-class.md) ne contient pas de valeur.

La constante `nullopt` de type `nullopt_t` indique qu’un `optional` type a un État non initialisé. Il peut être utilisé pour initialiser un `optional` objet ou comparé à un.

## <a name="syntax"></a>Syntaxe

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>Voir aussi

[\<optional>](optional.md)\
[optional, classe](optional-class.md)
