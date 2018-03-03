---
title: "LNK2013 d’erreur des outils Éditeur de liens | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2013
dev_langs:
- C++
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8cf88f768f05eee06ae8ffaa66f8de5a9c443f82
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-error-lnk2013"></a>Erreur des outils Éditeur de liens LNK2013
type correction débordement. Cible 'symbol name' est hors limites  
  
 L’éditeur de liens ne peut contenir l’adresse nécessaire ou le décalage de l’instruction donnée parce que le symbole cible est trop loin à partir de l’emplacement de l’instruction.  
  
 Vous pouvez résoudre ce problème en créant plusieurs images ou en utilisant le [/Order](../../build/reference/order-put-functions-in-order.md) option pour l’instruction et la cible rapprocher.  
  
 Lorsque le nom de symbole est un symbole défini par l’utilisateur (et non généré par le compilateur), vous pouvez également essayer les actions suivantes pour résoudre l’erreur :  
  
-   Modifiez la fonction statique pour être non statique.  
  
-   Renommez la section de code contenant la fonction statique pour être le même que l’appelant.  
  
 Utilisez `DUMPBIN /SYMBOLS`, pour déterminer si une fonction est statique.