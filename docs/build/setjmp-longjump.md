---
title: setjmp-longjump | Documents Microsoft
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
ms.openlocfilehash: 55cf6a2503367777464f09f92e3e3614c3d9f11b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379833"
---
# <a name="setjmplongjump"></a>setjmp/longjump
Lorsque vous incluez setjmpex.h ou setjmp.h, tous les appels à [setjmp](../c-runtime-library/reference/setjmp.md) ou [longjmp](../c-runtime-library/reference/longjmp.md) entraînent un déroulement qui appelle des destructeurs et enfin des appels.  Cela diffère de x86, y compris les résultats de setjmp.h dans les clauses finally et destructeurs ne pas appelés.  
  
 Un appel à `setjmp` conserve le pointeur de pile actuel, les registres non volatils et les registres MxCsr.  Les appels à `longjmp` retour à la plus récente `setjmp` appeler le site et réinitialise le pointeur de pile, les registres non volatils et MxCsr inscrit, à l’état préservé par la plus récente `setjmp` appeler.  
  
## <a name="see-also"></a>Voir aussi  
 [Convention d’appel](../build/calling-convention.md)