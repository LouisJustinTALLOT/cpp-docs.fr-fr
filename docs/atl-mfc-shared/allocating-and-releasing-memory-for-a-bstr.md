---
title: Allocation et libération de mémoire pour un BSTR
ms.date: 11/04/2016
f1_keywords:
- bstr
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
ms.openlocfilehash: 5d21134b85013f9a8ae508590f1a8db0c2e7a7e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668570"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Allocation et libération de mémoire pour un BSTR

Lorsque vous créez `BSTR`s et les passer entre les objets COM, vous devez prendre en charge la mémoire qu’ils utilisent afin d’éviter les fuites de mémoire. Quand un `BSTR` reste dans une interface, vous devez libérer sa mémoire lorsque vous avez terminé avec lui. Toutefois, quand un `BSTR` passe en dehors d’une interface, l’objet de réception prend la responsabilité pour sa gestion de la mémoire.

En règle générale, les règles pour l’allocation et libération de la mémoire allouée pour `BSTR`s sont les suivantes :

- Lorsque vous appelez une fonction qui attend un `BSTR` argument, vous devez allouer la mémoire pour le `BSTR` avant l’appel et mise en production par la suite. Exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Lorsque vous appelez une fonction qui retourne un `BSTR`, vous devez libérer la chaîne vous-même. Exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Lorsque vous implémentez une fonction qui retourne un `BSTR`, allouez la chaîne mais ne le libérez pas. La réception la fonction libère la mémoire. Exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-sysfreestring)

