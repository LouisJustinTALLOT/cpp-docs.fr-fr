---
title: jitintrinsic | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- jitintrinsic
- jitintrinsic_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], jitintrinsic
- jitintrinsic __declspec modifier
ms.assetid: 23dbe416-7ef6-442b-b16d-9a81aab04fa6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 71cd88882ea104275e4c1a43ccf05494a859d303
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32418752"
---
# <a name="jitintrinsic"></a>jitintrinsic
Marque la fonction comme significative pour le CLR (Common Langage Runtime) 64 bits. Ceci est utilisé pour certaines fonctions dans les bibliothèques fournies par Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
__declspec(jitintrinsic)  
```  
  
## <a name="remarks"></a>Notes  
 `jitintrinsic` ajoute un MODOPT (<xref:System.Runtime.CompilerServices.IsJitIntrinsic>) à la signature de la fonction.  
  
 Il est déconseillé aux utilisateurs d'avoir recours à ce modificateur `__declspec`, car des résultats inattendus peuvent survenir.  
  
## <a name="see-also"></a>Voir aussi  
 [__declspec](../cpp/declspec.md)   
 [Mots clés](../cpp/keywords-cpp.md)