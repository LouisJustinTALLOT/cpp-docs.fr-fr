---
title: Erreur du compilateur C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: a6a7bc0591fd51c808c303e94eeaaffd6111ffcd
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201917"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834

'operator opérateur’doit être globalement qualifié

Les opérateurs `new` et `delete` sont liés à la classe où ils résident. La résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` à partir d’une autre classe. Pour implémenter plusieurs formes de l’opérateur `new` ou `delete`, créez une version de l’opérateur avec des paramètres formels supplémentaires.
