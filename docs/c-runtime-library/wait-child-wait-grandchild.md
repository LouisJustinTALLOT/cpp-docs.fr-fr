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
ms.openlocfilehash: 98858058add6a0a11d4f9331989c6816e38130aa
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745052"
---
# <a name="waitchild-waitgrandchild"></a>_WAIT_CHILD, _WAIT_GRANDCHILD

## <a name="syntax"></a>Syntaxe

```
#include <process.h>
```

## <a name="remarks"></a>Remarques

La fonction `_cwait` peut être utilisée par n’importe quel processus pour attendre un autre processus (si l’ID du processus est connu). L’argument action peut être une des valeurs suivantes :

|Constante|Signification|
|--------------|-------------|
|`_WAIT_CHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié.|
|`_WAIT_GRANDCHILD`|Le processus appelant attend jusqu'à l’arrêt du nouveau processus spécifié et de tous les processus qu’il crée.|

## <a name="see-also"></a>Voir aussi

[_cwait](../c-runtime-library/reference/cwait.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)
