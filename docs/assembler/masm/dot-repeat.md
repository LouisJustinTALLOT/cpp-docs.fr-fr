---
title: . RÉPÉTEZ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .REPEAT
dev_langs:
- C++
helpviewer_keywords:
- .REPEAT directive
ms.assetid: cb8ad8c6-587b-42f9-a0ad-b5316a24918c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 41e3dadaa95cb4bf0ca4a17af32332d5b5471245
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052448"
---
# <a name="repeat"></a>.REPEAT
Génère du code qui répète l’exécution du bloc de *instructions* jusqu'à ce que `condition` prend la valeur true. [. UNTILCXZ](../../assembler/masm/dot-untilcxz.md), qui prend la valeur true lorsque CX est égal à zéro, peut être remplacé par [. Jusqu'à ce que](../../assembler/masm/dot-until.md). Le `condition` est facultatif avec **. UNTILCXZ**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
   .REPEAT  
statements  
.UNTIL condition  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)