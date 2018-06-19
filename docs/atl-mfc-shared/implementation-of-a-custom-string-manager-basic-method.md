---
title: Implémentation d’un gestionnaire de chaîne personnalisé (méthode élémentaire) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 259f9533747b266f0be0a782cdc94c98f167d2d2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32355723"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)
Le moyen le plus simple pour personnaliser la méthode d’allocation de mémoire pour les données de chaîne fournie par le ATL **CAtlStringMgr** classe, qui fournissent des routines d’allocation de mémoire de votre propre. Le constructeur de **CAtlStringMgr** accepte un seul paramètre : un pointeur vers un `IAtlMemMgr` objet. `IAtlMemMgr` est une classe de base abstraite qui fournit une interface générique à un segment de mémoire. À l’aide de la `IAtlMemMgr` interface, le **CAtlStringMgr** alloue, réalloue et libère la mémoire utilisée pour stocker les données de chaîne. Vous pouvez implémenter la `IAtlMemMgr` interface vous-même, ou utiliser l’un des cinq classes de gestionnaire de mémoire fournis par ATL. Les gestionnaires de mémoire fournis par ATL englobent simplement les fonctions d’allocation mémoire existant :  
  
-   [CCRTHeap](../atl/reference/ccrtheap-class.md) encapsule les fonctions de tas CRT standards ([malloc](../c-runtime-library/reference/malloc.md), [libre](../c-runtime-library/reference/free.md), et [realloc](../c-runtime-library/reference/realloc.md))  
  
-   [CWin32Heap](../atl/reference/cwin32heap-class.md) encapsule un segment de mémoire Win32 gérer, à l’aide [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597), [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701), et [HeapRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366704)  
  
-   [CLocalHeap](../atl/reference/clocalheap-class.md) encapsule les API Win32 : [LocalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366723), [LocalFree](http://msdn.microsoft.com/library/windows/desktop/aa366730), et [LocalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366742)  
  
-   [CGlobalHeap](../atl/reference/cglobalheap-class.md) encapsule les API Win32 : [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574), [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579), et [GlobalRealloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
-   [CComHeap](../atl/reference/ccomheap-class.md) encapsule les API d’allocation de tâches COM : [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), et [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280)  
  
 À des fins de gestion de la mémoire de chaîne, la classe la plus utile est `CWin32Heap` , car il permet de créer plusieurs segments de mémoire indépendants. Par exemple, si vous souhaitez utiliser un segment de mémoire distinct pour les chaînes, vous pouvez procédez comme suit :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]  
  
 Pour utiliser le Gestionnaire de chaînes privé pour gérer la mémoire pour un `CString` variable, passez un pointeur vers le gestionnaire en tant que paramètre à la `CString` constructeur de la variable :  
  
 [!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

