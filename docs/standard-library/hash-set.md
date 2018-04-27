---
title: '&lt;hash_set&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- <hash_set>
- std::<hash_set>
dev_langs:
- C++
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 909944726124a6a3a87ba60ea790945d67ad17a9
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> Cet en-tête est obsolète. L’alternative est [<unordered_set>](../standard-library/unordered-set.md).

Définit les classes de modèle de conteneur hash_set et hash_multiset et leurs modèles de prise en charge.

## <a name="syntax"></a>Syntaxe

```cpp
#include <hash_set>

```

## <a name="remarks"></a>Notes

### <a name="operators"></a>Opérateurs

|Version de hash_set|Version de hash_multiset|Description|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|Teste si l’objet hash_set ou hash_multiset situé à gauche de l’opérateur n’est pas égal à l’objet hash_set ou hash_multiset situé à droite.|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator== (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|Teste si l’objet hash_set ou hash_multiset situé à gauche de l’opérateur est égal à l’objet hash_set ou hash_multiset situé à droite.|

### <a name="specialized-template-functions"></a>Fonctions avec modèle spécialisé

|Version de hash_set|Version de hash_multiset|Description|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|Échange les éléments de deux objets hash_set ou hash_multiset.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[hash_compare, classe](../standard-library/hash-compare-class.md)|Décrit un objet qui peut être utilisé par les conteneurs associatifs de hachage, hash_map, hash_multimap, hash_set ou hash_multiset, comme objet de paramètre **Traits** par défaut pour ordonner et hacher les éléments qu’ils contiennent.|
|[hash_set, classe](../standard-library/hash-set-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés.|
|[hash_multiset, classe](../standard-library/hash-multiset-class.md)|Sert au stockage et à la récupération rapide des données d’une collection dans laquelle les valeurs des éléments contenus sont uniques et servent de valeurs de clés.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
