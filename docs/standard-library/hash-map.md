---
description: 'En savoir plus sur : &lt; hash_map&gt;'
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: b3e46a3f8ef1638525414c1a1414c4eb6e418c31
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231873"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> Cet en-tête est obsolète. L’alternative est [\<unordered_map>](unordered-map.md) .

Définit les modèles de classe de conteneur hash_map et hash_multimap et leurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_map>
```

### <a name="operators"></a>Opérateurs

|Version de hash_map|Version de hash_multimap|Description|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[opérateur ! = (hash_multimap)](hash-map-operators.md#op_neq_mm)|Teste si l’objet hash_map ou hash_multimap situé à gauche de l’opérateur n’est pas égal à l’objet hash_map ou hash_multimap situé à droite.|
|[opérateur = = (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|Teste si l’objet hash_map ou hash_multimap situé à gauche de l’opérateur est égal à l’objet hash_map ou hash_multimap situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version de hash_map|Version de hash_multimap|Description|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|Échange les éléments de deux objets hash_maps ou hash_multimaps.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe hash_compare](hash-compare-class.md)|Décrit un objet qui peut être utilisé par l’un des conteneurs associatifs de hachage (hash_map, hash_multimap, hash_set ou hash_multiset) comme un `Traits` objet paramètre par défaut pour classer et hacher les éléments qu’ils contiennent.|
|[Classe value_compare](value-compare-class.md)|Fournit un objet de fonction qui peut comparer les éléments d’un hash_map en comparant les valeurs de leurs clés pour déterminer leur ordre relatif dans le hash_map.|
|[Classe hash_map](hash-map-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle chaque élément est une paire qui a une clé de tri dont la valeur est unique et une valeur de données associée.|
|[Classe hash_multimap](hash-multimap-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle chaque élément est une paire qui a une clé de tri dont la valeur ne doit pas nécessairement être unique et une valeur de données associée.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<hash_map>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](cpp-standard-library-reference.md)
