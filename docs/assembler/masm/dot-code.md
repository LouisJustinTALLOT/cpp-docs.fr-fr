---
title: . CODE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .CODE
dev_langs:
- C++
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 59e376fc9c10ab8891b02e4da334341ae0534b73
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32051228"
---
# <a name="code"></a>.CODE
Lorsqu’il est utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md), indique le début d’un segment de code.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
.CODE [[name]]  
```  
  
#### <a name="parameters"></a>Paramètres  
  
|Paramètre|Description|  
|---------------|-----------------|  
|`name`|Paramètre facultatif qui spécifie le nom du segment de code. Le nom par défaut est _TEXT pour minuscule, petite, compact et plat [modèles](../../assembler/masm/dot-model.md). Le nom par défaut est *modulename*_TEXT pour d’autres modèles.|  
  
## <a name="see-also"></a>Voir aussi  
 [Référence des directives](../../assembler/masm/directives-reference.md)   
 [.DATA](../../assembler/masm/dot-data.md)