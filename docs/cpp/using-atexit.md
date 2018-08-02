---
title: Utilisation d’atexit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- atexit
dev_langs:
- C++
helpviewer_keywords:
- atexit function
ms.assetid: d28fda17-c3d4-4af6-ba44-f44886bbb237
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f4acd81a5420f9fe2685e7570f26fea61691b845
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467402"
---
# <a name="using-atexit"></a>Utilisation d'atexit
Avec le [atexit](../c-runtime-library/reference/atexit.md) (fonction), vous pouvez spécifier une fonction de sortie de traitement qui s’exécute avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **atexit** sont détruits avant l’exécution de la fonction de sortie de traitement.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)