---
title: Point de déclaration en C++ | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- point of declaration
ms.assetid: 92ea8707-80cb-497c-b479-f907b8401859
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e42f43e6187e19df6e9c1111c0e92aa4b9929199
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="point-of-declaration-in-c"></a>Point de déclaration en C++
Un nom est considéré comme déclaré immédiatement après son déclarateur mais avant son initialiseur (facultatif). (Pour plus d’informations sur les déclarateurs, consultez [déclarations et définitions](declarations-and-definitions-cpp.md).)  
  
 Considérez cet exemple :  
  
```  
// point_of_declaration1.cpp  
// compile with: /W1   
double dVar = 7.0;  
int main()  
{  
   double dVar = dVar;   // C4700  
}  
```  
  
 Si le point de déclaration ont été *après* l’initialisation, puis local `dVar` serait initialisée à 7,0, la valeur de la variable globale `dVar`. Toutefois, comme ce n'est pas le cas, `dVar` est initialisé avec une valeur non définie.  
  
## <a name="see-also"></a>Voir aussi  
 [Portée](../cpp/scope-visual-cpp.md)