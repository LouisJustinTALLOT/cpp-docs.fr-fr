---
title: '&lt;d’exécution&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 81e9aa63265c367412fda709aacd5ca3953e9fdf
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445027"
---
# <a name="ltexecutiongt"></a>&lt;d’exécution&gt;

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
|[Classe parallel_policy](parallel-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.|
|[Classe parallel_unsequenced_policy](parallel-unsequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée et vectorisé.|
|[Classe sequenced_policy](sequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et exiger que l’exécution d’un algorithme parallèle ne soit pas parallélisée.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<d’exécution >

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ Standard](cpp-standard-library-reference.md)
