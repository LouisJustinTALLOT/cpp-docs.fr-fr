---
title: __halt | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __halt
- __halt_cpp
dev_langs:
- C++
helpviewer_keywords:
- __halt intrinsic
- HLT instruction
ms.assetid: a074f44a-101c-45a5-8a5e-cfd223c34002
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a36790eb1df098e6f663a30894c29a9ea14587b0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33327201"
---
# <a name="halt"></a>__halt
**Section spécifique à Microsoft**  
  
 Arrête le microprocesseur jusqu'à ce qu’une interruption activée, une interruption non masquable (NMI) ou une réinitialisation se produit.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __halt( void );  
```  
  
## <a name="requirements"></a>Spécifications  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__halt`|x86, [!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Le `__halt` fonction est équivalente à la `HLT` instruction machine et est disponible uniquement en mode noyau. Pour plus d’informations, recherchez le document, « manuel du développeur du logiciel de l’Architecture Intel, Volume 2 : Instruction Set référence, » à la [Intel Corporation](http://go.microsoft.com/fwlink/p/?linkid=127) site.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)