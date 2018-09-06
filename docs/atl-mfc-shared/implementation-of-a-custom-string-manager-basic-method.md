---
title: Implémentation d’un gestionnaire de chaînes personnalisé (méthode élémentaire) | Microsoft Docs
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
ms.openlocfilehash: 5c251ae73b4adaaed09e5ed654e394a130281332
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/05/2018
ms.locfileid: "43756403"
---
# <a name="implementation-of-a-custom-string-manager-basic-method"></a>Implémentation d’un gestionnaire de chaînes personnalisé (méthode élémentaire)

Le moyen le plus simple pour personnaliser le schéma d’allocation de mémoire pour les données de chaîne sont d’utiliser ATL-fourni par le `CAtlStringMgr` classe mais fournissent des routines d’allocation de mémoire de votre propre. Le constructeur de `CAtlStringMgr` accepte un seul paramètre : un pointeur vers un `IAtlMemMgr` objet. `IAtlMemMgr` est une classe de base abstraite qui fournit une interface générique à un segment de mémoire. À l’aide de la `IAtlMemMgr` interface, le `CAtlStringMgr` alloue, réalloue et libère la mémoire utilisée pour stocker les données de chaîne. Vous pouvez implémenter la `IAtlMemMgr` interface vous-même, ou utilisez une des cinq classes de gestionnaire de mémoire fournis par ATL. Les gestionnaires de mémoire fournis par ATL ne font qu’envelopper les fonctions d’allocation mémoire existant :

- [CCRTHeap](../atl/reference/ccrtheap-class.md) encapsule les fonctions de tas CRT standards ([malloc](../c-runtime-library/reference/malloc.md), [gratuit](../c-runtime-library/reference/free.md), et [realloc](../c-runtime-library/reference/realloc.md))

- [CWin32Heap](../atl/reference/cwin32heap-class.md) encapsule un segment de mémoire Win32 gérer, à l’aide [HeapAlloc](/windows/desktop/api/heapapi/nf-heapapi-heapalloc), [HeapFree](/windows/desktop/api/heapapi/nf-heapapi-heapfree), et [HeapRealloc](/windows/desktop/api/heapapi/nf-heapapi-heaprealloc)

- [CLocalHeap](../atl/reference/clocalheap-class.md) encapsule les API Win32 : [LocalAlloc](/windows/desktop/api/winbase/nf-winbase-localalloc), [LocalFree](/windows/desktop/api/winbase/nf-winbase-localfree), et [LocalRealloc](/windows/desktop/api/winbase/nf-winbase-localrealloc)

- [CGlobalHeap](../atl/reference/cglobalheap-class.md) encapsule les API Win32 : [GlobalAlloc](/windows/desktop/api/winbase/nf-winbase-globalalloc), [GlobalFree](/windows/desktop/api/winbase/nf-winbase-globalfree), et [GlobalRealloc](/windows/desktop/api/winbase/nf-winbase-globalrealloc).

- [CComHeap](../atl/reference/ccomheap-class.md) encapsule les API d’allocateur de tâche de COM : [CoTaskMemAlloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemalloc), [CoTaskMemFree](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemfree), et [CoTaskMemRealloc](/windows/desktop/api/combaseapi/nf-combaseapi-cotaskmemrealloc)

Pour les besoins de gestion de la mémoire de chaîne, la classe la plus utile est `CWin32Heap` , car il permet de créer plusieurs segments de mémoire indépendants. Par exemple, si vous souhaitez utiliser un segment de mémoire distinct pour les chaînes, vous pouvez procédez comme suit :

[!code-cpp[NVC_ATLMFC_Utilities#180](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_1.cpp)]

Pour utiliser le Gestionnaire de chaînes privé pour gérer la mémoire pour un `CString` variable, passez un pointeur vers le gestionnaire en tant que paramètre à la `CString` constructeur de la variable :

[!code-cpp[NVC_ATLMFC_Utilities#181](../atl-mfc-shared/codesnippet/cpp/implementation-of-a-custom-string-manager-basic-method_2.cpp)]

## <a name="see-also"></a>Voir aussi

[Gestion de la mémoire avec CStringT](../atl-mfc-shared/memory-management-with-cstringt.md)

