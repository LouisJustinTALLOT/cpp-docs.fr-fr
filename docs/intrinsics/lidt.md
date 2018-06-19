---
title: __lidt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __lidt
- __lidt_cpp
dev_langs:
- C++
helpviewer_keywords:
- LIDT instruction
- __lidt intrinsic
ms.assetid: 8298d25d-a19e-4900-828d-6b3b09841882
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8dd972d2a7e8d75f7149b2dc2766ffca86b0b2e5
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33326509"
---
# <a name="lidt"></a>__lidt
**Section spécifique à Microsoft**  
  
 Charge le Registre des interruptions table descripteur (IDTR) avec la valeur de l’emplacement de mémoire spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __lidt(  
     void *Source);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `Source`|Pointeur vers la valeur doit être copié vers le IDTR.|  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__lidt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le `__lidt` fonction est équivalente à la `LIDT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document, « manuel du développeur du logiciel de l’Architecture Intel, Volume 2 : Instruction Set référence, » à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__sidt](../intrinsics/sidt.md)