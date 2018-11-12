---
title: hash_compare, classe
ms.date: 11/04/2016
f1_keywords:
- hash_set/stdext::hash_compare
helpviewer_keywords:
- hash_compare class
ms.assetid: d502bb59-de57-4585-beb9-00e3a998c0af
ms.openlocfilehash: f535122b67f854b8b204664b829ce9da5fe3c6a6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575784"
---
# <a name="hashcompare-class"></a>hash_compare, classe

La classe de modèle décrit un objet qui peut être utilisé par les conteneurs associatifs de hachage, hash_map, hash_multimap, hash_set ou hash_multiset, comme objet de paramètre **Traits** par défaut pour ordonner et hacher les éléments qu’ils contiennent.

## <a name="syntax"></a>Syntaxe

class hash_compare { Traits comp; public: const size_t bucket_size = 4; const size_t min_buckets = 8; hash_compare(); hash_compare(Traits pred); size_t operator()(const Key& key) const; bool operator()( const Key& key1, const Key& key2) const; };

## <a name="remarks"></a>Notes

Chaque conteneur associatif de hachage stocke un objet de hachage de caractéristiques de type `Traits` (un paramètre de modèle). Vous pouvez dériver une classe d’une spécialisation de hash_compare pour remplacer de manière sélective certaines fonctions et certains objets, ou vous pouvez fournir votre propre version de cette classe si vous répondez à certaines exigences minimales. En particulier, pour un objet hash_comp de type `hash_compare<Key, Traits>`, le comportement suivant est requis par les conteneurs ci-dessus :

- Pour toutes les valeurs `key` de type `Key`, l’appel **hash_comp**(`key`) sert de fonction de hachage, ce qui produit une distribution de valeurs de type `size_t`. La fonction fournie par hash_compare retourne `key`.

- Pour toute valeur `key1` de type `Key` qui précède `key2` dans la séquence et ayant la même valeur de hachage (valeur retournée par la fonction de hachage), **hash_comp**(`key2`, `key1`) a la valeur false. La fonction doit imposer un ordonnancement total sur les valeurs de type `Key`. La fonction fournie par hash_compare retourne *comp*(`key2`, `key1`) `,` où *comp* est un objet stocké de type `Traits` que vous pouvez spécifier lorsque vous construire l’objet hash_comp. Pour la valeur par défaut `Traits` type de paramètre `less<Key>`, clés de tri va jamais en diminuant valeur.

- La constante entière `bucket_size` Spécifie le nombre moyen d’éléments par « compartiment » (entrée de table de hachage) que le conteneur doit essayer de ne pas dépasser. La valeur doit être supérieure à zéro. La valeur fournie par hash_compare est 4.

- La constante entière `min_buckets` Spécifie le nombre minimal de compartiments à conserver dans la table de hachage. Il doit s'agir d'une puissance de deux et sa valeur doit être supérieure à zéro. La valeur fournie par hash_compare est 8.

## <a name="example"></a>Exemple

Consultez les exemples pour [hash_map::hash_map](../standard-library/hash-map-class.md#hash_map), [hash_multimap::hash_multimap](../standard-library/hash-multimap-class.md#hash_multimap), [hash_set::hash_set](../standard-library/hash-set-class.md#hash_set) et [hash_multiset::hash_multiset](../standard-library/hash-multiset-class.md#hash_multiset) pour voir comment déclarer et utiliser hash_compare.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<hash_map>

**Espace de noms :** stdext

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
