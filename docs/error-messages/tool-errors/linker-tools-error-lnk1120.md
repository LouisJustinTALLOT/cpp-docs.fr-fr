---
title: L’erreur LNK1120 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 05/17/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1120
dev_langs:
- C++
helpviewer_keywords:
- LNK1120
ms.assetid: 56aa7d36-921f-4daf-b44d-cca0d4fb1b51
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fab2b937f8bf941219c678c638e9757903ee7698
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33298510"
---
# <a name="linker-tools-error-lnk1120"></a>Erreur des outils Éditeur de liens LNK1120
*nombre* externes non résolus  
  
L’erreur LNK1120 indique le nombre (*nombre*) d’erreurs de symbole externe non résolu pour cette opération de liaison. La plupart non résolue de symbole externe les erreurs sont signalées individuellement par [erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) et [erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), qui précède ce message d’erreur, une fois pour chaque symbole externe non résolu Erreur de symbole.  
  
Pour corriger cette erreur, corrigez toutes les autres erreurs externes non résolues ou d’autres erreurs de l’éditeur de liens qui la précèdent dans la sortie de génération. Cette erreur n’est pas signalée lorsqu’il ne reste aucune erreur externe non résolu.  
