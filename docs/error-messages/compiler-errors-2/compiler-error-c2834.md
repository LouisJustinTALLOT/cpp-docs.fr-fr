---
title: Erreur du compilateur C2834 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b94e1a3fba9bc3589af020340651b4546347cf1a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46089344"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834

'operator opérateur' doit être globalement qualifié

Le `new` et `delete` opérateurs sont liées à la classe dans laquelle ils résident. Résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` d’une autre classe. Pour implémenter plusieurs formes de la `new` ou `delete` opérateur, créer une version de l’opérateur avec des paramètres formels supplémentaires.