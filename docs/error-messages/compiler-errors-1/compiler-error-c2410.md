---
title: Erreur du compilateur C2410 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f9c2a2df0941130c4f2416806a05ce0378373eb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33226442"
---
# <a name="compiler-error-c2410"></a>Erreur du compilateur C2410
'identificateur' : nom de membre ambigu dans 'contexte'  
  
 L’identificateur est un membre de plus d’une structure ou union dans ce contexte.  
  
 Utilisez un spécificateur d’union ou de structure sur l’opérande qui a provoqué l’erreur. Un spécificateur d’union ou de structure est un identificateur de type `struct` ou `union` (un `typedef` nom ou une variable du même type que la structure ou l’union référencée). Le spécificateur doit être l’opérande gauche du premier opérateur de sélection de membres (.) pour utiliser l’opérande.