---
title: LNK4092 d’avertissement des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4092
dev_langs:
- C++
helpviewer_keywords:
- LNK4092
ms.assetid: d569ec47-a338-40e1-940b-8a8061459acb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 72edd9e75dbc781355396e38f767a64c1ded3aa9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302579"
---
# <a name="linker-tools-warning-lnk4092"></a>Avertissement des outils Éditeur de liens LNK4092
la section partagée 'section' accessible en écriture contient des réadressages ; image peut ne pas fonctionne correctement  
  
 L’éditeur de liens émet cet avertissement chaque fois que vous avez une section partagée pour vous avertir d’un problème sérieux.  
  
 Une façon de partager des données entre plusieurs processus consiste à marquer une section comme « partagée ». Toutefois, le marquage d’une section comme partagée peut entraîner des problèmes. Par exemple, vous avez une DLL qui contient des déclarations comme celle-ci dans une section de données partagée :  
  
```  
int var = 1;  
int *pvar = &var;  
```  
  
 L’éditeur de liens ne peut pas résoudre `pvar` parce que sa valeur dépend où la DLL est chargée en mémoire, donc il passe un enregistrement de réadressage dans la DLL. Lorsque la DLL est chargée en mémoire, l’adresse de `var` peuvent être résolus et `pvar` attribué. Si un autre processus charge la même DLL mais ne peut pas faire à la même adresse, la réaffectation de l’adresse de `var` sera mis à jour pour le second processus et l’espace d’adressage du premier processus pointera sur la mauvaise adresse.