---
description: 'En savoir plus sur : implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)'
title: Implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)
ms.date: 11/04/2016
helpviewer_keywords:
- IAtlStringMgr class, using
ms.assetid: eac5d13e-cbb4-4e82-b01e-f5f2dbcb962a
ms.openlocfilehash: e532312edff16229b6b91eef1d95ae764b70eb5e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97166952"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implémentation d’un gestionnaire de chaînes personnalisé (méthode de base)

Le moyen le plus simple de personnaliser le schéma d’allocation de mémoire pour les données de type chaîne consiste à utiliser la classe fournie par ATL, `CAtlStringMgr` mais à fournir vos propres routines d’allocation de mémoire. Le constructeur pour `CAtlStringMgr` accepte un seul paramètre : un pointeur vers un `IAtlMemMgr` objet. `IAtlMemMgr` est une classe de base abstraite qui fournit une interface générique à un segment de mémoire. À l’aide de l' `IAtlMemMgr` interface, `CAtlStringMgr` alloue, réalloue et libère la mémoire utilisée pour stocker les données de chaîne. Vous pouvez implémenter l' `IAtlMemMgr` interface vous-même ou utiliser l’une des cinq classes du gestionnaire de mémoire fournies par ATL. Les gestionnaires de mémoire fournis par ATL encapsulent simplement les fonctionnalités d’allocation de mémoire existantes :

- [CCRTHeap](../atl/reference/ccrtheap-class.md) Encapsule les fonctions de tas CRT standard ([malloc](../c-runtime-library/reference/malloc.md), [Free](../c-runtime-library/reference/free.md)et [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) Encapsule un handle de tas Win32 à l’aide de [HeapAlloc](/windows/win32/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/win32/api/heapapi/nf-heapapi-heapfree)et [HeapRealloc](/windows/win32/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) Encapsule les API Win32 : [LocalAlloc](/windows/win32/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/win32/api/winbase/nf-winbase-localfree)et [LocalRealloc](/windows/win32/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) Encapsule les API Win32 : [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/win32/api/winbase/nf-winbase-globalfree)et [GlobalReAlloc](/windows/win32/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) Encapsule les API d’allocateur de tâche COM : [CoTaskMemAlloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemfree)et [CoTaskMemRealloc](/windows/win32/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Dans le cadre de la gestion de la mémoire de chaînes, la classe la plus utile est `CWin32Heap` parce qu’elle vous permet de créer plusieurs tas indépendants. Par exemple, si vous souhaitez utiliser un tas distinct uniquement pour les chaînes, vous pouvez effectuer les opérations suivantes :

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Pour utiliser ce gestionnaire de chaînes privé pour gérer la mémoire pour une `CString` variable, transmettez un pointeur vers le gestionnaire en tant que paramètre du `CString` constructeur de la variable :

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)
