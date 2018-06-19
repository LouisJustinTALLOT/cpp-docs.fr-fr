---
title: 'Gestion de la mémoire : Exemples | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 84bc2ce7c084f2951d63eee546df3bf70a2ba1fe
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347189"
---
# <a name="memory-management-examples"></a>Gestion de la mémoire : exemples
Cet article décrit la façon dont MFC effectue les allocations de frame et les allocations de tas pour chacun des trois types d’allocations de mémoire :  
  
-   [Un tableau d’octets](#_core_allocation_of_an_array_of_bytes)  
  
-   [Une structure de données](#_core_allocation_of_a_data_structure)  
  
-   [Un objet](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> Allocation d’un tableau d’octets  
  
#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Pour allouer un tableau d’octets sur le frame  
  
1.  Définissez le tableau comme indiqué par le code suivant. Le tableau est automatiquement supprimé et sa mémoire récupérée lorsque la variable tableau quitte sa portée.  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]  
  
#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Pour allouer un tableau d’octets (ou n’importe quel type de données primitif) sur le tas  
  
1.  Utilisez le **nouveau** opérateur avec la syntaxe tableau indiquée dans cet exemple :  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]  
  
#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Pour libérer les tableaux à partir du tas  
  
1.  Utilisez le **supprimer** opérateur comme suit :  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> Allocation d’une Structure de données  
  
#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Pour allouer une structure de données sur le frame  
  
1.  Définissez la variable de structure comme suit :  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]  
  
     La mémoire occupée par la structure est récupérée lors de sa sortie à sa portée.  
  
#### <a name="to-allocate-data-structures-on-the-heap"></a>Pour les structures de données sur le tas  
  
1.  Utilisez **nouveau** pour allouer les structures de données sur le tas et **supprimer** à libérer, comme indiqué dans les exemples suivants :  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> Allocation d’un objet  
  
#### <a name="to-allocate-an-object-on-the-frame"></a>Pour allouer un objet sur le frame  
  
1.  Déclarez l’objet comme suit :  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]  
  
     Le destructeur de l’objet est automatiquement appelé lorsque l’objet quitte sa portée.  
  
#### <a name="to-allocate-an-object-on-the-heap"></a>Pour allouer un objet sur le tas  
  
1.  Utilisez le **nouveau** opérateur, qui retourne un pointeur vers l’objet, pour allouer des objets sur le tas. Utilisez le **supprimer** opérateur pour les supprimer.  
  
     Les exemples de tas et le frame suivants supposent que le `CPerson` constructeur n’accepte aucun argument.  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]  
  
     Si l’argument pour le `CPerson` constructeur est un pointeur vers `char`, l’instruction pour l’allocation de frame est :  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]  
  
     L’instruction pour l’allocation de tas est :  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire : allocation de tas](../mfc/memory-management-heap-allocation.md)

