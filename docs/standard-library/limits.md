---
description: 'En savoir plus sur : &lt; limites&gt;'
title: '&lt;limits&gt;'
ms.date: 11/04/2016
f1_keywords:
- <limits>
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
ms.openlocfilehash: 23601b4b7f7ea06071a6b1f5fbd87ce0a0babce3
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98126388"
---
# <a name="ltlimitsgt"></a>&lt;limits&gt;

Définit le modèle `numeric_limits` de classe et deux énumérations concernant les représentations à virgule flottante et l’arrondi.

## <a name="requirements"></a>Spécifications

**En-tête :**\<limits>

**Espace de noms :** std

## <a name="remarks"></a>Notes

Les spécialisations explicites de la `numeric_limits` classe décrivent de nombreuses propriétés des types fondamentaux, y compris le caractère, l’entier et les types à virgule flottante, et **`bool`** qui sont définis par l’implémentation plutôt que fixés par les règles du langage C++. Les propriétés décrites dans \<limits> incluent la précision, les représentations de taille minimale et maximale, l’arrondi et les erreurs de type de signalisation.

## <a name="members"></a>Membres

### <a name="enumerations"></a>Énumérations

|Nom|Description|
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour représenter une valeur à virgule flottante dénormalisée (trop petite pour être représentée comme valeur normalisée) :|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|L'énumération décrit les différentes méthodes qu'une implémentation peut choisir pour arrondir une valeur à virgule flottante en une valeur entière.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[Classe numeric_limits](../standard-library/numeric-limits-class.md)|Le modèle de classe décrit les propriétés arithmétiques des types numériques intégrés.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)
