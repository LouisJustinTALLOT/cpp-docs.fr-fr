---
title: Erreur du compilateur C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 4d09af5b29318e1481c666fcfe56b3f80434d4a0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80206494"
---
# <a name="compiler-error-c2241"></a>Erreur du compilateur C2241

'identifier' : accès au membre restreint

Le code tente d’accéder à un membre privé ou protégé.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Modifiez le niveau d’accès du membre.

1. Déclarez le membre comme `friend` de la fonction qui y accède.
