---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: aa143198ec662ae33263d1ee5d79ffadf51c61d9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50632451"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Définit la classe de modèle `numeric_limits` et deux énumérations concernant les représentations et l'arrondi des valeurs à virgule flottante.

## <a name="syntax"></a>Syntaxe

```cpp
#include <limits>

```

## <a name="remarks"></a>Notes

Les spécialisations explicites de la `numeric_limits` classe décrivent de nombreuses propriétés des types fondamentaux, y compris le caractère, entier et les types à virgule flottante et **bool** qui sont implémentation défini plutôt que fixés par les règles du langage C++. Les propriétés décrites dans \<limits> incluent la précision, les représentations de taille minimale et maximale, l’arrondi et le signalement des erreurs de type.

### <a name="enumerations"></a>Énumérations

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[numeric_limits, classe](../standard-library/numeric-limits-class.md)|La classe de modèle décrit les propriétés arithmétiques des types numériques intégrés.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
