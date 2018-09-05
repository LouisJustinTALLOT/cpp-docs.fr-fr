---
title: Erreur ML irrécupérable A1017 | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
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
ms.openlocfilehash: fb98eab68da417526a75beaa57870ce906c85a8d
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43688557"
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017

**nom de fichier source manquant**

ML n’a pas trouvé un fichier pour assembler ou passer à l’éditeur de liens.

Cette erreur est générée lorsque vous donnez des options de ligne de commande ML sans spécifier un nom de fichier sur lequel agir. Pour assembler les fichiers qui n’ont pas une extension .asm, utilisez le **/Ta** option de ligne de commande.

Cette erreur peut également être générée en appelant ML sans paramètres si la variable d’environnement machine Learning contient les options de ligne de commande.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>