---
title: Erreur irrécupérable NMAKE U1073 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U1073
dev_langs:
- C++
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c309ed94cd1c984406e0d21f0139e35c6e41d7d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46053936"
---
# <a name="nmake-fatal-error-u1073"></a>Erreur irrécupérable NMAKE U1073

ignorez comment rendre 'targetname'

La cible spécifiée n’existe pas, et il n’existe aucune commande à exécuter ou une règle d’inférence à appliquer.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Vérifiez l’orthographe du nom de la cible.

1. Si *targetname* est une pseudocible, spécifiez-la en tant que cible dans un autre bloc de description.

1. Si *targetname* est un appel de macro, veillez à ne développe pas une chaîne null.