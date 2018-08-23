---
title: __outdwordstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outdwordstring
dev_langs:
- C++
helpviewer_keywords:
- outsd instruction
- __outdwordstring intrinsic
- rep outsd instruction
ms.assetid: 55b31a65-aab7-4b5c-b61d-d9e2fb0c497a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: adc104e3325a2a9fda922f8ef32aa84982f35366
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "42540025"
---
# <a name="outdwordstring"></a>__outdwordstring
**Section spécifique à Microsoft**  
  
 Génère le `rep outsd` instruction, qui envoie `Count` mots doubles en commençant à `Buffer` le port d’e/s spécifié par `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outdwordstring(   
   unsigned short Port,   
   unsigned long* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
 [in] `Port`  
 Le port pour envoyer les données.  
  
 [in] `Buffer`  
 Un pointeur vers les données seront envoyés le port spécifié.  
  
 [in] `Count`  
 Le nombre de mots doubles à envoyer.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__outdwordstring`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)