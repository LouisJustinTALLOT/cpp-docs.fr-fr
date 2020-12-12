---
description: 'En savoir plus sur les éléments suivants : avertissement des outils Éditeur de liens LNK4092'
title: Avertissement des outils Éditeur de liens LNK4092
ms.date: 11/04/2016
f1_keywords:
- LNK4092
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
ms.openlocfilehash: 6ef835981a8ed7921147697d6ed9fc79ceeb7033
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97210008"
---
# <a name="linker-tools-warning-lnk4092"></a>Avertissement des outils Éditeur de liens LNK4092

la section partagée’section’accessible en écriture contient des réadressages ; l’image risque de ne pas s’exécuter correctement

L’éditeur de liens émet cet avertissement chaque fois que vous disposez d’une section partagée pour vous avertir d’un problème potentiellement sérieux.

Une façon de partager des données entre plusieurs processus consiste à marquer une section comme « partagée ». Toutefois, le marquage d’une section comme partagée peut entraîner des problèmes. Par exemple, vous avez une DLL qui contient des déclarations de ce type dans une section de données partagées :

```
int var = 1;
int *pvar = &var;
```

L’éditeur de liens ne peut pas résoudre, `pvar` car sa valeur dépend de l’emplacement de chargement de la dll dans la mémoire. il met donc un enregistrement de réadressage dans la dll. Lorsque la DLL est chargée en mémoire, l’adresse de `var` peut être résolue et `pvar` assignée. Si un autre processus charge la même DLL, mais ne peut pas le charger à la même adresse, le déplacement de l’adresse de `var` sera mis à jour pour le deuxième processus et l’espace d’adressage du premier processus pointera vers l’adresse incorrecte.
