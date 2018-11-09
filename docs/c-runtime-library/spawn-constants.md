---
title: spawn, constantes
ms.date: 11/04/2016
f1_keywords:
- _P_NOWAIT
- _P_OVERLAY
- _P_WAIT
- _P_DETACH
- _P_NOWAITO
helpviewer_keywords:
- _P_OVERLAY constant
- P_DETACH constant
- P_OVERLAY constant
- P_NOWAIT constant
- _P_DETACH constant
- _P_NOWAIT constant
- _P_NOWAITO constant
- P_NOWAITO constant
- spawn constants
- P_WAIT constant
- _P_WAIT constant
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
ms.openlocfilehash: 1bfb13309ae4bd667a5e128300740f4c903f08be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50580945"
---
# <a name="spawn-constants"></a>spawn, constantes

## <a name="syntax"></a>Syntaxe

```
#include <process.h>
```

## <a name="remarks"></a>Notes

L'argument `mode` détermine l'action effectuée par le processus appelant avant et pendant une opération de génération dynamique. Les valeurs suivantes pour `mode` sont possibles :

|Constante|Signification|
|--------------|-------------|
|`_P_OVERLAY`|Superpose un processus appelant avec un nouveau processus, en détruisant le processus appelant (même effet que les appels `_exec`).|
|`_P_WAIT`|Interrompt un thread appelant jusqu'à ce que l'exécution du nouveau processus soit terminée (`_spawn` synchrone).|
|`_P_NOWAIT`, `_P_NOWAITO`|Continue d'exécuter un processus appelant en même temps que le nouveau processus (`_spawn` asynchrone).|
|`_P_DETACH`|Continue d'exécuter le processus appelant ; le nouveau processus est exécuté en arrière-plan sans accès à la console ou au clavier. Les appels à `_cwait` sur le nouveau processus échoueront. Il s’agit d’un `_spawn` asynchrone.|

## <a name="see-also"></a>Voir aussi

[_spawn, _wspawn, fonctions](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[Constantes globales](../c-runtime-library/global-constants.md)