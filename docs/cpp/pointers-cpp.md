---
title: Pointeurs (C++)
ms.date: 11/19/2019
description: À propos des pointeurs bruts et des pointeurs intelligents dans Microsoft C.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 485cee667fa288bff76fdeac7c9f229355c276d1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371917"
---
# <a name="pointers-c"></a>Pointeurs (C++)

Un pointeur est une variable qui stocke l’adresse mémoire d’un objet. Les pointeurs sont largement utilisés en C et en CMD à trois fins principales :

- d’allouer de nouveaux objets sur le tas,
- de transmettre des fonctions à d’autres fonctions
- d’itérer sur des éléments dans des tableaux ou d’autres structures de données.

Dans la programmation de style C, *les pointeurs bruts* sont utilisés pour tous ces scénarios. Cependant, les pointeurs bruts sont la source de nombreuses erreurs de programmation graves. Par conséquent, leur utilisation est fortement déconseillée, sauf lorsqu’ils offrent un avantage de performance important et il n’y a aucune ambiguïté quant à quel pointeur est le *pointeur propriétaire* qui est responsable de la suppression de l’objet. Le CMD moderne fournit des *pointeurs intelligents* pour l’attribution d’objets, *d’itérateurs* pour la traversée des structures de données et des *expressions lambda* pour les fonctions de passage. En utilisant ces installations de langue et de bibliothèque au lieu de pointeurs bruts, vous rendrez votre programme plus sûr, plus facile à débobli, et plus simple à comprendre et à entretenir. Voir [les pointeurs intelligents](smart-pointers-modern-cpp.md), les [itérateurs](../standard-library/iterators.md)et les expressions [Lambda](lambda-expressions-in-cpp.md) pour plus d’informations.

## <a name="in-this-section"></a>Contenu de cette section

- [Pointeurs bruts](raw-pointers.md)
- [Const et pointeurs volatils](const-and-volatile-pointers.md)
- [nouveaux opérateurs et supprimer](new-and-delete-operators.md)
- [Pointeurs intelligents](smart-pointers-modern-cpp.md)
- [Comment : Créer et utiliser unique_ptr instances](how-to-create-and-use-unique-ptr-instances.md)
- [Comment : Créer et utiliser shared_ptr instances](how-to-create-and-use-shared-ptr-instances.md)
- [Comment : Créer et utiliser weak_ptr instances](how-to-create-and-use-weak-ptr-instances.md)
- [Comment : Créer et utiliser les instances CComPtr et CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Voir aussi

[Iterators](../standard-library/iterators.md)</br>
[Expressions lambda](lambda-expressions-in-cpp.md)
