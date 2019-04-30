---
title: treat_as_floating_point, structure
ms.date: 11/04/2016
f1_keywords:
- chrono/std::chrono::treat_as_floating_point
ms.assetid: d0a2161c-bbb2-4924-8961-7568d5ad5434
ms.openlocfilehash: 1b7b58983032ee74ed3d88feb7325cd537e1cc2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411940"
---
# <a name="treatasfloatingpoint-structure"></a>treat_as_floating_point, structure

Spécifie si `Rep` peut être traité comme un type à virgule flottante.

## <a name="syntax"></a>Syntaxe

```cpp
template <class Rep>
struct treat_as_floating_point : is_floating_point<Rep>;
```

## <a name="remarks"></a>Notes

`Rep` peut être traité comme un type à virgule flottante uniquement lorsque la spécialisation `treat_as_floating_point<Rep>` est dérivée de [true_type](../standard-library/type-traits-typedefs.md#true_type). La classe de modèle peut être spécialisée pour un type défini par l’utilisateur.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<chrono >

**Espace de noms :** std::chrono

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<chrono>](../standard-library/chrono.md)<br/>
