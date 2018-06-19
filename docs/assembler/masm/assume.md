---
title: SUPPOSONS | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- ASSUME
dev_langs:
- C++
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8898895d2e107e522fe88dc954146d64e6f62b9
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32050634"
---
# <a name="assume"></a>ASSUME
Active la vérification des erreurs pour les valeurs de Registre.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
ASSUME segregister:name [[, segregister:name]]...  
ASSUME dataregister:type [[, dataregister:type]]...  
ASSUME register:ERROR [[, register:ERROR]]...  
ASSUME [[register:]] NOTHING [[, register:NOTHING]]...  
```  
  
## <a name="remarks"></a>Notes  
 Après une `ASSUME` est placé entre en vigueur, l’assembleur surveille les modifications apportées aux valeurs des registres donnés. **ERREUR** génère une erreur si le Registre est utilisé. **NOTHING** supprime inscrire la vérification des erreurs. Vous pouvez combiner les différents types d’hypothèses dans une instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Informations de référence sur les directives](../../assembler/masm/directives-reference.md)