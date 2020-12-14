---
description: 'En savoir plus sur : struct input_iterator_tag'
title: input_iterator_tag, struct
ms.date: 11/04/2016
f1_keywords:
- xutility/std::input_iterator_tag
helpviewer_keywords:
- input_iterator_tag class
- input_iterator_tag struct
ms.assetid: ad68a4c6-f315-4ce1-8b74-c1fc71bd1577
ms.openlocfilehash: 92bd110af71aecfa632b8e739126698eba457019
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97231704"
---
# <a name="input_iterator_tag-struct"></a>input_iterator_tag, struct

Classe qui fournit un type de retour pour une `iterator_category` fonction qui représente un itérateur d’entrée.

## <a name="syntax"></a>Syntaxe

input_iterator_tag de struct {} ;

## <a name="remarks"></a>Notes

Les classes de balise de catégorie sont utilisées comme balises de compilation pour la sélection de l’algorithme. La fonction de modèle doit rechercher la catégorie la plus spécifique de son argument d’itérateur, pour pouvoir utiliser l’algorithme le plus efficace au moment de la compilation. Pour chaque itérateur de type `Iterator`, `iterator_traits`< `Iterator`> **::iterator_category** doit être défini comme étant la balise de catégorie la plus spécifique qui décrit le comportement de l’itérateur.

Le type est identique à **iterator** \< **Iter**> **:: iterator_category** lorsque `Iter` décrit un objet pouvant servir d’itérateur d’entrée.

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de, consultez [iterator_traits](../standard-library/iterator-traits-struct.md) ou [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) `iterator_tag` .

## <a name="requirements"></a>Spécifications

**En-tête :**\<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Informations de référence sur la bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)
