---
title: . FPO | Documents Microsoft
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
ms.openlocfilehash: df5185c0dc699764427989b2f46345d90ded1729
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32055929"
---
# <a name="fpo"></a>.FPO
La barre d’outils. La directive de FPO contrôle l’émission d’enregistrements de débogage à la section ou du segment de .debug$ F.  
  
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
 Nombre de variables locales, une valeur non signée 32 bits.  
  
 `cdwParams`  
 Taille des paramètres dans les valeurs de type DWORD, une valeur non signé 16 bits.  
  
 *cbProlog*  
 Nombre d’octets dans le code de prologue de fonction, une valeur non signé 8 bits.  
  
 `cbRegs`  
 Registres enregistrés des numéros.  
  
 `fUseBP`  
 Indique si le registre EBP a été alloué. 0 ou 1.  
  
 *cbFrame*  
 Indique le type de frame.  Consultez [FPO_DATA](http://msdn.microsoft.com/library/windows/desktop/ms679352) pour plus d’informations.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)