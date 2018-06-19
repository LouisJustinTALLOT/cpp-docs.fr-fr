---
title: bidirectional_iterator_tag, struct | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xutility/std::bidirectional_iterator_tag
dev_langs:
- C++
helpviewer_keywords:
- bidirectional_iterator_tag class
- bidirectional_iterator_tag struct
ms.assetid: 9ac06066-b8ae-44b6-bee4-b05855f6a31a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 108397f6c3c3c088839230f2b48b505300149345
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844391"
---
# <a name="bidirectionaliteratortag-struct"></a>bidirectional_iterator_tag, struct

Classe qui fournit un type de retour pour la fonction **iterator_category** représentant un itérateur bidirectionnel.

## <a name="syntax"></a>Syntaxe

```cpp
struct bidirectional_iterator_tag    : public forward_iterator_tag {};
```

## <a name="remarks"></a>Notes

Les classes de balise de catégorie sont utilisées comme balises de compilation pour la sélection de l’algorithme. La fonction de modèle doit rechercher la catégorie la plus spécifique de son argument d’itérateur, pour pouvoir utiliser l’algorithme le plus efficace au moment de la compilation. Pour chaque itérateur de type `Iterator`, `iterator_traits`< `Iterator`>:: **iterator_category** doit être défini comme étant la balise de catégorie la plus spécifique qui décrit le comportement de l’itérateur.

Le type est identique à **iterator**\< **Iter**>:: **iterator_category** quand **Iter** décrit un objet pouvant servir d’itérateur bidirectionnel.

## <a name="example"></a>Exemple

Consultez [random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md) pour obtenir un exemple d’utilisation de `bidirectional_iterator_tag`.

## <a name="requirements"></a>Spécifications

**En-tête :** \<iterator>

**Espace de noms :** std

## <a name="see-also"></a>Voir aussi

[forward_iterator_tag, struct](../standard-library/forward-iterator-tag-struct.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Informations de référence sur la bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)<br/>
