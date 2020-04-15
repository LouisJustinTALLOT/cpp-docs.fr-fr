---
title: 'Gestion de la mémoire : exemples'
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367847"
---
# <a name="memory-management-examples"></a>Gestion de la mémoire : exemples

Cet article décrit comment MFC effectue des allocations de cadre et des allocations de tas pour chacun des trois types typiques d’allocations de mémoire :

- [Une gamme d’octets](#_core_allocation_of_an_array_of_bytes)

- [Une structure de données](#_core_allocation_of_a_data_structure)

- [Un objet](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Répartition d’un tableau de octets

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Pour allouer une gamme d’octets sur le cadre

1. Définissez le tableau tel qu’il est indiqué par le code suivant. Le tableau est automatiquement supprimé et sa mémoire récupérée lorsque la variable de tableau sort de sa portée.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Attribuer une gamme d’octets (ou tout type de données primitives) sur le tas

1. Utilisez le **nouvel** opérateur avec la syntaxe de tableau montrée dans cet exemple :

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Pour traiter les tableaux du tas

1. Utilisez l’opérateur **de suppression** comme suit :

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Répartition d’une structure de données

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Allouer une structure de données sur le cadre

1. Définissez la variable de structure comme suit :

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   La mémoire occupée par la structure est récupérée lorsqu’elle sort de son champ d’application.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Allouer des structures de données sur le tas

1. Utilisez **de nouveaux** pour allouer des structures de données sur le tas et **supprimer** pour les traiter, comme le montrent les exemples suivants :

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Répartition d’un objet

#### <a name="to-allocate-an-object-on-the-frame"></a>Allouer un objet sur le cadre

1. Déclarez l’objet comme suit :

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Le destructeur de l’objet est automatiquement invoqué lorsque l’objet sort de sa portée.

#### <a name="to-allocate-an-object-on-the-heap"></a>Attribuer un objet sur le tas

1. Utilisez le **nouvel** opérateur, qui renvoie un pointeur à l’objet, pour allouer des objets sur le tas. Utilisez l’opérateur **de suppression** pour les supprimer.

   Les exemples de tas et `CPerson` de cadre suivants supposent que le constructeur ne prend aucun argument.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Si l’argument `CPerson` pour le constructeur est un pointeur à **char**, la déclaration pour l’attribution de cadre est:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   La déclaration pour l’allocation de tas est la suivante:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](../mfc/memory-management-heap-allocation.md)
