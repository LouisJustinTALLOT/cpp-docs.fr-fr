---
title: EQU | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EQU
dev_langs:
- C++
helpviewer_keywords:
- EQU directive
ms.assetid: 96db466a-1eab-45bd-a3c2-5a59bd754eab
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1d7678cac4c480934fe9f6dd9816e636481c2d64
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050748"
---
# <a name="equ"></a>EQU
La première directive affecte la valeur numérique de *expression* à *nom*.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      name EQU expression  
name EQU <text>  
```  
  
## <a name="remarks"></a>Notes  
 Le *nom* ne peut pas être redéfini plus tard.  
  
 La deuxième affecte la directive spécifiée *texte* à *nom*. Le *nom* peuvent être affectés à un autre *texte* plus tard. Consultez [TEXTEQU](../../assembler/masm/textequ.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)