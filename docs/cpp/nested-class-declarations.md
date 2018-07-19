---
title: Déclarations de classes imbriquées | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- classes [C++], declaring
- declarations, class
- nested classes [C++]
- nested classes [C++], declaring
- declaring classes [C++]
- declarations, nested classes
ms.assetid: c02e471d-b7f9-41b8-8ef6-2323f006dbd5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 86c61792ab20bc0c10c9297d2a66588dd3c066ef
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942729"
---
# <a name="nested-class-declarations"></a>Déclarations de classes imbriquées
Une classe peut être déclarée dans la portée d'une autre classe. Il s'agit d'une « classe imbriquée ». Les classes imbriquées sont prises dans la portée de la classe englobante et peuvent être utilisées dans cette portée. Pour faire référence à une classe imbriquée à partir d'une portée différente de sa portée englobante immédiate, vous devez utiliser un nom qualifié complet.  
  
 L'exemple suivant montre comment déclarer des classes imbriquées :  
  
```cpp 
// nested_class_declarations.cpp  
class BufferedIO  
{  
public:  
   enum IOError { None, Access, General };  
  
   // Declare nested class BufferedInput.  
   class BufferedInput  
   {  
   public:  
      int read();  
      int good()  
      {  
         return _inputerror == None;  
      }  
   private:  
       IOError _inputerror;  
   };  
  
   // Declare nested class BufferedOutput.  
   class BufferedOutput  
   {  
      // Member list  
   };  
};  
  
int main()  
{  
}  
```  
  
 `BufferedIO::BufferedInput` et `BufferedIO::BufferedOutput` sont déclarées dans `BufferedIO`. Ces noms de classe ne sont pas visibles en dehors de la portée de la classe `BufferedIO`. Toutefois, un objet de type `BufferedIO` ne contient aucun objet de type `BufferedInput` ou `BufferedOutput`.  
  
 Les classes imbriquées ne peuvent utiliser directement les noms, les noms de types, les noms des membres statiques et les énumérateurs qu'à partir de la classe englobante. Pour utiliser des noms d'autres membres de classe, vous devez utiliser des pointeurs, les références ou des noms d'objet.  
  
 Dans l'exemple `BufferedIO` précédent, l'énumération `IOError` est accessible directement par les fonctions membres des classes imbriquées, `BufferedIO::BufferedInput` ou `BufferedIO::BufferedOutput`, comme indiqué dans la fonction `good`.  
  
> [!NOTE]
>  Les classes imbriquées déclarent uniquement des types dans la portée de classe. Elles n'entraînent pas la création d'objets contenus de la classe imbriquée. L'exemple précédent déclare deux classes imbriquées mais ne déclare aucun objet de ces types de classe.  
  
 Il existe une exception à la visibilité de portée d'une déclaration de classe imbriquée : lorsqu'un nom de type est déclaré avec une déclaration anticipée.  Dans ce cas, le nom de classe déclaré par la déclaration anticipée est visible en dehors de la classe englobante, sa portée étant définie de telle sorte qu'elle est la plus petite portée englobante sans classe.  Exemple :  
  
```cpp 
// nested_class_declarations_2.cpp  
class C  
{  
public:  
    typedef class U u_t; // class U visible outside class C scope  
    typedef class V {} v_t; // class V not visible outside class C  
};  
  
int main()  
{  
    // okay, forward declaration used above so file scope is used  
    U* pu;  
  
    // error, type name only exists in class C scope  
    u_t* pu2; // C2065  
  
    // error, class defined above so class C scope  
    V* pv; // C2065  
  
    // okay, fully qualified name  
    C::V* pv2;  
}  
```  
  
## <a name="access-privilege-in-nested-classes"></a>Privilège d'accès dans les classes imbriquées  
 Le fait d'imbriquer une classe dans une autre classe ne donne pas de privilèges d'accès spécifiques aux fonctions membres de la classe imbriquée. De même, les fonctions membres de la classe englobante ne disposent d'aucun accès spécial aux membres de la classe imbriquée.  
  
