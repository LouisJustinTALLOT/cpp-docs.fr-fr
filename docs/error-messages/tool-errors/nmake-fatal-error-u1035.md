---
title: Erreur irrécupérable NMAKE U1035 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1035
dev_langs:
- C++
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0383bf4742d637d669070efa5370ebda0c7ab159
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019859"
---
# <a name="nmake-fatal-error-u1035"></a>Erreur irrécupérable NMAKE U1035

Erreur de syntaxe : attendu ' :' ou '=' un séparateur

Signe deux-points (**:**) ou un signe égal (**=**) était attendu.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Pour corriger en vérifiant les causes possibles suivantes

1. Un signe deux-points ne respectaient pas une cible.

1. Un signe deux-points et aucun espace (par exemple, a :),) suivi une cible de lettre unique. NMAKE interprète cela comme une spécification de lecteur.

1. Un signe deux-points ne respectaient pas une règle d’inférence.

1. Une définition de macro n’a pas été suivie par un signe égal.

1. Un caractère suivi d’une barre oblique inverse (**\\**) qui a été utilisé pour une commande continue sur une nouvelle ligne.

1. Une chaîne est apparue qui n’est pas suivie de n’importe quelle règle de syntaxe NMAKE.

1. Le makefile a été mis en forme par un traitement de texte.