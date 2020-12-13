---
description: 'En savoir plus sur : allocation et libération de mémoire pour un BSTR'
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
ms.openlocfilehash: 2b027bdc5615578bc785075ae7e8709e2b3a7ea5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97142661"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Allocation et libération de mémoire pour un BSTR

Lorsque vous créez `BSTR` des et que vous les transmettez entre des objets com, vous devez veiller à traiter la mémoire qu’ils utilisent afin d’éviter les fuites de mémoire. Quand un `BSTR` reste dans une interface, vous devez libérer sa mémoire lorsque vous n’en avez plus besoin. Toutefois, lorsqu’un `BSTR` passe en dehors d’une interface, l’objet récepteur assume la responsabilité de sa gestion de la mémoire.

En général, les règles d’allocation et de libération de mémoire allouée aux `BSTR` s sont les suivantes :

- Quand vous appelez une fonction qui attend un `BSTR` argument, vous devez allouer la mémoire pour `BSTR` avant l’appel et la libérer ultérieurement. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]

- Quand vous appelez une fonction qui retourne un `BSTR` , vous devez libérer la chaîne vous-même. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]

   [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]

- Lorsque vous implémentez une fonction qui retourne un `BSTR` , allouez la chaîne, mais ne la libérez pas. La réception de la fonction libère la mémoire. Par exemple :

   [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]

## <a name="see-also"></a>Voir aussi

[Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
[CStringT :: AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)<br/>
[SysAllocString](/windows/win32/api/oleauto/nf-oleauto-sysallocstring)<br/>
[SysFreeString](/windows/win32/api/oleauto/nf-oleauto-sysfreestring)
