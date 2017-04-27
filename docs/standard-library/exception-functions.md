---
title: '&lt;exception&gt;, fonctions | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
caps.latest.revision: 12
manager: ghogen
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 08d2a2161a2596cebb27175c55023d5313c7b908
ms.lasthandoff: 02/24/2017

---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt;, fonctions
||||  
|-|-|-|  
|[current_exception](#current_exception)|[get_terminate](#get_terminate)|[get_unexpected](#get_unexpected)|  
|[make_exception_ptr](#make_exception_ptr)|[rethrow_exception](#rethrow_exception)|[set_terminate](#set_terminate)|  
|[set_unexpected](#set_unexpected)|[terminate](#terminate)|[uncaught_exception](#uncaught_exception)|  
|[unexpected](#unexpected)|  
  
##  <a name="current_exception"></a>  current_exception  
 Obtient un pointeur intelligent vers l'exception actuelle.  
  
```cpp  
exception_ptr current_exception();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Objet [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui pointe vers l’exception actuelle.  
  
### <a name="remarks"></a>Notes  
 Appelez la fonction `current_exception` dans un bloc catch. Si une exception a été levée et si le bloc catch peut l'intercepter, la fonction `current_exception` retourne un objet `exception_ptr` qui référence l'exception. Sinon, la fonction retourne un objet `exception_ptr` null.  
  
 La fonction `current_exception` capture l’exception en vol même si l’instruction `catch` spécifie une instruction [exception-declaration](../cpp/try-throw-and-catch-statements-cpp.md).  
  
 Le destructeur de l'exception actuelle est appelé à la fin du bloc `catch` si vous n'avez pas levé à nouveau l'exception. Toutefois, même si vous appelez la fonction `current_exception` dans le destructeur, celle-ci retourne un objet `exception_ptr` qui référence l’exception actuelle.  
  
 Les appels successifs à la fonction `current_exception` retournent des objets `exception_ptr` qui font référence à des copies de l'exception actuelle. Par conséquent, les objets sont considérés comme inégaux car ils font référence à des copies, bien que les copies aient la même valeur binaire.  
  
##  <a name="make_exception_ptr"></a>  make_exception_ptr  
 Crée un objet [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui contient une copie d’une exception.  
  
```cpp  
template <class E>  
exception_ptr make_exception_ptr(E Except);
```  
  
### <a name="parameters"></a>Paramètres  
 `Except`  
 Classe avec l'exception à copier. Généralement, vous spécifiez un objet de [classe exception](../standard-library/exception-class.md) comme argument pour la fonction `make_exception_ptr`, bien que tout objet de classe puisse être l’argument.  
  
### <a name="return-value"></a>Valeur de retour  
 Objet [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) qui pointe vers une copie de l’exception actuelle pour `Except`.  
  
### <a name="remarks"></a>Notes  
 L’appel de la fonction `make_exception_ptr` équivaut à lever une exception C++, à l’intercepter dans un bloc catch, puis à appeler la fonction [current_exception](../standard-library/exception-functions.md#current_exception) pour retourner un objet `exception_ptr` qui référence l’exception. L'implémentation Microsoft de la fonction `make_exception_ptr` est plus efficace que le fait de lever puis d'intercepter une exception.  
  
 En général, une application ne requiert pas la fonction `make_exception_ptr`, et son utilisation est d'ailleurs déconseillée.  
  
##  <a name="rethrow_exception"></a>  rethrow_exception  
 Lève une exception passée comme paramètre.  
  
```cpp  
void rethrow_exception(exception_ptr P);
```  
  
### <a name="parameters"></a>Paramètres  
 `P`  
 L'exception interceptée à lever de nouveau. Si `P` est un [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) null, la fonction lève [std::bad_exception](../standard-library/bad-exception-class.md).  
  
### <a name="remarks"></a>Notes  
 Après avoir enregistré une exception interceptée dans un objet `exception_ptr`, le thread principal peut traiter l'objet. Dans votre thread principal, appelez la fonction `rethrow_exception` avec l'objet `exception_ptr` en tant qu'argument. La fonction `rethrow_exception` extrait l'exception de l'objet `exception_ptr` puis lève l'exception dans le contexte du thread principal.  
  
##  <a name="get_terminate"></a>  get_terminate  
 Obtient la fonction `terminate_handler` actuelle.  
  
```cpp  
terminate_handler get_terminate();
```  
  
##  <a name="set_terminate"></a>  set_terminate  
 Génère un nouvel appel à `terminate_handler` à l'arrêt du programme.  
  
```  
terminate_handler set_terminate(terminate_handler fnew) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `fnew`  
 La fonction doit être appelée à la fin.  
  
### <a name="return-value"></a>Valeur de retour  
 Adresse de la fonction précédente utilisée à appeler à la fin.  
  
### <a name="remarks"></a>Notes  
 La fonction établit un nouveau [terminate_handler](../standard-library/exception-typedefs.md#terminate_handler) comme la fonction * `fnew`. Par conséquent, `fnew` ne doit pas être un pointeur null. La fonction retourne l’adresse du gestionnaire d’arrêt précédent.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// exception_set_terminate.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
  
using namespace std;  
  
void termfunction()  
{  
    cout << "My terminate function called." << endl;  
    abort();  
}  
  
int main()  
{  
    terminate_handler oldHandler = set_terminate(termfunction);  
  
    // Throwing an unhandled exception would also terminate the program  
    // or we could explicitly call terminate();  
  
    //throw bad_alloc();  
    terminate();  
}  
  
```  
  
##  <a name="get_unexpected"></a>  get_unexpected  
 Obtient la fonction `unexpected_handler` actuelle.  
  
```cpp  
unexpected_handler get_unexpected();
```  
  
##  <a name="set_unexpected"></a>  set_unexpected  
 Génère un nouveau `unexpected_handler` à appeler en cas d'exception inattendue.  
  
```  
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```  
  
### <a name="parameters"></a>Paramètres  
 `fnew`  
 Fonction à appeler en cas d’exception inattendue.  
  
### <a name="return-value"></a>Valeur de retour  
 Adresse du `unexpected_handler` précédent.  
  
### <a name="remarks"></a>Notes  
 `fnew` ne doit pas être un pointeur null.  
  
 La norme C++ nécessite l’appel de `unexpected` quand une fonction lève une exception qui n’est pas dans sa liste d’exceptions à lever. L’implémentation actuelle ne le prend pas en charge. L’exemple suivant appelle `unexpected` directement, qui appelle ensuite le `unexpected_handler`.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// exception_set_unexpected.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
  
using namespace std;  
  
void uefunction()  
{  
    cout << "My unhandled exception function called." << endl;  
    terminate(); // this is what unexpected() calls by default  
}  
  
int main()  
{  
    unexpected_handler oldHandler = set_unexpected(uefunction);  
  
    unexpected(); // library function to force calling the   
                  // current unexpected handler  
}  
  
```  
  
##  <a name="terminate"></a>  terminate  
 Appelle un gestionnaire d'arrêt.  
  
```  
void terminate();
```  
  
### <a name="remarks"></a>Notes  
 La fonction appelle un gestionnaire d’arrêt, une fonction de type `void`. Si le programme appelle directement **terminate**, le gestionnaire d’arrêt est le dernier défini par un appel à [set_terminate](../standard-library/exception-functions.md#set_terminate). Si **terminate** est appelé pour d’autres raisons pendant l’évaluation d’une expression throw, le gestionnaire d’arrêt est celui qui est actif juste après l’évaluation de l’expression throw.  
  
 Un gestionnaire d’arrêt ne peut pas retourner à son appelant. Au démarrage du programme, le gestionnaire d’arrêt est une fonction qui appelle **abort**.  
  
### <a name="example"></a>Exemple  
  Consultez [set_unexpected](../standard-library/exception-functions.md#set_unexpected) pour obtenir un exemple d’utilisation de **terminate**.  
  
##  <a name="uncaught_exception"></a>  uncaught_exception  
 Retourne `true` uniquement si une exception levée est actuellement traitée.  
  
```  
bool uncaught_exception();
```  
  
### <a name="return-value"></a>Valeur de retour  
 Retourne `true` à la fin de l’évaluation d’une expression throw et avant la fin de l’initialisation de la déclaration d’exception dans le gestionnaire correspondant, ou en appelant [unexpected](../standard-library/exception-functions.md#unexpected) suite à l’expression throw. En particulier, `uncaught_exception` retourne `true` quand elle est appelée à partir d’un destructeur lui-même appelé pendant le déroulement d’une exception. Concernant les appareils, `uncaught_exception` est uniquement pris en charge sur Windows CE 5.00 et versions supérieures, notamment les plateformes Windows Mobile 2005.  
  
### <a name="example"></a>Exemple  
  
```cpp  
// exception_uncaught_exception.cpp  
// compile with: /EHsc  
#include <exception>  
#include <iostream>  
#include <string>  
  
class Test   
{  
public:  
   Test( std::string msg ) : m_msg( msg )   
   {  
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;  
   }  
   ~Test( )   
   {  
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl  
         << "        std::uncaught_exception( ) = "  
         << std::uncaught_exception( )  
         << std::endl;  
   }  
private:  
    std::string m_msg;  
};  
  
// uncaught_exception will be true in the destructor   
// for the object created inside the try block because   
// the destructor is being called as part of the unwind.  
  
int main( void )  
   {  
      Test t1( "outside try block" );  
      try   
      {  
         Test t2( "inside try block" );  
         throw 1;  
      }  
      catch (...) {  
   }  
}  
```  
  
```Output  
In Test::Test("outside try block")  
In Test::Test("inside try block")  
In Test::~Test("inside try block")  
        std::uncaught_exception( ) = 1  
In Test::~Test("outside try block")  
        std::uncaught_exception( ) = 0  
```  
  
##  <a name="unexpected"></a>  unexpected  
 Appelle le gestionnaire d’exceptions inattendues.  
  
```  
void unexpected();
```  
  
### <a name="remarks"></a>Notes  
 La norme C++ nécessite l’appel de `unexpected` quand une fonction lève une exception qui n’est pas dans sa liste d’exceptions à lever. L’implémentation actuelle ne le prend pas en charge. L’exemple appelle `unexpected` directement, qui appelle le gestionnaire d’exceptions inattendues.  
  
 La fonction appelle un gestionnaire d’exceptions inattendues, une fonction de type `void`. Si le programme appelle directement `unexpected`, le gestionnaire d’exceptions inattendues est le dernier défini par un appel à [set_unexpected](../standard-library/exception-functions.md#set_unexpected).  
  
 Un gestionnaire d’exceptions inattendues ne peut pas retourner à son appelant. Il peut mettre fin à l’exécution en effectuant l’une des opérations suivantes :  
  
-   Levée d’un objet d’un type répertorié dans la spécification d’exception ou d’un objet de n’importe quel type, si le programme appelle directement le gestionnaire d’exceptions inattendues.  
  
-   Levée d’un objet de type [bad_exception](../standard-library/bad-exception-class.md).  
  
-   Appel de [terminate](../standard-library/exception-functions.md#terminate), **abort** ou **exit**( `int`).  
  
 Au démarrage du programme, le gestionnaire d’exceptions inattendues est une fonction qui appelle [terminate](../standard-library/exception-functions.md#terminate).  
  
### <a name="example"></a>Exemple  
  Consultez [set_unexpected](../standard-library/exception-functions.md#set_unexpected) pour obtenir un exemple d’utilisation de **unexpected.**  
  
## <a name="see-also"></a>Voir aussi  
 [\<exception>](../standard-library/exception.md)


