---
title: '&lt;vector&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <vector>
dev_langs:
- C++
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0fc8fb21afe1f024e4e5418d3cc706f654946de6
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857634"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Définit la classe de modèle de conteneur vector et plusieurs modèles de prise en charge.

Le conteneur `vector` permet d'organiser les éléments d'un type donné dans une séquence linéaire. Il fournit un accès aléatoire rapide à chaque élément, et gère les ajouts et suppressions dynamiques dans la séquence. Il est recommandé d'utiliser le conteneur `vector` pour une séquence si votre priorité est de garantir des performances optimales au niveau de l'accès aléatoire.

Pour plus d’informations sur la classe `vector`, consultez [vector, classe](../standard-library/vector-class.md). Pour plus d’informations sur la spécialisation `vector<bool>`, consultez [vector\<bool>, classe](../standard-library/vector-bool-class.md).

## <a name="syntax"></a>Syntaxe

```cpp
namespace std {
template <class Type, class Allocator>
class vector;
template <class Allocator>
class vector<bool>;

template <class Allocator>
struct hash<vector<bool, Allocator>>;
 // TEMPLATE FUNCTIONS
template <class Type, class Allocator>
bool operator== (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator!= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<(
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator> (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator<= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
bool operator>= (
    const vector<Type, Allocator>& left,
    const vector<Type, Allocator>& right);

template <class Type, class Allocator>
void swap (
    vector<Type, Allocator>& left,
    vector<Type, Allocator>& right);

}  // namespace std
```

### <a name="parameters"></a>Paramètres

Tapez le paramètre de modèle pour le type de données stockées dans le vecteur.

Le paramètre de modèle pour l’objet allocateur stocké responsable de l’allocation de mémoire et la libération d’allocateur.

`left` Premier vecteur (gauche) dans une opération de comparaison

`right` Deuxième vecteur (à droite) dans une opération de comparaison.

### <a name="operators"></a>Opérateurs

|Opérateur|Description|
|-|-|
|[operator! =](../standard-library/vector-operators.md#op_neq)|Vérifie si le vecteur situé à gauche de l'opérateur n'est pas égal au vecteur situé à droite.|
|[operator<](../standard-library/vector-operators.md#op_lt)|Vérifie si le vecteur situé à gauche de l'opérateur est inférieur au vecteur situé à droite.|
|[operator\<=](../standard-library/vector-operators.md#op_gt_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est inférieur ou égal au vecteur situé à droite.|
|[operator==](../standard-library/vector-operators.md#op_eq_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est égal au vecteur situé à droite.|
|[operator>](../standard-library/vector-operators.md#op_gt)|Vérifie si le vecteur situé à gauche de l'opérateur est supérieur au vecteur situé à droite.|
|[operator>=](../standard-library/vector-operators.md#op_gt_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est supérieur ou égal au vecteur situé à droite.|

### <a name="classes"></a>Classes

|Classe|Description|
|-|-|
|[vector, classe](../standard-library/vector-class.md)|Classe de modèle de conteneurs de séquence qui organisent les éléments d'un type donné dans une disposition linéaire et fournissent un accès aléatoire rapide à chaque élément.|

### <a name="specializations"></a>Spécialisations

|||
|-|-|
|[vector\<bool>, classe](../standard-library/vector-bool-class.md)|Spécialisation complète de la classe de modèle vector pour les éléments de type `bool` possédant un allocateur pour le type sous-jacent utilisé par la spécialisation.|

## <a name="requirements"></a>Spécifications

**En-tête :** \<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
