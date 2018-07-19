---
title: Comment les blocs Catch sont évalués (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0190b62491dbb9d15ee4f01a1cbc4c2741f74dbe
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37943852"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Mode d'évaluation des blocs Catch (C++)
C++ vous permet de lever des exceptions de tout type, bien qu'en général il soit recommandé de lever des types dérivés de std::exception. Une exception C++ peut être interceptée par un **catch** gestionnaire qui spécifie le même type que l’exception levée, ou par un gestionnaire qui peut intercepter tout type d’exception.  
  
 Si le type de l'exception levée est une classe, qui possède également une classe (ou des classes) de base, elle peut être interceptée par des gestionnaires qui acceptent les classes de base du type de l'exception, ainsi que des références aux bases du type de l'exception. Notez que lorsqu’une exception est interceptée par une référence, elle est associée à l’objet exception levée réel. Dans le cas contraire, il s’agit d’une copie (similaire à un argument pour une fonction).  
  
 Lorsqu’une exception est levée, elle peut être interceptée par les types suivants de **catch** gestionnaires :  
  
-   Gestionnaire capable d'accepter tout type (à l'aide de la syntaxe avec points de suspension).  
  
-   Gestionnaire qui accepte le même type que l’objet exception. s’agissant d’une copie, **const** et **volatile** modificateurs sont ignorés.  
  
-   Gestionnaire qui accepte une référence au même type que l'objet exception.  
  
-   Un gestionnaire qui accepte une référence à un **const** ou **volatile** formulaire du même type que l’objet exception.  
  
-   Gestionnaire qui accepte une classe de base du même type que l’objet exception. puisqu’il s’agit d’une copie, **const** et **volatile** modificateurs sont ignorés. Le **catch** gestionnaire pour une classe de base ne doit pas précéder le **catch** gestionnaire pour la classe dérivée.  
  
-   Gestionnaire qui accepte une référence à une classe de base du même type que l'objet exception.  
  
-   Un gestionnaire qui accepte une référence à un **const** ou **volatile** forme d’une classe de base du même type que l’objet exception.  
  
-   Gestionnaire qui accepte un pointeur vers lequel un objet pointeur levé peut être converti via des règles de conversion de pointeur standard.  
  
 L’ordre dans lequel **catch** gestionnaires apparaissent est significatif, étant donné que gestionnaires pour une donnée **essayez** bloc sont examinés dans leur ordre d’apparition. Par exemple, il est incorrect de placer le gestionnaire d'une classe de base avant le gestionnaire d'une classe dérivée. Après une mise en correspondance **catch** gestionnaire est trouvé, les gestionnaires suivants ne sont pas examinés. Par conséquent, les points de suspension **catch** gestionnaire doit être le dernier gestionnaire son **essayez** bloc. Exemple :  
  
```cpp 
// ...  
try  
{  
    // ...  
}  
catch( ... )  
{  
    // Handle exception here.  
}  
// Error: the next two handlers are never examined.  
catch( const char * str )  
{  
    cout << "Caught exception: " << str << endl;  
}  
catch( CExcptClass E )  
{  
    // Handle CExcptClass exception here.  
}  
```  
  
 Dans cet exemple, les points de suspension **catch** gestionnaire est le seul gestionnaire qui est examiné.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion d’exceptions C++](../cpp/cpp-exception-handling.md)