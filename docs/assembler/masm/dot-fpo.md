---
title: . FPO | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 234ec5bd703a390d1e2ee60e48d99d346d4aad95
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43203111"
---
# <a name="fpo"></a>.FPO
La barre d’outils. La directive FPO contrôle l’émission d’enregistrements de débogage à la section ou le segment de .debug$ F.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
FPO (  
cdwLocals  
,   
cdwParams  
,   
cbProlog  
,   
cbRegs  
,   
fUseBP  
,   
cbFrame  
)  
  
```  
  
#### <a name="parameters"></a>Paramètres  
 `cdwLocals`  
 Nombre de variables locales, une valeur 32 bits non signé.  
  
 `cdwParams`  
 Taille des paramètres dans DWORDS, une valeur 16 bits non signé.  
  
 *cbProlog*  
 Nombre d’octets dans le code de prologue de fonction, une valeur non signé 8 bits.  
  
 `cbRegs`  
 Numéro de registres enregistrés.  
  
 `fUseBP`  
 Indique si le registre EBP a été alloué. 0 ou 1.  
  
 *cbFrame*  
 Indique le type de trame.  Consultez [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)