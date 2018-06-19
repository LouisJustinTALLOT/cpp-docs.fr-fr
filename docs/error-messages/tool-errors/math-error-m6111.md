---
title: Erreur mathématique M6111 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6111
dev_langs:
- C++
helpviewer_keywords:
- M6111
ms.assetid: c0fc13f8-33c8-4e3f-a440-126cc623441b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3b03937ed442b169b960d573b44c0eb6ebca9660
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33317994"
---
# <a name="math-error-m6111"></a>Erreur mathématique M6111
dépassement de capacité négatif de pile  
  
 Une opération à virgule flottante a provoqué un dépassement de capacité de pile sur le coprocesseur 8087/287/387 ou l’émulateur.  
  
 Cette erreur est souvent due à un appel à une `long double` fonction qui ne retourne pas de valeur. Par exemple, la commande suivante génère cette erreur lorsque compilé et exécuté :  
  
```  
long double ld() {};  
main ()  
{  
  ld();  
}  
```  
  
 Programme se termine par le code de sortie 139.