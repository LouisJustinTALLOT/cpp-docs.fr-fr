---
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- limits/std::<limits>
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 3ad740975cfff4f65f9e1c800a709cfaca3367db
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687819"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Définit le `numeric_limits` de modèle de classe et deux énumérations concernant les représentations à virgule flottante et l’arrondi.

## <a name="requirements"></a>spécifications

**En-tête :** \<limits>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les spécialisations explicites de la classe `numeric_limits` décrivent de nombreuses propriétés des types fondamentaux, y compris le caractère, l’entier et les types à virgule flottante et **bool** qui sont définis par l’implémentation C++ plutôt que fixés par les règles du sous. Les propriétés décrites dans \<limits> incluent la précision, les représentations de taille minimale et maximale, l’arrondi et le signalement des erreurs de type.

## <a name="members"></a>Membres

### <a name="enumerations"></a>Énumérations

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.|

### <a name="classes"></a>Classes

|||
|-|-|
|[numeric_limits, classe](../standard-library/numeric-limits-class.md)|Le modèle de classe décrit les propriétés arithmétiques des types numériques intégrés.|

## <a name="see-also"></a>Voir aussi

[Référence de fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