## <a name="member-functions-in-nested-classes"></a>Fonctions membres dans les classes imbriquées  
 Les fonctions membres déclarées dans des classes imbriquées peuvent être définies dans la portée du fichier. L'exemple précédent pourrait avoir été écrit comme suit :  
  
```cpp 
// member_functions_in_nested_classes.cpp  
class BufferedIO  
{  
public:  
    enum IOError { None, Access, General };  
    class BufferedInput  
    {  
    public:  
        int read(); // Declare but do not define member  
        int good(); //  functions read and good.  
    private:  
        IOError _inputerror;  
    };  
  
    class BufferedOutput  
    {  
        // Member list.  
    };  
};  
// Define member functions read and good in  
//  file scope.  
int BufferedIO::BufferedInput::read()  
{  
   return(1);  
}  
  
int BufferedIO::BufferedInput::good()  
{  
    return _inputerror == None;  
}  
int main()  
{  
}  
```  
  
 Dans l’exemple précédent, le *qualified-type-name* syntaxe est utilisée pour déclarer le nom de fonction. La déclaration :  
  
```cpp 
BufferedIO::BufferedInput::read()  
```  
  
 signifie « la fonction `read` qui est membre de la classe `BufferedInput` qui est dans la portée de la classe `BufferedIO`  ». Étant donné que cette déclaration utilise le *qualified-type-name* syntaxe, les constructions de la forme suivante sont possibles :  
  
```cpp 
typedef BufferedIO::BufferedInput BIO_INPUT;  
  
int BIO_INPUT::read()  
```  
  
 La déclaration précédente équivaut au précédent, mais il utilise un **typedef** nom à la place des noms de classes.  
  
## <a name="friend-functions-in-nested-classes"></a>Fonctions friend dans les classes imbriquées  
 Les fonctions friend déclarées dans une classe imbriquée sont considérées comme étant dans la portée de la classe imbriquée, pas dans la classe englobante. Par conséquent, les fonctions friend ne comprennent pas de privilèges d'accès spéciaux sur les membres ou les fonctions membres de la classe englobante. Si vous souhaitez utiliser un nom déclaré dans une classe imbriquée dans une fonction friend et que la fonction friend est définie dans la portée du fichier, utilisez les noms de types qualifiés comme suit :  
  
```cpp 
// friend_functions_and_nested_classes.cpp  
  
#include <string.h>  
  
enum  
{  
    sizeOfMessage = 255  
};  
  
char *rgszMessage[sizeOfMessage];  
  
class BufferedIO  
{  
public:  
    class BufferedInput  
    {  
    public:  
        friend int GetExtendedErrorStatus();  
        static char *message;  
        static int  messageSize;  
        int iMsgNo;  
   };  
};  
  
char *BufferedIO::BufferedInput::message;  
int BufferedIO::BufferedInput::messageSize;  
  
int GetExtendedErrorStatus()  
{  
    int iMsgNo = 1; // assign arbitrary value as message number  
  
    strcpy_s( BufferedIO::BufferedInput::message,  
              BufferedIO::BufferedInput::messageSize,  
              rgszMessage[iMsgNo] );  
  
    return iMsgNo;  
}  
  
int main()  
{  
}  
```  
  
 Le code suivant illustre la fonction `GetExtendedErrorStatus` déclarée comme fonction friend. Dans la fonction, définie dans la portée du fichier, un message est copié d'un tableau statique dans un membre de classe. Notez qu'une meilleure implémentation de `GetExtendedErrorStatus` consiste à le déclarer comme suit :  
  
```cpp 
int GetExtendedErrorStatus( char *message )  
```  
  
 Avec l'interface précédente, plusieurs classes peuvent utiliser les services de cette fonction en passant par un emplacement en mémoire où ils souhaitent copier le message d'erreur.  
  
## <a name="see-also"></a>Voir aussi  
 [Classes et structs](../cpp/classes-and-structs-cpp.md)