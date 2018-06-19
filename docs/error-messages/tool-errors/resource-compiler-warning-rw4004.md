---
title: Avertissement RW4004 du compilateur de ressources | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW4004
dev_langs:
- C++
helpviewer_keywords:
- RW4004
ms.assetid: 596b6a89-9ce7-4ba7-bdcb-e8054c7efafa
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 94bd1c043ac5660c5cb8fc8b2bfa1dd2f6968b55
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33337104"
---
# <a name="resource-compiler-warning-rw4004"></a>Avertissement RW4004 du compilateur de ressources 
Caractère ASCII non équivalent au code de touche virtuelle  
  
 Vous avez utilisé un littéral de chaîne pour le code de touche virtuelle dans un accélérateur de type VIRTKEY.  
  
 Cet avertissement ne vous empêche pas de continuer, mais sachez que les touches accélérateur générées risquent de ne pas correspondre à la chaîne spécifiée. (Les VIRTKEY utilisent des codes de touches différents des accélérateurs ASCII.)  
  
 Tandis que les littéraux de chaîne sont valides, vous assurer que vous obtenez l’accélérateur souhaité à l’aide de la **VK_\* #define** valeurs dans WINDOWS.h.