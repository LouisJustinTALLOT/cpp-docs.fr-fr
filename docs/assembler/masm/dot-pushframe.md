---
title: . PUSHFRAME | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .PUSHFRAME
dev_langs:
- C++
helpviewer_keywords:
- .PUSHFRAME directive
ms.assetid: 17b123d0-4c6d-4fd2-85eb-798e8ad0a73c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66531207d21bb7e9e0c165db135f5a0c0d77e478
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32053202"
---
# <a name="pushframe"></a>.PUSHFRAME
Génère un `UWOP_PUSH_MACHFRAME` d’entrée du code de déroulement. Si le paramètre facultatif `code` est spécifié, l’entrée de code de déroulement reçoit un modificateur de 1. Sinon, le modificateur est 0.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.PUSHFRAME [code]  
```  
  
## <a name="remarks"></a>Notes  
 . PUSHFRAME permet aux utilisateurs de ml64.exe spécifier la façon dont une fonction de frame se déroule et est autorisée uniquement dans le prologue, qui s’étend de la [PROC](../../assembler/masm/proc.md) la déclaration de FRAME le [. ENDPROLOG](../../assembler/masm/dot-endprolog.md) la directive. Ces directives ne génèrent pas de code ; ils génèrent uniquement `.xdata` et `.pdata`. . PUSHFRAME doit être précédé d’instructions qui mettent véritablement en œuvre les actions devant être déroulée. Il est recommandé d’encapsuler les directives de déroulement et le code qu’ils visent à déroulement dans une macro pour garantir l’accord.  
  
 Pour plus d’informations, consultez [MASM pour x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)