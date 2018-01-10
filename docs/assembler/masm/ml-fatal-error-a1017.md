---
title: "Erreur ML irrécupérable A1017 | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: A1017
dev_langs: C++
helpviewer_keywords: A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0603ccb1de5767294afcfc012c1b9c8b18ac776d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017
**nom de fichier source manquant**  
  
 ML n’a pas trouvé un fichier pour assembler ou passer à l’éditeur de liens.  
  
 Cette erreur est générée lorsque vous accordez des options de ligne de commande de ML sans spécifier un nom de fichier sur lequel agir. Pour assembler les fichiers qui n’ont pas l’extension .asm, utilisez le **/Ta** une option de ligne de commande.  
  
 Cette erreur peut également être générée en appelant ML sans paramètres si la variable d’environnement ML contient les options de ligne de commande.  
  
## <a name="see-also"></a>Voir aussi  
 [Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)