---
title: LNK2013 d’erreur des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9320b9ead0276b6fb5e1b9773260049a01520e12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33299849"
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013
type correction débordement. Cible 'symbol name' est hors limites  
  
 L’éditeur de liens ne peut contenir l’adresse nécessaire ou le décalage de l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.  
  
 Vous pouvez résoudre ce problème en créant plusieurs images ou en utilisant le [/Order](../../build/reference/order-put-functions-in-order.md) option pour l’instruction et la cible rapprocher.  
  
 Lorsque le nom de symbole est un symbole défini par l’utilisateur (et non généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :  
  
-   Modifiez la fonction statique pour être non statique.  
  
-   Renommez la section de code contenant la fonction statique pour être le même que l’appelant.  
  
 Utilisez `DUMPBIN /SYMBOLS`, pour déterminer si une fonction est statique.