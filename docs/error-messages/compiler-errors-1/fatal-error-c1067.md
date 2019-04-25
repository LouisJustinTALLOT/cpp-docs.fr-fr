---
title: Erreur irrécupérable C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: f8fe301e25d9ecb5cc67397f9537e0bbd86c0627
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165851"
---
# <a name="fatal-error-c1067"></a>Erreur irrécupérable C1067

limite du compilateur : Limite de 64 Ko sur la taille d’un enregistrement de type a été dépassé.

Cette erreur peut se produire si un symbole a un nom décoré dépassant 247 caractères.  Pour résoudre, raccourcissez le nom du symbole.

Lorsque le compilateur génère des informations de débogage, il émet des enregistrements de type pour définir les types rencontrés dans le code source.  Par exemple, les enregistrements de type incluent des structures simples et des listes d’arguments de fonctions.  Certains de ces enregistrements de type peuvent être des grandes listes.

Il existe une limite de 64 Ko de la taille de l’enregistrement de n’importe quel type.  Si vous dépassez cette limite de 64 Ko cette erreur se produit.

C1067 peut également se produire s’il existe de nombreux symboles portant des noms longs ou si une classe, struct ou union comporte trop de membres.