---
description: 'En savoir plus sur : &lt; hash_set&gt;'
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: aec05414d11bd5312febf4dd61b71db1b3f04452
ms.sourcegitcommit: 118e4ad82c0f1c9ac120f105d84224e5fe4cef28
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2021
ms.locfileid: "98125959"
---
# <a name="lthash_setgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Cet en-tête est obsolète. L’alternative est [<unordered_set>](../standard-library/unordered-set.md).

Définit les modèles de classe de conteneur hash_set et hash_multiset et leurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_set>
```

## <a name="remarks"></a>Notes

### <a name="operators"></a>Opérateurs

|Version de hash_set|Version de hash_multiset|Description|
|-----------------------|----------------------------|-----------------|
|[opérateur ! = (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Teste si l’objet hash_set ou hash_multiset situé à gauche de l’opérateur n’est pas égal à l’objet hash_set ou hash_multiset situé à droite.|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[opérateur = = (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Teste si l’objet hash_set ou hash_multiset situé à gauche de l’opérateur est égal à l’objet hash_set ou hash_multiset situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version de hash_set|Version de hash_multiset|Description|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Échange les éléments de deux objets hash_set ou hash_multiset.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[Classe hash_compare](../standard-library/hash-compare-class.md)|Décrit un objet qui peut être utilisé par l’un des conteneurs associatifs de hachage (hash_map, hash_multimap, hash_set ou hash_multiset) comme un `Traits` objet paramètre par défaut pour classer et hacher les éléments qu’ils contiennent.|
|[Classe hash_set](../standard-library/hash-set-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés.|
|[Classe hash_multiset](../standard-library/hash-multiset-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
