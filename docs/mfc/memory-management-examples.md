---
description: 'En savoir plus sur : gestion de la mémoire : exemples'
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
ms.openlocfilehash: dcd7ba9ce5fee0af932766494f0a7afd64684e77
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222292"
---
# <a name="memory-management-examples"></a>Gestion de la mémoire : exemples

Cet article explique comment MFC effectue des allocations de frames et des allocations de tas pour chacun des trois genres types d’allocations de mémoire :

- [Tableau d’octets](#_core_allocation_of_an_array_of_bytes)

- [Structure de données](#_core_allocation_of_a_data_structure)

- [Un objet](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a> Allocation d’un tableau d’octets

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Pour allouer un tableau d’octets sur le frame

1. Définissez le tableau comme indiqué dans le code suivant. Le tableau est automatiquement supprimé et sa mémoire est récupérée lorsque la variable de tableau quitte son étendue.

   [!code-cpp[NVC_MFC_Utilities#1](codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Pour allouer un tableau d’octets (ou un type de données primitif) sur le tas

1. Utilisez l' **`new`** opérateur avec la syntaxe de tableau indiquée dans cet exemple :

   [!code-cpp[NVC_MFC_Utilities#2](codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Pour libérer les tableaux du tas

1. Utilisez l' **`delete`** opérateur comme suit :

   [!code-cpp[NVC_MFC_Utilities#3](codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a> Allocation d’une structure de données

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Pour allouer une structure de données sur le frame

1. Définissez la variable de structure comme suit :

   [!code-cpp[NVC_MFC_Utilities#4](codesnippet/cpp/memory-management-examples_4.cpp)]

   La mémoire occupée par la structure est récupérée lorsqu’elle quitte son étendue.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Pour allouer des structures de données sur le tas

1. Utilisez **`new`** pour allouer des structures de données sur le tas et les **`delete`** libérer, comme indiqué dans les exemples suivants :

   [!code-cpp[NVC_MFC_Utilities#5](codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a> Allocation d’un objet

#### <a name="to-allocate-an-object-on-the-frame"></a>Pour allouer un objet sur le frame

1. Déclarez l’objet comme suit :

   [!code-cpp[NVC_MFC_Utilities#6](codesnippet/cpp/memory-management-examples_6.cpp)]

   Le destructeur de l’objet est automatiquement appelé lorsque l’objet quitte son étendue.

#### <a name="to-allocate-an-object-on-the-heap"></a>Pour allouer un objet sur le tas

1. Utilisez l' **`new`** opérateur, qui retourne un pointeur vers l’objet, pour allouer des objets sur le tas. Utilisez l' **`delete`** opérateur pour les supprimer.

   Les exemples de tas et de frame suivants supposent que le `CPerson` constructeur ne prend pas d’arguments.

   [!code-cpp[NVC_MFC_Utilities#7](codesnippet/cpp/memory-management-examples_7.cpp)]

   Si l’argument du `CPerson` constructeur est un pointeur vers **`char`** , l’instruction pour l’allocation de frame est :

   [!code-cpp[NVC_MFC_Utilities#8](codesnippet/cpp/memory-management-examples_8.cpp)]

   L’instruction pour l’allocation du tas est la suivante :

   [!code-cpp[NVC_MFC_Utilities#9](codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire : allocation de tas](memory-management-heap-allocation.md)
