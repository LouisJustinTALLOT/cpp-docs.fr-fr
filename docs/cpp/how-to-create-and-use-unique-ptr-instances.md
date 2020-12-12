---
description: 'En savoir plus sur : Comment : créer et utiliser des instances unique_ptr'
title: 'Procédure : Créer et utiliser des instances unique_ptr'
ms.custom: how-to
ms.date: 11/19/2018
ms.topic: conceptual
ms.assetid: 9a373030-e587-452f-b9a5-c5f9d58b7673
ms.openlocfilehash: a53b3a9704c62803b50c9bde2c7db70c190a8008
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97268663"
---
# <a name="how-to-create-and-use-unique_ptr-instances"></a>Procédure : Créer et utiliser des instances unique_ptr

Un [unique_ptr](../standard-library/unique-ptr-class.md) ne partage pas son pointeur. Il ne peut pas être copié vers un autre `unique_ptr` , passé par valeur à une fonction ou utilisé dans un algorithme de la bibliothèque standard C++ qui requiert que des copies soient effectuées. Un `unique_ptr` peut uniquement être déplacé. Cela signifie que la propriété de la ressource mémoire est transférée à un autre `unique_ptr` et que le `unique_ptr` d'origine ne le possède plus. Il est recommandé de restreindre un objet à un seul propriétaire, car la multiplicité des propriétaires ajoute de la complexité à la logique du programme. Par conséquent, lorsque vous avez besoin d’un pointeur intelligent pour un objet C++ ordinaire, utilisez `unique_ptr` et, lorsque vous construisez un `unique_ptr` , utilisez la fonction d’assistance [make_unique](../standard-library/memory-functions.md#make_unique) .

Le diagramme suivant illustre le transfert de propriété entre deux instances `unique_ptr`.

![Déplacement de la propriété d’un PTR&#95;unique](media/unique_ptr.png "Déplacement de la propriété d’un PTR&#95;unique")

`unique_ptr` est défini dans l' `<memory>` en-tête de la bibliothèque C++ standard. Elle est aussi efficace qu’un pointeur brut et peut être utilisée dans les conteneurs de la bibliothèque standard C++. L’ajout d' `unique_ptr` instances aux conteneurs de la bibliothèque standard C++ est efficace, car le constructeur de déplacement du `unique_ptr` élimine la nécessité d’une opération de copie.

## <a name="example-1"></a>Exemple 1

L'exemple suivant montre comment créer des instances `unique_ptr` et les passer entre des fonctions.

[!code-cpp[stl_smart_pointers#210](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_1.cpp)]

Ces exemples illustrent cette caractéristique de base de `unique_ptr` : il peut être déplacé, mais pas copié. Le « déplacement » transfère la propriété à un nouvel `unique_ptr` et réinitialise l'ancien `unique_ptr`.

## <a name="example-2"></a>Exemple 2

L'exemple suivant montre comment créer des instances `unique_ptr` et les utiliser dans un vecteur.

[!code-cpp[stl_smart_pointers#211](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_2.cpp)]

Dans la boucle for de plage, remarquez que `unique_ptr` est passé par référence. Si vous essayez d'effectuer un passage par valeur ici, le compilateur génère une erreur, car le constructeur de copie `unique_ptr` est supprimé.

## <a name="example-3"></a>Exemple 3

L'exemple suivant montre comment initialiser un `unique_ptr` qui est un membre de classe.

[!code-cpp[stl_smart_pointers#212](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_3.cpp)]

## <a name="example-4"></a>Exemple 4

Vous pouvez utiliser [make_unique](../standard-library/memory-functions.md#make_unique) pour créer un `unique_ptr` dans un tableau, mais vous ne pouvez pas utiliser `make_unique` pour initialiser les éléments du tableau.

[!code-cpp[stl_smart_pointers#213](codesnippet/CPP/how-to-create-and-use-unique-ptr-instances_4.cpp)]

Pour plus d’exemples, consultez [make_unique](../standard-library/memory-functions.md#make_unique).

## <a name="see-also"></a>Voir aussi

[Pointeurs intelligents (Modern C++)](smart-pointers-modern-cpp.md)<br/>
[make_unique](../standard-library/memory-functions.md#make_unique)
