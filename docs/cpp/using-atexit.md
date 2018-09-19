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
ms.openlocfilehash: 9d5164394853d2ac4f18efc94863b8fc3fa5ba78
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053126"
---
# <a name="using-atexit"></a>Utilisation d'atexit

Avec le [atexit](../c-runtime-library/reference/atexit.md) (fonction), vous pouvez spécifier une fonction de sortie de traitement qui s’exécute avant l’arrêt du programme. Aucun objet statique global initialisé avant l’appel à **atexit** sont détruits avant l’exécution de la fonction de sortie de traitement.

## <a name="see-also"></a>Voir aussi

[Considérations supplémentaires sur la terminaison](../cpp/additional-termination-considerations.md)