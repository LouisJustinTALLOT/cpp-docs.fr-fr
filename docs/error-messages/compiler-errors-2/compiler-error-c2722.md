---
title: Erreur du compilateur C2722 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2722
dev_langs:
- C++
helpviewer_keywords:
- C2722
ms.assetid: 4cc2c7fa-cb12-4bcf-9df1-6d627ef62973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8c8838ed6b2d202d58c9553a773da9653839b6c8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236376"
---
# <a name="compiler-error-c2722"></a>Erreur du compilateur C2722
' :: opérateur ' : non conforme après une commande operator ; Utilisez 'operator opérateur'  
  
 Un `operator` instruction redéfinit `::new` ou `::delete`. Le `new` et `delete` opérateurs sont globaux, par conséquent, l’opérateur de résolution de portée (`::`) n’a aucune signification. Supprimer le `::` opérateur.