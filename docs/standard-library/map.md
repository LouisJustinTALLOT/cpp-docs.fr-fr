---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 9a58160c573fac7d4ad170f589c04c75b456299a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88846431"
---
# <a name="ltmapgt"></a>&lt;map&gt;

Définit le mappage des modèles de classe de conteneur et Multimap et leurs modèles de prise en charge.

## <a name="requirements"></a>Configuration requise

**En-tête :**\<map>

**Espace de noms :** std

> [!NOTE]
> La \<map> bibliothèque utilise également l' `#include <initializer_list>` instruction.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|Version map|Version multimap|Description|
|-----------------|----------------------|-----------------|
|[opérateur ! = (Map)](../standard-library/map-operators.md#op_neq)|[opérateur ! = (Multimap)](../standard-library/map-operators.md#op_neq)|Teste si l'objet map ou multimap situé à gauche de l'opérateur n'est pas égal à l'objet map ou multimap situé à droite.|
|[< d’opérateur (Map)](../standard-library/map-operators.md#op_eq_eq)|[< d’opérateur (Multimap)](../standard-library/map-operators.md#op_eq_eq)|Teste si l'objet map ou multimap situé à gauche de l'opérateur est inférieur à l'objet map ou multimap situé à droite.|
|[opérateur<= (Map)](../standard-library/map-operators.md#op_lt)|[opérateur \< = (Multimap)](../standard-library/map-operators.md#op_lt)|Teste si l'objet map ou multimap situé à gauche de l'opérateur est inférieur ou égal à l'objet map ou multimap situé à droite.|
|[opérateur = = (Map)](../standard-library/map-operators.md#op_eq_eq)|[opérateur = = (Multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|Teste si l'objet map ou multimap situé à gauche de l'opérateur est égal à l'objet map ou multimap situé à droite.|
|[> d’opérateur (Map)](../standard-library/map-operators.md#op_gt)|[> d’opérateur (Multimap)](../standard-library/map-operators.md#op_gt_multimap)|Teste si l'objet map ou multimap situé à gauche de l'opérateur est supérieur à l'objet map ou multimap situé à droite.|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|Teste si l'objet map ou multimap situé à gauche de l'opérateur est supérieur ou égal à l'objet map ou multimap situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version map|Version multimap|Description|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|Échange les éléments de deux classes map ou multimap.|

### <a name="classes"></a>Classes

|Nom|Description|
|-|-|
|[Classe value_compare](../standard-library/value-compare-class-map.md)|Fournit un objet de fonction qui peut comparer les éléments d'un map en comparant les valeurs de leurs clés pour déterminer leur ordre relatif dans le map.|
|[Map (classe)](../standard-library/map-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle chacun des éléments a une clé unique avec laquelle les données sont automatiquement triées.|
|[multimap, classe](../standard-library/multimap-class.md)|Sert au stockage et à la récupération des données d’une collection dans laquelle chacun des éléments a une clé avec laquelle les données sont automatiquement triées et les clés ne doivent pas obligatoirement avoir des valeurs uniques.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
