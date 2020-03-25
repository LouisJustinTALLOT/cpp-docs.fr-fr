---
title: Avertissement des outils Éditeur de liens LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 706ab843f4b079b507033af76a7f407816fce820
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183356"
---
# <a name="linker-tools-warning-lnk4092"></a>Avertissement des outils Éditeur de liens LNK4092

la section partagée’section’accessible en écriture contient des réadressages ; l’image risque de ne pas s’exécuter correctement

L’éditeur de liens émet cet avertissement chaque fois que vous disposez d’une section partagée pour vous avertir d’un problème potentiellement sérieux.

Une façon de partager des données entre plusieurs processus consiste à marquer une section comme « partagée ». Toutefois, le marquage d’une section comme partagée peut entraîner des problèmes. Par exemple, vous avez une DLL qui contient des déclarations de ce type dans une section de données partagées :

```
int var = 1;
int *pvar = &var;
```

L’éditeur de liens ne peut pas résoudre `pvar`, car sa valeur dépend de l’emplacement de chargement de la DLL dans la mémoire. il met donc un enregistrement de réadressage dans la DLL. Lorsque la DLL est chargée en mémoire, l’adresse de `var` peut être résolue et `pvar` affectée. Si un autre processus charge la même DLL, mais ne peut pas le charger à la même adresse, le déplacement de l’adresse de `var` sera mis à jour pour le deuxième processus et l’espace d’adressage du premier processus pointera vers l’adresse incorrecte.
