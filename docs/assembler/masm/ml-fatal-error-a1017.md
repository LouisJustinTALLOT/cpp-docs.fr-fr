---
title: Erreur ML irrécupérable A1017
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 22a16569364760d0cb1d01011405f7a11dd21cac
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62177771"
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017

**nom de fichier source manquant**

ML n’a pas trouvé un fichier pour assembler ou passer à l’éditeur de liens.

Cette erreur est générée lorsque vous donnez des options de ligne de commande ML sans spécifier un nom de fichier sur lequel agir. Pour assembler les fichiers qui n’ont pas une extension .asm, utilisez le **/Ta** option de ligne de commande.

Cette erreur peut également être générée en appelant ML sans paramètres si la variable d’environnement machine Learning contient les options de ligne de commande.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>