---
description: 'En savoir plus sur : erreur du compilateur C2834'
title: Erreur du compilateur C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: 6f74853f264af653988ed77ddb9a9c7935f3c542
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194434"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834

'operator opérateur’doit être globalement qualifié

Les `new` `delete` opérateurs et sont liés à la classe dans laquelle ils résident. La résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` d’une autre classe. Pour implémenter plusieurs formes de `new` l' `delete` opérateur or, créez une version de l’opérateur avec des paramètres formels supplémentaires.
