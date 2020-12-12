---
description: 'En savoir plus sur : &lt; exécution&gt;'
title: '&lt;production&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: ea444ab2f4fcf3211e85837701a8ea6a0c3ec81f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97324407"
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

|Nom|Description|
|-|-|
|[Struct is_execution_policy](is-execution-policy-struct.md)|Détecte les stratégies d’exécution pour l’exclusion des signatures de fonction de la participation à la résolution de surcharge ambiguë.|
|[Classe parallel_policy](parallel-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.|
|[Classe parallel_unsequenced_policy](parallel-unsequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et indiquer que l’exécution d’un algorithme parallèle peut être parallélisée et vectorisé.|
|[Classe sequenced_policy](sequenced-policy-class.md)|Utilisé comme type unique pour lever l’ambiguïté de la surcharge de l’algorithme parallèle et exiger que l’exécution d’un algorithme parallèle ne soit pas parallélisée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<execution>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](cpp-standard-library-reference.md)
