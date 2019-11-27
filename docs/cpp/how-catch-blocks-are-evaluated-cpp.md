---
title: Mode d'évaluation des blocs Catch (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 027dc87923a588ea891dbf6dd835e2baba75a1cb
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245853"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Mode d'évaluation des blocs Catch (C++)

C++ vous permet de lever des exceptions de tout type, bien qu'en général il soit recommandé de lever des types dérivés de std::exception. Une C++ exception peut être interceptée par un gestionnaire **catch** qui spécifie le même type que l’exception levée, ou par un gestionnaire qui peut intercepter tout type d’exception.

Si le type de l'exception levée est une classe, qui possède également une classe (ou des classes) de base, elle peut être interceptée par des gestionnaires qui acceptent les classes de base du type de l'exception, ainsi que des références aux bases du type de l'exception. Notez que lorsqu'une exception est interceptée par une référence, elle est associée à l'objet exception levée réel. Dans le cas contraire, il s'agit d'une copie (similaire à un argument pour une fonction).

Lorsqu’une exception est levée, elle peut être interceptée par les types de gestionnaires **catch** suivants :

- Gestionnaire capable d'accepter tout type (à l'aide de la syntaxe avec points de suspension).

- Gestionnaire qui accepte le même type que l’objet exception ; étant donné qu’il s’agit d’une copie, les modificateurs **const** et **volatile** sont ignorés.

- Gestionnaire qui accepte une référence au même type que l'objet exception.

- Gestionnaire qui accepte une référence à une forme **const** ou **volatile** du même type que l’objet exception.

- Gestionnaire qui accepte une classe de base du même type que l’objet exception ; étant donné qu’il s’agit d’une copie, les modificateurs **const** et **volatile** sont ignorés. Le gestionnaire **catch** pour une classe de base ne doit pas précéder le gestionnaire **catch** pour la classe dérivée.

- Gestionnaire qui accepte une référence à une classe de base du même type que l'objet exception.

- Gestionnaire qui accepte une référence à une forme **const** ou **volatile** d’une classe de base du même type que l’objet exception.

- Gestionnaire qui accepte un pointeur vers lequel un objet pointeur levé peut être converti via des règles de conversion de pointeur standard.

L’ordre dans lequel les gestionnaires **catch** apparaissent est significatif, car les gestionnaires d’un bloc **try** donné sont examinés dans l’ordre de leur apparence. Par exemple, il est incorrect de placer le gestionnaire d'une classe de base avant le gestionnaire d'une classe dérivée. Une fois qu’un gestionnaire **catch** correspondant a été trouvé, les gestionnaires suivants ne sont pas examinés. Par conséquent, un gestionnaire **catch** de points de suspension doit être le dernier gestionnaire de son bloc **try** . Exemple :

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

Dans cet exemple, le gestionnaire **catch** de points de suspension est le seul gestionnaire examiné.

## <a name="see-also"></a>Voir aussi

[Meilleures C++ pratiques modernes pour les exceptions et la gestion des erreurs](../cpp/errors-and-exception-handling-modern-cpp.md)