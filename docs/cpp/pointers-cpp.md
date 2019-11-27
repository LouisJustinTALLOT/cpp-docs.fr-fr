---
title: Pointeurs (C++)
ms.date: 11/19/2019
description: À propos des pointeurs bruts et des pointeurs intelligents dans Microsoft C++.
helpviewer_keywords:
- pointers (C++)
ms.assetid: 595387c5-8e58-4670-848f-344c7caf985e
ms.openlocfilehash: 21dcc55048e9e378f370f25254e1910b05e49d69
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246422"
---
# <a name="pointers-c"></a>Pointeurs (C++)

Un pointeur est une variable qui stocke l’adresse mémoire d’un objet. Les pointeurs sont largement utilisés à la fois en C++ C et à trois fins principales :

- pour allouer de nouveaux objets sur le tas,
- pour passer des fonctions à d’autres fonctions
- pour itérer au sein des éléments dans des tableaux ou d’autres structures de données.

Dans la programmation de style C, les *pointeurs bruts* sont utilisés pour tous ces scénarios. Toutefois, les pointeurs bruts sont la source de nombreuses erreurs de programmation graves. Par conséquent, leur utilisation est fortement déconseillée, sauf dans les cas où ils offrent un gain de performances significatif et il n’y a aucune ambiguïté quant au pointeur *propriétaire* qui est responsable de la suppression de l’objet. Moderne C++ fournit des *pointeurs intelligents* pour l’allocation d’objets, des *itérateurs* pour parcourir les structures de données et des *expressions lambda* pour passer des fonctions. En utilisant ces fonctionnalités de langage et de bibliothèque plutôt que des pointeurs bruts, vous rendez votre programme plus sûr, plus facile à déboguer et plus simple à comprendre et à gérer. Pour plus d’informations, consultez [pointeurs intelligents](smart-pointers-modern-cpp.md), [itérateurs](../standard-library/iterators.md)et [expressions lambda](lambda-expressions-in-cpp.md) .

## <a name="in-this-section"></a>Dans cette section

- [Pointeurs bruts](raw-pointers.md)
- [Pointeurs const et volatile](const-and-volatile-pointers.md)
- [opérateurs New et Delete](new-and-delete-operators.md)
- [Pointeurs intelligents](smart-pointers-modern-cpp.md)
- [Comment : créer et utiliser des instances unique_ptr](how-to-create-and-use-unique-ptr-instances.md)
- [Comment : créer et utiliser des instances shared_ptr](how-to-create-and-use-shared-ptr-instances.md)
- [Comment : créer et utiliser des instances weak_ptr](how-to-create-and-use-weak-ptr-instances.md)
- [Comment : créer et utiliser des instances CComPtr et CComQIPtr](how-to-create-and-use-ccomptr-and-ccomqiptr-instances.md)

## <a name="see-also"></a>Voir aussi

[Itérateurs](../standard-library/iterators.md)</br>
[Expressions lambda](lambda-expressions-in-cpp.md)
