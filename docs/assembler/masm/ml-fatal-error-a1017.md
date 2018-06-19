---
title: Erreur ML irrécupérable A1017 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A1017
dev_langs:
- C++
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5fcb2d921a40b35c6022b2aca1e22adc2d8c45e
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2018
ms.locfileid: "32054681"
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017
**nom de fichier source manquant**  
  
 ML n’a pas trouvé un fichier pour assembler ou passer à l’éditeur de liens.  
  
 Cette erreur est générée lorsque vous accordez des options de ligne de commande de ML sans spécifier un nom de fichier sur lequel agir. Pour assembler les fichiers qui n’ont pas l’extension .asm, utilisez le **/Ta** une option de ligne de commande.  
  
 Cette erreur peut également être générée en appelant ML sans paramètres si la variable d’environnement ML contient les options de ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)