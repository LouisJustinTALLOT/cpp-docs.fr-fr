---
title: __sidt | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __sidt
dev_langs:
- C++
helpviewer_keywords:
- sidt instruction
- __sidt intrinsic
ms.assetid: 01e83d14-6e63-4dea-8f64-5a0339d69641
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 96d20916210b0fe55817dceb86d388a33f8e238b
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42541562"
---
# <a name="sidt"></a>__sidt
**Section spécifique à Microsoft**  
  
 Stocke la valeur de l’historique de table du descripteur d’interruption (IDTR) dans l’emplacement de mémoire spécifié.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __sidt(  
     void *Destination);  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|[in] `Destination`|Pointeur vers l’emplacement de mémoire où se trouve le IDTR.|  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__sidt`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le `__sidt` fonction est équivalente à la `SIDT` instruction machine. Pour plus d’informations, recherchez dans le document, « manuel du développeur de logiciels Architecture Intel, Volume 2 : référence de jeu d’instructions, » à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__lidt](../intrinsics/lidt.md)