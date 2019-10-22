---
title: treat_as_floating_point, structure
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: add69179b23a953a937458cbfa55254b21c5ea37
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72685113"
---
# <a name="treat_as_floating_point-structure"></a>treat_as_floating_point, structure

Spécifie si `Rep` peut être traité comme un type à virgule flottante.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Notes

`Rep` peut être traité comme un type à virgule flottante uniquement lorsque la spécialisation `treat_as_floating_point<Rep>` est dérivée de [true_type](../standard-library/type-traits-typedefs.md#true_type). Le modèle de classe peut être spécialisé pour un type défini par l’utilisateur.

## <a name="requirements"></a>spécifications

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[\<chrono>](../standard-library/chrono.md)
