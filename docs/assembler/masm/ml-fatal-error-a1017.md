---
title: Erreur ML irrécupérable A1017
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 523fed26afae5a88c5f154283487d3453a2e48c7
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318057"
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017

**nom de fichier source manquant**

ML n’a pas pu trouver un fichier à assembler ou à passer à l’éditeur de liens.

Cette erreur est générée lorsque vous fournissez des options de ligne de commande ML sans spécifier de nom de fichier sur lequel agir. Pour assembler des fichiers qui n’ont pas d’extension. asm, utilisez l’option de ligne de commande **/ta** .

Cette erreur peut également être générée en appelant ML sans paramètre si la variable d’environnement ML contient des options de ligne de commande.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](ml-error-messages.md)
