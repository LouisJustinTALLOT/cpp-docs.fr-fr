---
title: Ce pointeur | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- this_cpp
dev_langs:
- C++
helpviewer_keywords:
- nonstatic member functions [C++]
- pointers, to class instance
- this pointer
ms.assetid: 92e3256a-4ad9-4d46-8be1-d77fad90791f
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 86ccf50a089b1497bdc166ee9367215dc59b3ca1
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="this-pointer"></a>Pointeur this
Le **cela** pointeur est accessible uniquement dans les fonctions membres non statiques d’un **classe**, `struct`, ou **union** type. Il pointe vers l'objet pour lequel la fonction membre est appelée. Les fonctions membres statiques n’ont pas un **cela** pointeur.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
      this   
this->member-identifier  
```  
  
## <a name="remarks"></a>Remarques  
 D’un objet **cela** pointeur ne fait pas partie de l’objet lui-même ; il n’est pas reflétée dans le résultat d’une `sizeof` instruction sur l’objet. En revanche, lorsqu’une fonction membre non statique est appelée pour un objet, l’adresse de l’objet est passée par le compilateur comme argument masqué à la fonction. Par exemple, l'appel de fonction suivant :  
  
```  
myDate.setMonth( 3 );  
```  
  
 peut être interprété de cette façon :  
  
```  
setMonth( &myDate, 3 );  
```  
  
 L’adresse de l’objet est accessible à partir de la fonction membre en tant que le **cela** pointeur. La plupart des utilisations de **cela** sont implicites. Il est permis, bien qu’inutile d’utiliser explicitement **cela** lorsque vous faites référence aux membres de la classe. Exemple :  
  
```  
void Date::setMonth( int mn )  
{  
   month = mn;            // These three statements  
   this->month = mn;      // are equivalent  
   (*this).month = mn;  
}  
```  
  
 L'expression `*this` est utilisée couramment pour retourner l'objet actuel d'une fonction membre :  
  
```  
return *this;  
```  
  
 Le **cela** pointeur est également utilisé pour se protéger contre les autoréférences :  
  
```  
if (&Object != this) {  
// do not execute in cases of self-reference  
```  
  
> [!NOTE]
>  Étant donné que la **cela** pointeur non modifiable, assignations en vue de **cela** ne sont pas autorisés. Les implémentations précédentes de C++ autorisaient les assignations à **cela**.  
  
 Parfois, le **cela** pointeur est utilisé directement, par exemple, pour manipuler les données elles-mêmes les structures, où l’adresse de l’objet actuel est requis.  
  
## <a name="example"></a>Exemple  
  
```  
// this_pointer.cpp  
// compile with: /EHsc  
  
#include <iostream>  
#include <string.h>  
  
using namespace std;  
  
class Buf   
{  
public:  
    Buf( char* szBuffer, size_t sizeOfBuffer );  
    Buf& operator=( const Buf & );  
    void Display() { cout << buffer << endl; }  
  
private:  
    char*   buffer;  
    size_t  sizeOfBuffer;  
};  
  
Buf::Buf( char* szBuffer, size_t sizeOfBuffer )  
{  
    sizeOfBuffer++; // account for a NULL terminator  
  
    buffer = new char[ sizeOfBuffer ];  
    if (buffer)  
    {  
        strcpy_s( buffer, sizeOfBuffer, szBuffer );  
        sizeOfBuffer = sizeOfBuffer;  
    }  
}  
  
Buf& Buf::operator=( const Buf &otherbuf )   
{  
    if( &otherbuf != this )   
    {  
        if (buffer)  
            delete [] buffer;  
  
        sizeOfBuffer =  strlen( otherbuf.buffer ) + 1;   
        buffer = new char[sizeOfBuffer];  
        strcpy_s( buffer, sizeOfBuffer, otherbuf.buffer );  
    }  
    return *this;  
}  
  
int main()  
{  
    Buf myBuf( "my buffer", 10 );  
    Buf yourBuf( "your buffer", 12 );  
  
    // Display 'my buffer'  
    myBuf.Display();  
  
    // assignment opperator  
    myBuf = yourBuf;  
  
    // Display 'your buffer'  
    myBuf.Display();  
}  
```  
  
```Output  
my buffer  
your buffer  
```  
  
## <a name="type-of-the-this-pointer"></a>Type du pointeur this  
 Le **cela** type de pointeur peut être modifié dans la déclaration de fonction par le **const** et `volatile` mots clés. Pour déclarer une fonction comme ayant les attributs d’un ou plusieurs de ces mots clés, ajoutez le ou les mots clés après la liste d’arguments de la fonction.  
  
 Considérez cet exemple :  
  
```  
// type_of_this_pointer1.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Le code précédent déclare une fonction membre, `X`, dans lequel le **cela** pointeur est traité comme un **const** pointeur vers un **const** objet. Combinaisons de *cv-mod-list* options peuvent être utilisées, mais elles modifient toujours l’objet vers lequel pointé **cela**, et non le **cela** pointeur lui-même. Par conséquent, la déclaration suivante déclare la fonction `X`; le **cela** pointeur est un **const** pointeur vers un **const** objet :  
  
```  
// type_of_this_pointer2.cpp  
class Point  
{  
    unsigned X() const;  
};  
int main()  
{  
}  
```  
  
 Le type de **cela** un membre de la fonction est décrite par la syntaxe suivante, où *cv-qualifier-list* est déterminée par le déclarateur de fonctions membres et peut être **const**ou **volatile** (ou les deux), et *de type classe* est le nom de la classe :  
  
 *type de classe [cv-qualifier-list]* ** \* const cela  **  
  
 En d’autres termes, **cela** est toujours un pointeur const ; il ne peut pas être réassigné.  Le **const** ou `volatile` qualificateurs utilisés dans la déclaration de fonction membre s’appliquent à l’instance de classe vers laquelle pointé **cela** dans l’étendue de cette fonction.  
  
 Le tableau ci-dessous fournit davantage d'explications sur le fonctionnement de ces modificateurs.  
  
### <a name="semantics-of-this-modifiers"></a>Sémantique des modificateurs du pointeur this  
  
|Modificateur|Signification|  
|--------------|-------------|  
|**const**|Impossible de modifier les données membres ; Impossible d’appeler des fonctions membres qui ne sont pas **const**.|  
|`volatile`|Les données membres sont chargées à partir de la mémoire chaque fois que vous y accédez ; certaines optimisations sont désactivées.|  
  
 Il s’agit d’une erreur pour passer un **const** objet à une fonction membre qui n’est pas **const**. De même, il est incorrect de passer un objet `volatile` à une fonction membre qui n'est pas `volatile`.  
  
 Fonctions membres déclarées comme **const** ne peut pas modifier les données membres, dans ces fonctions, les **cela** pointeur est un pointeur vers un **const** objet.  
  
> [!NOTE]
>  Constructeurs et destructeurs ne peuvent pas être déclarés en tant que **const** ou `volatile`. Ils peuvent, toutefois, être appelée sur **const** ou `volatile` objets.  
  
## <a name="see-also"></a>Voir aussi  
 [Mots clés](../cpp/keywords-cpp.md)   
 
