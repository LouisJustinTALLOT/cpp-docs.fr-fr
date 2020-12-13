---
description: 'En savoir plus sur : struct output_iterator_tag'
title: output_iterator_tag, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 1bd97f88dc7ae68976920cf006cd10115b16b2f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340903"
---
# <a name="output_iterator_tag-struct"></a>output_iterator_tag, struct

Classe qui fournit un type de retour pour une `iterator_category` fonction qui représente un itérateur de sortie.

## <a name="syntax"></a>Syntaxe

output_iterator_tag de struct {} ;

## <a name="remarks"></a>Notes

Les classes de balise de catégorie sont utilisées comme balises de compilation pour la sélection de l’algorithme. La fonction de modèle doit rechercher la catégorie la plus spécifique de son argument d’itérateur, pour pouvoir utiliser l’algorithme le plus efficace au moment de la compilation. Pour chaque itérateur de type `Iterator`, `iterator_traits`< `Iterator`> **::iterator_category** doit être défini comme étant la balise de catégorie la plus spécifique qui décrit le comportement de l’itérateur.

Le type est identique à **iterator** \< **Iter**> **:: iterator_category** lorsque `Iter` décrit un objet pouvant servir d’itérateur de sortie.

Cette balise n’est pas paramétrable sur `value_type` ou `difference_type` pour l’itérateur, comme avec les autres balises d’itérateur, car les itérateurs de sortie n’ont pas de `value_type` ou `difference_type`.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [iterator_traits](../standard-library/iterator-traits-struct.md) ou [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) `iterator_tag` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
