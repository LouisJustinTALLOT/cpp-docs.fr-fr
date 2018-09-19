---
title: Erreur du compilateur C2097 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2097
dev_langs:
- C++
helpviewer_keywords:
- C2097
ms.assetid: 7e5b2fd4-f61c-4b8a-b265-93e987a04bd3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2da955f5382a1ebacdb507a69ed02627b11462e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021861"
---
# <a name="compiler-error-c2097"></a>Erreur du compilateur C2097

initialisation non conforme

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Initialisation d’une variable à l’aide d’une valeur non constante.

1. Initialisation d’une adresse courte avec une adresse longue.

1. Initialisation d’une structure locale, une union ou un tableau avec une expression non constante lors de la compilation avec **/Za**.

1. Initialisation avec une expression contenant un opérateur virgule.

1. Initialisation avec une expression qui n’est ni constante ni symbolique.