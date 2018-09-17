---
title: __outwordstring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outwordstring
dev_langs:
- C++
helpviewer_keywords:
- rep outsw instruction
- __outwordstring intrinsic
- outsw instruction
ms.assetid: b470c7a0-1de9-4370-886a-b2c3a1f842f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3c49f76175ced83fb9a9b7e72e1c1fc7dbb68e20
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720666"
---
# <a name="outwordstring"></a>__outwordstring
**Section spécifique à Microsoft**  
  
 Génère le `rep outsw` instruction, qui envoie `Count` mots commençant `Buffer` le port d’e/s spécifié par `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outwordstring(   
   unsigned short Port,   
   unsigned short* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*Port*<br/>
[in] Le port pour envoyer les données.  
  
*mémoire tampon*<br/>
[in] Un pointeur vers les données seront envoyés le port spécifié.  
  
*Nombre*<br/>
[in] Le nombre de mots à envoyer.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__outwordstring`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)