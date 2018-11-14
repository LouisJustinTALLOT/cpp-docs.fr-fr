---
title: _WAIT_CHILD, _WAIT_GRANDCHILD
ms.date: 11/04/2016
f1_keywords:
- _WAIT_GRANDCHILD
- WAIT_CHILD
- WAIT_GRANDCHILD
- _WAIT_CHILD
helpviewer_keywords:
- WAIT_CHILD constant
- WAIT_GRANDCHILD constant
- _WAIT_CHILD constant
- _WAIT_GRANDCHILD constant
ms.assetid: 7acd96fa-d118-4339-bb00-e5afaf286945
ms.openlocfilehash: 714b4e79f1c229817a12908aad0d726f74023036
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524389"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD

## <a name="syntax"></a>Syntaxe

```

#include <process.h>
```

## <a name="remarks"></a>Notes

La fonction `_cwait` peut être utilisée par n’importe quel processus pour attendre un autre processus (si l’ID du processus est connu). L’argument action peut être une des valeurs suivantes :

|Constante|Signification|
|--------------|-------------|
|`_WAIT_CHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié.|
|`_WAIT_GRANDCHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié et de tous les processus qu’il crée.|

## <a name="see-also"></a>Voir aussi

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)