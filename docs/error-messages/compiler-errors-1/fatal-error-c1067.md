---
title: Erreur irrécupérable C1067 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1067
dev_langs:
- C++
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 89ac7084e92f7f2ed496a4c1572e94a4fa46862f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33229090"
---
# <a name="fatal-error-c1067"></a>Erreur irrécupérable C1067
limite du compilateur : limite de 64 Ko sur la taille d’un enregistrement de type a été dépassé.  
  
 Cette erreur peut se produire si un symbole comporte un nom décoré dépassant 247 caractères.  Pour résoudre, raccourcissez le nom de symbole.  
  
 Lorsque le compilateur génère des informations de débogage, il émet des enregistrements de type pour définir les types rencontrés dans le code source.  Par exemple, les enregistrements de type incluent les structures simples et des listes d’arguments de fonctions.  Certains de ces enregistrements de type peuvent être longues listes.  
  
 Il existe une limite de 64 Ko de la taille de l’enregistrement de n’importe quel type.  Si cette limite de 64 Ko est dépassée. cette erreur se produit.  
  
 C1067 peut également se produire s’il existe de nombreux symboles avec des noms longs ou si une classe, struct ou union comporte trop de membres.