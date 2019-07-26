---
title: '&lt;production&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3b0ccd540c56500c2f265aa6192a12fc2d5078b0
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457965"
---
# <a name="ltexecutiongt"></a>&lt;production&gt;

Décrit les stratégies d’exécution pour les algorithmes parallèles.

## <a name="syntax"></a>Syntaxe

```
namespace std {
    template<class T> inline constexpr bool is_execution_policy_v = is_execution_policy<T>::value;
}
namespace std::execution {
    inline constexpr sequenced_policy seq { unspecified };
    inline constexpr parallel_policy par { unspecified };
    inline constexpr parallel_unsequenced_policy par_unseq { unspecified };
}
```
### <a name="classes-and-structs"></a>Classes et structs

|||
|-|-|
|[Struct is_execution_policy](is-execution-policy-struct.md)|Détecte les stratégies d’exécution pour l’exclusion des signatures de fonction de la participation à la résolution de surcharge ambiguë.|
|[parallel_policy, classe](parallel-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.|
|[parallel_unsequenced_policy, classe](parallel-unsequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée et vectorisé.|
|[sequenced_policy, classe](sequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et exiger que l’exécution d’un algorithme parallèle ne soit pas parallélisée.|

## <a name="requirements"></a>Configuration requise

**En-tête:** \<> d’exécution

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](cpp-standard-library-reference.md)
