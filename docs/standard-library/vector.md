---
title: '&lt;vector&gt;'
ms.date: 11/04/2016
f1_keywords:
- <vector>
helpviewer_keywords:
- vector header
ms.assetid: c1431ad8-c0b6-4dbb-89c4-5f651e432d7f
ms.openlocfilehash: 4e9f3e4a35cd772897e326fafedf359062e6128b
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224524"
---
# <a name="ltvectorgt"></a>&lt;vector&gt;

Définit le vecteur de modèle de classe de conteneur et plusieurs modèles de prise en charge.

Le conteneur `vector` permet d'organiser les éléments d'un type donné dans une séquence linéaire. Il fournit un accès aléatoire rapide à chaque élément, et gère les ajouts et suppressions dynamiques dans la séquence. Il est recommandé d'utiliser le conteneur `vector` pour une séquence si votre priorité est de garantir des performances optimales au niveau de l'accès aléatoire.

> [!NOTE]
> La \<vector> bibliothèque utilise également l' `#include <initializer_list>` instruction.

Pour plus d’informations sur la classe `vector`, consultez [vector, classe](../standard-library/vector-class.md). Pour plus d’informations sur la spécialisation `vector<bool>` , consultez [Vector, \<bool> classe](../standard-library/vector-bool-class.md).

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

*Entrer*\
Paramètre de modèle pour le type de données stockées dans le vecteur.

*Allocateur*\
Paramètre de modèle pour l'objet allocateur stocké qui gère l'allocation et la libération de mémoire.

*gauche*\
Premier vecteur (à gauche) dans une opération de comparaison.

*Oui*\
Deuxième vecteur (à droite) dans une opération de comparaison.

## <a name="members"></a>Membres

### <a name="operators"></a>Opérateurs

|||
|-|-|
|[and! =](../standard-library/vector-operators.md#op_neq)|Vérifie si le vecteur situé à gauche de l'opérateur n'est pas égal au vecteur situé à droite.|
|[<d’opérateur](../standard-library/vector-operators.md#op_lt)|Vérifie si le vecteur situé à gauche de l'opérateur est inférieur au vecteur situé à droite.|
|[and\<=](../standard-library/vector-operators.md#op_gt_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est inférieur ou égal au vecteur situé à droite.|
|[opérateur = =](../standard-library/vector-operators.md#op_eq_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est égal au vecteur situé à droite.|
|[>d’opérateur](../standard-library/vector-operators.md#op_gt)|Vérifie si le vecteur situé à gauche de l'opérateur est supérieur au vecteur situé à droite.|
|[>opérateur =](../standard-library/vector-operators.md#op_gt_eq)|Vérifie si le vecteur situé à gauche de l'opérateur est supérieur ou égal au vecteur situé à droite.|

### <a name="classes"></a>Classes

|||
|-|-|
|[Vector, classe](../standard-library/vector-class.md)|Modèle de classe de conteneurs de séquence qui organisent les éléments d'un type donné dans une disposition linéaire et fournissent un accès aléatoire rapide à chaque élément.|

### <a name="specializations"></a>Spécialisations

|||
|-|-|
|Hachage|Retourne un hachage du vecteur.|
|[Vector, \<bool> classe](../standard-library/vector-bool-class.md)|Spécialisation complète du vecteur de modèle de classe pour les éléments de type **`bool`** avec un allocateur pour le type sous-jacent utilisé par la spécialisation.|

## <a name="requirements"></a>Spécifications

**En-tête :**\<vector>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
