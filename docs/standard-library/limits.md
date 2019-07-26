---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: de8f815cd59b84a1e63c231e18e4882d0b5d6f09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447572"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Définit la classe de modèle `numeric_limits` et deux énumérations concernant les représentations et l'arrondi des valeurs à virgule flottante.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<limits>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les spécialisations explicites `numeric_limits` de la classe décrivent de nombreuses propriétés des types fondamentaux, y compris le caractère, l’entier et les types à virgule flottante et **bool** qui sont définis par l’implémentation plutôt que fixés par les règles du C++langue. Les propriétés décrites dans \<limits> incluent la précision, les représentations de taille minimale et maximale, l’arrondi et le signalement des erreurs de type.

## <a name="members"></a>Membres

### <a name="enumerations"></a>Énumérations

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.|

### <a name="classes"></a>Classes

|||
|-|-|
|[numeric_limits, classe](../standard-library/numeric-limits-class.md)|La classe de modèle décrit les propriétés arithmétiques des types numériques intégrés.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
