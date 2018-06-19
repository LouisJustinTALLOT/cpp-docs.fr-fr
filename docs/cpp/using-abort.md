---
title: Utilisation d’abort | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- Abort
dev_langs:
- C++
helpviewer_keywords:
- abort function
ms.assetid: 3ba39b78-ef74-4a8d-8dee-2d62442de174
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7231339ba4884445d7ad6b0161c6cff793c6db8a
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32421846"
---
# <a name="using-abort"></a>Utilisation de abort
Appel de la [abandonner](../c-runtime-library/reference/abort.md) fonction provoque l’arrêt immédiat. Il ignore le processus normal de destruction des objets statiques globaux initialisés. Il ignore également tout traitement spécial qui a été spécifié avec la fonction `atexit`.  
  
## <a name="see-also"></a>Voir aussi  
 [Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)