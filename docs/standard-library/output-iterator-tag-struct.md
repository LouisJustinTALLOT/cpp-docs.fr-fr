---
title: output_iterator_tag, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::output_iterator_tag
helpviewer_keywords:
- output_iterator_tag class
- output_iterator_tag struct
ms.assetid: c23a4331-b069-4fa0-9c3a-1c9be7095553
ms.openlocfilehash: 942e2214f42f97e262d4daf7836e8b6ced0e0ab2
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68453016"
---
# <a name="output_iterator_tag-struct"></a>output_iterator_tag, struct

Classe qui fournit un type de retour pour `iterator_category` une fonction qui représente un itérateur de sortie.

## <a name="syntax"></a>Syntaxe

output_iterator_tag {}struct ;

## <a name="remarks"></a>Notes

Les classes de balise de catégorie sont utilisées comme balises de compilation pour la sélection de l’algorithme. La fonction de modèle doit rechercher la catégorie la plus spécifique de son argument d’itérateur, pour pouvoir utiliser l’algorithme le plus efficace au moment de la compilation. Pour chaque itérateur de type `Iterator`, `iterator_traits`< `Iterator`>  **::iterator_category** doit être défini comme étant la balise de catégorie la plus spécifique qui décrit le comportement de l’itérateur.

Le type est identique à **iterator** \< **ITER**>  **:: iterator_category** lorsque `Iter` décrit un objet pouvant servir d’itérateur de sortie.

Cette balise n’est pas paramétrable sur `value_type` ou `difference_type` pour l’itérateur, comme avec les autres balises d’itérateur, car les itérateurs de sortie n’ont pas de `value_type` ou `difference_type`.

## <a name="example"></a>Exemples

Consultez [iterator_traits](../standard-library/iterator-traits-struct.md) ou [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) pour obtenir un exemple d’utilisation de `iterator_tag`.

## <a name="requirements"></a>Configuration requise

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ Standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)
