---
title: Erreur du compilateur C2241 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2241
dev_langs:
- C++
helpviewer_keywords:
- C2241
ms.assetid: 2f4e2c2c-b95c-4afe-bbe0-4214cd39d140
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd97551e0feaecce776cc552353716c67822f273
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055895"
---
# <a name="compiler-error-c2241"></a>Erreur du compilateur C2241

'identifier' : accès au membre restreint

Le code tente d’accéder à un membre privé ou protégé.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Pour résoudre ce problème, appliquez les solutions possibles suivantes.

1. Modifiez le niveau d’accès du membre.

1. Déclarez le membre comme `friend` de la fonction qui y accède.