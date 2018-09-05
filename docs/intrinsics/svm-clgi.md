---
title: __svm_clgi | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __svm_clgi
dev_langs:
- C++
helpviewer_keywords:
- CLGI instruction
- __svm_clgi intrinsic
ms.assetid: 6640f5ab-9472-46f9-a042-e15c4f1ff858
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e2b430c0ac4a07ec9bc0a9315fb1ad8ca6563ee9
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693770"
---
# <a name="svmclgi"></a>__svm_clgi
**Section spécifique à Microsoft**  
  
 Efface l’indicateur d’interruption global.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __svm_clgi( void );  
```  
  
## <a name="remarks"></a>Notes  
 Le `__svm_clgi` fonction est équivalente à la `CLGI` instruction machine. L’indicateur d’interruption global détermine si le microprocesseur ignore, diffère ou gère les interruptions dues à des événements comme un achèvement d’e/s, une alerte de température de matériel ou une exception de débogage.  
  
 Cette fonction prend en charge l’interaction du moniteur de machines virtuelles d’un hôte avec un système d’exploitation invité et ses applications. Pour plus d’informations, recherchez dans le document, « manuelle Volume AMD64 Architecture pour le programmeur 2 : programmation du système, « 24593, révision 3.11, de numéro de document sur le [corporation d’AMD](https://developer.amd.com/resources/developer-guides-manuals/) site.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__svm_clgi`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Intrinsèques du compilateur](../intrinsics/compiler-intrinsics.md)   
 [__svm_stgi](../intrinsics/svm-stgi.md)