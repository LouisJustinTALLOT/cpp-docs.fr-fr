---
title: Erreur du compilateur C2241
ms.date: 11/04/2016
f1_keywords:
- C2241
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
ms.openlocfilehash: 88f25931d84fe3884ebecbc97b9ddd73390bacc2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388967"
---
# <a name="compiler-error-c2241"></a>Erreur du compilateur C2241

'identifier' : accès au membre restreint

Le code tente d’accéder à un membre privé ou protégé.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Modifiez le niveau d’accès du membre.

1. Déclarez le membre comme `friend` de la fonction qui y accède.