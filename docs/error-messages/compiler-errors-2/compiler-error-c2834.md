---
title: Erreur du compilateur C2834 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: error-reference
f1_keywords:
- C2834
dev_langs:
- C++
helpviewer_keywords:
- C2834
ms.assetid: 28f9f6eb-ab2a-4e64-aaaa-9d14f955de41
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 616bb6fe351c7575bf04f319390d0a3cfcd3cc8a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2834"></a>Erreur du compilateur C2834
'operator opérateur' doit être globalement qualifié  
  
 Le `new` et `delete` opérateurs sont liés à la classe où elles résident. Résolution de portée ne peut pas être utilisée pour sélectionner une version de `new` ou `delete` à partir d’une autre classe. Pour implémenter plusieurs formes de le `new` ou `delete` (opérateur), créez une version de l’opérateur avec des paramètres formels supplémentaires.