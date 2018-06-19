---
title: Allocation et libération de mémoire pour un BSTR | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- bstr
dev_langs:
- C++
helpviewer_keywords:
- BSTRs, memory allocation
- memory deallocation, string memory
- memory [C++], releasing
- memory allocation, BSTRs
- memory deallocation, BSTR memory
- strings [C++], releasing
ms.assetid: 98041e29-3442-4a02-b425-7a4a13e9cc84
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 46ab5ae9d6f0bfa98231cbc41aa4ae0d10b89537
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32358323"
---
# <a name="allocating-and-releasing-memory-for-a-bstr"></a>Allocation et libération de mémoire pour un BSTR
Lorsque vous créez `BSTR`s et les passer entre les objets COM, vous devez être attentif dans le traitement de la mémoire qu’ils utilisent afin d’éviter les fuites de mémoire. Lorsqu’un `BSTR` reste dans une interface, vous devez libérer sa mémoire lorsque vous avez terminé avec lui. Toutefois, lorsqu’un `BSTR` passe en dehors d’une interface, l’objet récepteur assume la responsabilité de la gestion de la mémoire.  
  
 En général, les règles pour l’allocation et libération de la mémoire allouée pour `BSTR`s sont les suivantes :  
  
-   Lorsque vous appelez une fonction qui attend un `BSTR` argument, vous devez allouer la mémoire pour le `BSTR` avant l’appel et libérer ensuite. Par exemple :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#192](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_1.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#193](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_2.cpp)]  
  
-   Lorsque vous appelez une fonction qui retourne un `BSTR`, vous devez libérer la chaîne vous-même. Par exemple :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#194](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_3.cpp)]  
  
     [!code-cpp[NVC_ATLMFC_Utilities#195](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_4.cpp)]  
  
-   Lorsque vous implémentez une fonction qui retourne un `BSTR`, allouez la chaîne mais ne le libérez pas. La réception de la fonction libère la mémoire. Par exemple :  
  
     [!code-cpp[NVC_ATLMFC_Utilities#196](../atl-mfc-shared/codesnippet/cpp/allocating-and-releasing-memory-for-a-bstr_5.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Chaînes (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT::AllocSysString](../atl-mfc-shared/reference/cstringt-class.md#allocsysstring)   
 [SysAllocString](https://msdn.microsoft.com/library/windows/desktop/ms221458.aspx)   
 [SysFreeString](https://msdn.microsoft.com/library/windows/desktop/ms221481.aspx)

