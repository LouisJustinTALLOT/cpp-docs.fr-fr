---
title: Erreur irrécupérable C1126 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1126
dev_langs:
- C++
helpviewer_keywords:
- C1126
ms.assetid: f22b26a6-8ad7-47cf-a237-196c8ea60aca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a3ff02d69679074186e593d5e1c16bdf56d1052
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33225912"
---
# <a name="fatal-error-c1126"></a>Erreur irrécupérable C1126
'identificateur' : l’allocation automatique dépasse la taille  
  
 Espace alloué pour les variables locales d’une fonction (plus une quantité limitée de l’espace utilisé par le compilateur, notamment un supplémentaire de 20 octets pour les fonctions échangeables) dépasse la limite.  
  
 Pour corriger cette erreur, utilisez `malloc` ou `new` pour allouer de grandes quantités de données.