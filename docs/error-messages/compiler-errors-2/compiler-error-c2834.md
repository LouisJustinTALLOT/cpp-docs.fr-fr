---
title: Erreur du compilateur C2834
ms.date: 11/04/2016
f1_keywords:
- C2834
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
ms.openlocfilehash: fb4a0e6f3f6ec227b978ae0b7d3864b2134de986
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406819"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834

'operator opérateur' doit être globalement qualifié

Le `new` et `delete` opérateurs sont liées à la classe dans laquelle ils résident. Résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` d’une autre classe. Pour implémenter plusieurs formes de la `new` ou `delete` opérateur, créer une version de l’opérateur avec des paramètres formels supplémentaires.