---
title: Erreur irrécupérable C1021 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1021
dev_langs:
- C++
helpviewer_keywords:
- C1021
ms.assetid: e23171f4-ca6b-40c0-a913-a2edc6fa3766
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fcb464a676b47baa4589c17269819d3a84d058fe
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46029909"
---
# <a name="fatal-error-c1021"></a>Erreur irrécupérable C1021

Commande de préprocesseur non valide 'chaîne'

`string` n’est pas une [directive de préprocesseur](../../preprocessor/preprocessor-directives.md)valide. Pour résoudre cette erreur, utilisez un nom de préprocesseur valide pour `string`.

L’exemple suivant génère l’erreur C1021 :

```
// C1021.cpp
#BadPreProcName    // C1021 delete line
```