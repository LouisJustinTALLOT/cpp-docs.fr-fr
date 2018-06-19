---
title: Compilateur avertissement (niveau 1) C4182 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4182
dev_langs:
- C++
helpviewer_keywords:
- C4182
ms.assetid: 8970f3c6-e2dd-407e-b2ec-964360eb8b43
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79e86076a9d8218d08bd7437e2a06878b6ee91ff
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278179"
---
# <a name="compiler-warning-level-1-c4182"></a>Avertissement du compilateur (niveau 1) C4182
\#inclure au niveau d’imbrication est 'nombre' profondeur ; risque de récurrence infinie  
  
 Le compilateur a manqué d’espace sur le tas en raison du nombre de fichiers Include imbriqués. Un fichier Include est imbriqué quand il est inclus dans un autre fichier Include.  
  
 Ce message est un fourni à titre d’information et précède l’erreur [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md).