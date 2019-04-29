---
title: Avertissement des outils Éditeur de liens LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 0b18002135d225a90f7e45adc2ff57a64c0a79f4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279318"
---
# <a name="linker-tools-warning-lnk4092"></a>Avertissement des outils Éditeur de liens LNK4092

la section partagée 'section' accessible en écriture contient des réadressages ; image peut ne pas fonctionne correctement

L’éditeur de liens émet cet avertissement chaque fois que vous avez une section partagée pour vous avertir d’un problème sérieux.

La première consiste à partager des données entre plusieurs processus pour marquer une section comme « partagée ». Toutefois, marquage d’une section comme partagée peut entraîner des problèmes. Par exemple, vous avez une DLL qui contient des déclarations comme celle-ci dans une section de données partagée :

```
int var = 1;
int *pvar = &var;
```

L’éditeur de liens ne peut pas résoudre `pvar` , car sa valeur dépend où la DLL est chargée en mémoire, par conséquent, elle place un enregistrement de réadressage dans la DLL. Lorsque la DLL est chargée en mémoire, l’adresse de `var` peut être résolu et `pvar` affecté. Si un autre processus charge la même DLL mais ne peut pas faire à la même adresse, la réaffectation de l’adresse de `var` sera mis à jour pour le second processus et l’espace d’adressage du premier processus pointera vers une adresse incorrecte.