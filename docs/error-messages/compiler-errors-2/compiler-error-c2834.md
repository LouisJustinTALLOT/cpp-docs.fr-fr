---
title: Erreur du compilateur C2834 | Documents Microsoft
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
ms.openlocfilehash: 4eb4fb992f9213c4a4b456f786fd8f81308cec12
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33244782"
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834
'operator opérateur' doit être globalement qualifié  
  
 Le `new` et `delete` opérateurs sont liés à la classe où elles résident. Résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` à partir d’une autre classe. Pour implémenter plusieurs formes de le `new` ou `delete` (opérateur), créez une version de l’opérateur avec des paramètres formels supplémentaires.