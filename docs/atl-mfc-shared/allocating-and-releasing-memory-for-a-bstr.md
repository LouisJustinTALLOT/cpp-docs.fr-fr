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
ms.openlocfilehash: a7a82acff959d18dcadd3a2c8516a20d60a617d3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491401"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Allocation et libération de mémoire pour un BSTR

Lorsque vous créez `BSTR`des et que vous les transmettez entre des objets com, vous devez veiller à traiter la mémoire qu’ils utilisent afin d’éviter les fuites de mémoire. Quand un `BSTR` reste dans une interface, vous devez libérer sa mémoire lorsque vous n’en avez plus besoin. Toutefois, lorsqu’un `BSTR` passe en dehors d’une interface, l’objet récepteur assume la responsabilité de sa gestion de la mémoire.

En général, les règles d’allocation et de libération de mémoire `BSTR`allouée aux s sont les suivantes:

- Quand vous appelez une fonction qui attend un `BSTR` argument, vous devez allouer la mémoire `BSTR` pour avant l’appel et la libérer ultérieurement. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Quand vous appelez une fonction qui retourne un `BSTR`, vous devez libérer la chaîne vous-même. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Lorsque vous implémentez une fonction qui retourne `BSTR`un, allouez la chaîne, mais ne la libérez pas. La réception de la fonction libère la mémoire. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)
