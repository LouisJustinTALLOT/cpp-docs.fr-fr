---
title: 'Exemple d’appel : Prototype et appel de fonction | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2fcfda308ed3a5723b32729e7986a7063e9928fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32409369"
---
# <a name="calling-example-function-prototype-and-call"></a>Exemple d'appel : Prototype et appel de fonction
## <a name="microsoft-specific"></a>Section spécifique à Microsoft  
 L’exemple suivant montre les résultats d’un appel de fonction effectué à l’aide de différentes conventions d’appel.  
  
 Cet exemple repose sur la structure de fonction suivante. Remplacez `calltype` par la convention d'appel appropriée.  
  
```  
void    calltype MyFunc( char c, short s, int i, double f );  
.  
.  
.  
void    MyFunc( char c, short s, int i, double f )  
    {  
    .  
    .  
    .  
    }  
.  
.  
.  
MyFunc ('x', 12, 8192, 2.7183);  
```  
  
 Pour plus d’informations, consultez [résultats de l’appel exemple](../cpp/results-of-calling-example.md).  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [Conventions d’appel](../cpp/calling-conventions.md)