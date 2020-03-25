---
title: Erreur du compilateur C2722
ms.date: 11/04/2016
f1_keywords:
- C2722
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
ms.openlocfilehash: 7426df1970dee58cd4363ee345e2286165e375b6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80202170"
---
# <a name="compiler-error-c2722"></a>Erreur du compilateur C2722

' :: Operator' : la commande d’opérateur suivante n’est pas conforme ; Utilisez’operator opérateur'

Une instruction `operator` redéfinit `::new` ou `::delete`. Les opérateurs `new` et `delete` étant globaux, l’opérateur de résolution de portée (`::`) est dénué de sens. Supprimez l’opérateur `::` .
