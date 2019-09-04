---
title: '&lt;random&gt;, fonctions'
ms.date: 09/04/2019
f1_keywords:
- random/std::generate_canonical
ms.assetid: 2ac9ec59-619b-4b85-a425-f729277c1bc8
helpviewer_keywords:
- std::generate_canonical
ms.openlocfilehash: 3d94f607fc6b7bdf22d7f573f590b451dbaa718d
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273838"
---
# <a name="ltrandomgt-functions"></a>&lt;random&gt;, fonctions

## <a name="generate_canonical"></a>generate_canonical

Retourne une valeur à virgule flottante à partir d'une séquence aléatoire.

```cpp
template <class RealType, size_t Bits, class Generator>
RealType generate_canonical(Generator& Gen);
```

### <a name="parameters"></a>Paramètres

*RealType*\
Type intégral à virgule flottante. Pour connaître les types possibles, consultez [\<random>](../standard-library/random.md).

*Bits*\
Nombre de bits de caractère aléatoire à utiliser.

*Dynamo*\
Classe de générateur de nombres aléatoires.

*Général*\
Référence à une instance d’un générateur de nombres aléatoires de type *Generator*.

### <a name="remarks"></a>Notes

La fonction de modèle `operator()` appelle *à plusieurs reprises* et comprime les valeurs retournées dans une valeur `x` à virgule flottante de type *RealType* jusqu’à ce qu’elle ait recueilli le `x`nombre spécifié de bits de mantisse dans. Le nombre spécifié est le plus petit des *bits* (qui doit être différent de zéro) et le nombre complet de bits de mantisse dans *RealType*. Le premier appel fournit les bits d'ordre le plus bas. La fonction retourne `x`.
