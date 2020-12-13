---
description: 'En savoir plus sur : erreur irrécupérable C1067'
title: Erreur irrécupérable C1067
ms.date: 11/04/2016
f1_keywords:
- C1067
helpviewer_keywords:
- C1067
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
ms.openlocfilehash: ef50719740de99f85e7e94f99cf0e14531608b22
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97344417"
---
# <a name="fatal-error-c1067"></a>Erreur irrécupérable C1067

limite du compilateur : la limite de 64 Ko pour la taille d’un enregistrement de type a été dépassée

Cette erreur peut se produire si un symbole a un nom décoré dépassant 247 caractères.  Pour résoudre le nom du symbole, raccourcissez-le.

Lorsque le compilateur génère des informations de débogage, il émet des enregistrements de type pour définir les types rencontrés dans le code source.  Par exemple, les enregistrements de type incluent des structures simples et des listes d’arguments de fonctions.  Certains de ces enregistrements de type peuvent être des listes volumineuses.

La taille d’un enregistrement de type est limitée à 64 Ko.  Si cette limite de 64 Ko est dépassée, cette erreur se produit.

C1067 peut également se produire s’il existe de nombreux symboles avec des noms longs ou si une classe, un struct ou une Union possède trop de membres.
