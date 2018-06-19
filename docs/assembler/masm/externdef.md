---
title: EXTERNDEF | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- EXTERNDEF
dev_langs:
- C++
helpviewer_keywords:
- EXTERNDEF directive
ms.assetid: 95a10de6-c345-4428-a2f2-90f7d411dc86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b010f52f91a04388f34052fcc5c374690cff13df
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052698"
---
# <a name="externdef"></a>EXTERNDEF
Définit une ou plusieurs variables externes, des étiquettes ou des symboles appelés *nom* dont le type est `type`.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
EXTERNDEF [[langtype]] name:type [[, [[langtype]] name:type]]...  
```  
  
## <a name="remarks"></a>Notes  
 Si *nom* est défini dans le module, il est traité comme [PUBLIC](../../assembler/masm/public-masm.md). Si *nom* est référencé dans le module, il est traité comme [EXTERN](../../assembler/masm/extern-masm.md). Si *nom* est ne pas référencée, elle est ignorée. Le `type` peut être [ABS](../../assembler/masm/operator-abs.md), qui importe *nom* en tant que constante. Normalement utilisée dans les fichiers include.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)