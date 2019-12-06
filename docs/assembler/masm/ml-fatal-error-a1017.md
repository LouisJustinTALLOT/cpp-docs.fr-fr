---
title: Erreur ML irrécupérable A1017
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A1017
helpviewer_keywords:
- A1017
ms.assetid: bef0b312-5431-4e5a-b637-c19919acf01b
ms.openlocfilehash: 6fb0835cca135fc994866dc2453734d7b3012a64
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856824"
---
# <a name="ml-fatal-error-a1017"></a>Erreur ML irrécupérable A1017

**nom de fichier source manquant**

ML n’a pas pu trouver un fichier à assembler ou à passer à l’éditeur de liens.

Cette erreur est générée lorsque vous fournissez des options de ligne de commande ML sans spécifier de nom de fichier sur lequel agir. Pour assembler des fichiers qui n’ont pas d’extension. asm, utilisez l’option de ligne de commande **/ta** .

Cette erreur peut également être générée en appelant ML sans paramètre si la variable d’environnement ML contient des options de ligne de commande.

## <a name="see-also"></a>Voir aussi

[Messages d’erreur ML](../../assembler/masm/ml-error-messages.md)<br/>