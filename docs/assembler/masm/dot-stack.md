---
title: . PILE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .STACK
dev_langs:
- C++
helpviewer_keywords:
- .STACK directive
ms.assetid: 70019463-5d4f-41b6-8464-023a8ac2466f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dab47677da8db2afca73a078b110300a017e7c8d
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32052298"
---
# <a name="stack"></a>.STACK
Lorsqu’il est utilisé avec [. MODÈLE](../../assembler/masm/dot-model.md), définit un segment de pile (avec le nom du segment de pile). Le paramètre facultatif `size` Spécifie le nombre d’octets de la pile (valeur par défaut 1 024). Le `.STACK` directive ferme automatiquement l’instruction de la pile.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
.STACK [[size]]  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)