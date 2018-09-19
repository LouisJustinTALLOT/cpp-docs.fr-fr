---
title: Erreur du compilateur C3551 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3551
dev_langs:
- C++
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b45a6f66ab7cf2a5ebb7ae6b2a2f78e664092604
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035732"
---
# <a name="compiler-error-c3551"></a>Erreur du compilateur C3551

« type de retour spécifié à la fin attendu »

Si vous utilisez le mot clé `auto` en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Dans l’exemple suivant, le type de retour spécifié à la fin de la fonction `myFunction` est un pointeur vers un tableau de quatre éléments de type `int`.

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>Voir aussi

[auto](../../cpp/auto-cpp.md)