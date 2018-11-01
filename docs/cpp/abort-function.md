---
title: abort, fonction
ms.date: 12/01/2017
helpviewer_keywords:
- abort function
ms.assetid: 3352bcc4-1a8a-4e1f-8dcc-fe30f6b50f2d
ms.openlocfilehash: 7c87cb4fe7349a0d623c765c20e7e213a8454571
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451231"
---
# <a name="abort-function"></a>abort, fonction

Le **abandonner** fonction, déclarée également dans le fichier include standard \<stdlib.h >, met fin à un programme C++. La différence entre `exit` et **abandonner** qui est `exit` permet le traitement de terminaison d’exécution C++ se déroulent (objet global destructeurs seront appelés), tandis que **abandonner** arrête le programme immédiatement. Pour plus d’informations, consultez [abandonner](../c-runtime-library/reference/abort.md) dans le *Run-Time Library Reference*.

## <a name="see-also"></a>Voir aussi

[Terminaison du programme](../cpp/program-termination.md)