---
title: setjmp-longjump | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0e21902-095d-4198-8f9a-b6326525721a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f53160a5deeb3ea0db111fc0aae7429b19b7cc86
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45703272"
---
# <a name="setjmplongjump"></a>setjmp/longjump

Lorsque vous incluez setjmpex.h ou setjmp.h, tous les appels à [setjmp](../c-runtime-library/reference/setjmp.md) ou [longjmp](../c-runtime-library/reference/longjmp.md) entraînent un déroulement qui appelle des destructeurs et enfin des appels.  Cela diffère x86, où l’inclusion des résultats de setjmp.h dans les clauses finally et des destructeurs ne pas invoquées.

Un appel à `setjmp` conserve le pointeur de pile actuel, les registres non volatils et les registres MxCsr.  Les appels à `longjmp` retour à la plus récente `setjmp` appeler le site et réinitialise le pointeur de pile, les registres non volatils et les MxCsr inscrit, à l’état préservé par la plus récente `setjmp` appeler.

## <a name="see-also"></a>Voir aussi

[Convention d’appel](../build/calling-convention.md)