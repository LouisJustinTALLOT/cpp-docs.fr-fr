---
title: __readmsr | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __readmsr
dev_langs:
- C++
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b3be04079de11642b2641260fdfe997d3fcb48d6
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42539438"
---
# <a name="readmsr"></a>__readmsr
**Section spécifique à Microsoft**  
  
 Génère le `rdmsr` instruction, qui lit le Registre spécifiques au modèle spécifié par `register` et retourne sa valeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__int64 __readmsr(   
   int register   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `register`  
 Le modèle spécifique s’inscrire à lire.  
  
## <a name="return-value"></a>Valeur de retour  
 La valeur dans le Registre spécifié.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__readmsr`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette fonction est uniquement disponible en mode noyau, et la routine est uniquement disponible comme intrinsèque.  
  
 Pour plus d’informations, consultez la documentation AMD.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)