---
title: Suppression de tous les objets d’une collection CObject
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], deleting in collections
- objects in CObject collections, deleting
- CObject class [MFC], deleting in collection
- collection classes [MFC], deleting all objects
- CObject class collection
- objects in CObject collections
- collection classes [MFC], shared objects
ms.assetid: 81d2c1d5-a0a5-46e1-8ab9-82b45cf7afd2
ms.openlocfilehash: 5aac324b6af50db019c2a4b55b26a612cc081894
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225070"
---
# <a name="deleting-all-objects-in-a-cobject-collection"></a>Suppression de tous les objets d’une collection CObject

Cet article explique comment supprimer tous les objets d’une collection (sans supprimer l’objet collection lui-même).

Pour supprimer tous les objets d’une collection de `CObject` s (ou d’objets dérivés de `CObject` ), vous utilisez l’une des techniques d’itération décrites dans l’article [accès à tous les membres d’une collection](accessing-all-members-of-a-collection.md) pour supprimer chaque objet.

> [!CAUTION]
> Les objets au sein des collections peuvent être partagés. Autrement dit, la collection conserve un pointeur vers l'objet, mais d'autres parties du programme peuvent également avoir des pointeurs sur le même objet. Vous devez alors veiller à ne pas supprimer un objet qui est partagé jusqu'à ce que toutes les parties aient fini d'utiliser l'objet.

Cet article explique comment supprimer des objets dans :

- [Une liste](#_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject)

- [Un tableau](#_core_to_delete_all_elements_in_an_array)

- [Un mappage](#_core_to_delete_all_elements_in_a_map)

#### <a name="to-delete-all-objects-in-a-list-of-pointers-to-cobject"></a><a name="_core_to_delete_all_objects_in_a_list_of_pointers_to_cobject"></a>Pour supprimer tous les objets d’une liste de pointeurs vers CObject

1. Utilisez `GetHeadPosition` et `GetNext` pour parcourir la liste.

1. Utilisez l' **`delete`** opérateur pour supprimer chaque objet tel qu’il est trouvé dans l’itération.

1. Appelez la fonction `RemoveAll` pour supprimer tous les éléments dans la liste une fois que les objets associés à ces éléments ont été supprimés.

L'exemple suivant montre comment supprimer tous les objets d'une liste d'objets `CPerson`. Chaque objet de la liste est un pointeur vers un objet `CPerson` qui a été initialement alloué sur le tas.

[!code-cpp[NVC_MFCCollections#17](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_1.cpp)]

Le dernier appel de fonction, `RemoveAll`, est une fonction membre de la liste qui supprime tous les éléments de la liste. La fonction membre `RemoveAt` supprime un élément.

Notez la différence entre supprimer l'élément d'un objet et supprimer l'élément lui-même. Supprimer un élément de la liste supprime uniquement la référence de la liste à l'objet. L'objet existe encore en mémoire. Lorsque vous supprimez un objet, il arrête d'exister et sa mémoire est libérée. Par conséquent, il est important de supprimer un élément dès que l'objet de l'élément a été supprimé afin que la liste ne tente pas d'accéder aux objets qui n'existent plus.

#### <a name="to-delete-all-elements-in-an-array"></a><a name="_core_to_delete_all_elements_in_an_array"></a>Pour supprimer tous les éléments d’un tableau

1. Utilisez `GetSize` et des valeurs d'index entiers pour effectuer une itération au sein du tableau.

1. Utilisez l' **`delete`** opérateur pour supprimer chaque élément tel qu’il est trouvé dans l’itération.

1. Appelez la fonction `RemoveAll` pour supprimer tous les éléments du tableau après leur suppression.

   Le code pour supprimer tous les éléments d'un tableau est le suivant :

   [!code-cpp[NVC_MFCCollections#18](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_2.cpp)]

Comme dans l'exemple de liste ci-dessus, vous pouvez appeler `RemoveAll` pour supprimer tous les éléments d'un tableau ou `RemoveAt` pour supprimer chaque élément un par un.

#### <a name="to-delete-all-elements-in-a-map"></a><a name="_core_to_delete_all_elements_in_a_map"></a>Pour supprimer tous les éléments d’un mappage

1. Utilisez `GetStartPosition` et `GetNextAssoc` pour effectuer une itération au sein du tableau.

1. Utilisez l' **`delete`** opérateur pour supprimer la clé et/ou la valeur de chaque élément cartographique tel qu’il est trouvé dans l’itération.

1. Appelez la fonction `RemoveAll` pour supprimer tous les éléments du mappage après leur suppression.

   Le code pour supprimer tous les éléments d’une collection `CMap` est le suivant. Chaque élément du mappage a une chaîne en tant que clé et un objet `CPerson` (dérivé de `CObject`) en tant que valeur.

   [!code-cpp[NVC_MFCCollections#19](codesnippet/cpp/deleting-all-objects-in-a-cobject-collection_3.cpp)]

Vous pouvez appeler `RemoveAll` pour supprimer tous les éléments d'un mappage ou `RemoveKey` pour supprimer chaque élément avec la clé spécifiée.

## <a name="see-also"></a>Voir aussi

[Accès à tous les membres d’une collection](accessing-all-members-of-a-collection.md)
