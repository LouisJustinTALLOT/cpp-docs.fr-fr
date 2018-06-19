---
title: Erreur du compilateur C3552 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3552
dev_langs:
- C++
helpviewer_keywords:
- C3552
ms.assetid: 83401524-1bf1-44c0-8aca-a6eb35c4224c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a5f1453a6175019ad7c90471330d11c77da26134
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33252541"
---
# <a name="compiler-error-c3552"></a>Erreur du compilateur C3552
'typename' : un type de retour spécifié à la fin ne peut pas contenir 'auto'  
  
 Si vous utilisez le mot clé `auto` en tant qu’espace réservé pour le type de retour d’une fonction, vous devez fournir un type de retour spécifié à la fin. Toutefois, vous ne pouvez pas utiliser un autre mot clé `auto` pour spécifier le type de retour spécifié à la fin. Par exemple, le fragment de code suivant génère l’erreur C3552.  
  
 `auto myFunction->auto; // C3552`