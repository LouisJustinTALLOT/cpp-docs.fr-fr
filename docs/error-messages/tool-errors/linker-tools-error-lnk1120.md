---
title: L’erreur LNK1120 des outils Éditeur de liens | Microsoft Docs
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
ms.openlocfilehash: f1d2a55d683e9c8b9d6a0da2b3e5fa78d5a39933
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725567"
---
# <a name="linker-tools-error-lnk1120"></a>Erreur des outils Éditeur de liens LNK1120

> *nombre* externes non résolus  
  
L’erreur LNK1120 signale le nombre (*nombre*) des erreurs de symbole externe non résolu pour cette opération de liaison. La plupart non résolu les erreurs de symbole externe sont signalées individuellement par [erreur des outils Éditeur de liens LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md) et [erreur des outils Éditeur de liens LNK2019](../../error-messages/tool-errors/linker-tools-error-lnk2019.md), qui précèdent ce message d’erreur, une fois pour chaque symbole externe non résolu Erreur de symbole.  
  
Pour corriger cette erreur, corrigez toutes les autres erreurs externes non résolues ou d’autres erreurs de l’éditeur de liens qui la précèdent dans la sortie de génération. Cette erreur n’est pas signalée lorsqu’il ne reste aucune erreur externe non résolu.  
