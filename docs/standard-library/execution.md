---
title: '&lt;Exécution&gt;'
ms.date: 04/18/2019
f1_keywords:
- <execution>
- std::<execution>
helpviewer_keywords:
- execution header
ms.openlocfilehash: 3bce34019f9ed4880d72a9d16c3c8b78dde0e0e3
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268421"
---
# <a name="ltexecutiongt"></a>&lt;Exécution&gt;

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
|[is_execution_policy Struct](is-execution-policy-struct.md)|Détecte les stratégies d’exécution pour les besoins à l’exclusion des signatures de fonction de la participation de résolution de surcharge ambiguë dans le cas contraire.|
|[parallel_policy, classe](parallel-policy-class.md)|Utilisé comme un type unique pour lever l’ambiguïté de surcharge de l’algorithme parallèle et d’indiquer que l’exécution d’un algorithme parallèle peut être parallélisée.|
|[parallel_unsequenced_policy, classe](parallel-unsequenced-policy-class.md)|Utilisé comme un type unique pour lever l’ambiguïté de surcharge de l’algorithme parallèle et d’indiquer que l’exécution d’un algorithme parallèle peut être parallélisée et vectorisée.|
|[sequenced_policy, classe](sequenced-policy-class.md)|Utilisé comme un type unique pour lever l’ambiguïté de surcharge de l’algorithme parallèle et nécessitent que l’exécution d’un algorithme parallèle ne peut pas être parallélisée.|

## <a name="requirements"></a>Configuration requise

**En-tête :** \<exécution >

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](cpp-standard-library-reference.md)
