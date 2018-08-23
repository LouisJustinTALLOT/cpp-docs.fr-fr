---
title: __writemsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __writemsr
dev_langs:
- C++
helpviewer_keywords:
- Write Model Specific Register instruction
- wrmsr instruction
- __writemsr intrinsic
ms.assetid: 938b1553-51a8-4822-a818-6bed79b0fde5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d9a3fdc9b094ebb81db1bfe841d7974c5df89ca0
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539252"
---
# <a name="writemsr"></a>__writemsr
**Section spécifique à Microsoft**  
  
 Génère l’écriture dans le modèle de Registre spécifiques (`wrmsr`) instruction.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __writemsr(   
   unsigned long Register,   
   unsigned __int64 Value   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Register`  
 Le Registre spécifiques du modèle.  
  
 [in] `Value`  
 Valeur à écrire.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__writemsr`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette fonction peut uniquement être utilisée en mode noyau, et cette routine est uniquement disponible comme intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)