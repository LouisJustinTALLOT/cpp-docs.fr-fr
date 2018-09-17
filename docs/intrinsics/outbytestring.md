---
title: __outbytestring | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __outbytestring
dev_langs:
- C++
helpviewer_keywords:
- rep outsb instruction
- __outbytestring intrinsic
- outsb instruction
ms.assetid: c9150661-9c18-427f-bae8-710bba6ed78c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 54a816bd4df165b3df9de723560192ac9072b29c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45718833"
---
# <a name="outbytestring"></a>__outbytestring
**Section spécifique à Microsoft**  
  
 Génère le `rep outsb` instruction, qui envoie le premier `Count` octets de données vers lequel pointe `Buffer` vers le port spécifié par `Port`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
void __outbytestring(   
   unsigned short Port,   
   unsigned char* Buffer,   
   unsigned long Count   
);  
```  
  
#### <a name="parameters"></a>Paramètres  
*Port*<br/>
[in] Le port pour envoyer les données.  
  
*mémoire tampon*<br/>
[in] Les données seront envoyés le port spécifié.  
  
*Nombre*<br/>
[in] Le nombre d’octets de données à envoyer.  
  
## <a name="requirements"></a>Configuration requise  
  
|Intrinsèque|Architecture|  
|---------------|------------------|  
|`__outbytestring`|x86, x64|  
  
 **Fichier d’en-tête** \<intrin.h >  
  
## <a name="remarks"></a>Notes  
 Cette routine est disponible uniquement en tant qu'intrinsèque.  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [compilateur, fonctions intrinsèques](../intrinsics/compiler-intrinsics.md)