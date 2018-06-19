---
title: Concepts de base à l’aide des Exceptions managées | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 255a7d053228b73b2b0eb13f4732e9a7829549ba
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33114482"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Concepts de base dans l'utilisation des exceptions managées
Cette rubrique décrit la gestion des exceptions dans les applications managées. Autrement dit, une application qui est compilée avec le **/CLR** option du compilateur.  
  
## <a name="in-this-topic"></a>Dans cette rubrique  
  
-   [Lever des Exceptions sous /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)  
  
-   [Blocs Try/Catch pour les Extensions CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)  
  
## <a name="remarks"></a>Notes  
 Si vous compilez avec le **/CLR** option, vous pouvez gérer les exceptions CLR ainsi que la norme [gestion des exceptions C++](../cpp/cpp-exception-handling.md) et [structurée des exceptions](../cpp/structured-exception-handling-c-cpp.md) (SEH). Une exception CLR est une exception levée par un type managé. Le [System::Exception](https://msdn.microsoft.com/en-us/library/system.exception.aspx) classe fournit de nombreuses méthodes utiles pour le traitement des exceptions CLR et qu’il est recommandé d’utiliser une classe de base pour les classes d’exception définie par l’utilisateur.  
  
 Intercepter des types d’exception dérivés d’une interface n’est pas pris en charge sous **/CLR**. En outre, le common language runtime ne vous autorise pas à intercepter les exceptions de dépassement de capacité de pile ; le processus prendra fin à une exception de dépassement de capacité de pile.  
  
 Pour plus d’informations sur les différences dans la gestion des exceptions dans les applications managées et non managées, consultez [les différences dans l’Exception gestion comportement sous les Extensions managées pour C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a> Lever des Exceptions sous /clr  
 L’expression throw de C++ est étendue pour lever un handle à un type CLR. L’exemple suivant crée un type d’exception personnalisé et puis lève une instance de ce type :  
  
```  
// clr_exception_handling.cpp  
// compile with: /clr /c  
ref struct MyStruct: public System::Exception {  
public:  
   int i;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   throw pMyStruct;  
}  
```  
  
 Un type valeur doit être convertie (boxed) avant de levée :  
  
```  
// clr_exception_handling_2.cpp  
// compile with: /clr /c  
value struct MyValueStruct {  
   int i;  
};  
  
void GlobalFunction() {  
   MyValueStruct v = {11};  
   throw (MyValueStruct ^)v;  
}  
```  
  
##  <a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a> Blocs Try/Catch pour les Extensions CLR  
 Le même **essayez**/**catch** structure de bloc peut être utilisée pour intercepter les exceptions natives et CLR :  
  
```  
// clr_exception_handling_3.cpp  
// compile with: /clr  
using namespace System;  
ref struct MyStruct : public Exception {  
public:  
   int i;  
};  
  
struct CMyClass {  
public:  
   double d;  
};  
  
void GlobalFunction() {  
   MyStruct^ pMyStruct = gcnew MyStruct;  
   pMyStruct->i = 11;  
   throw pMyStruct;  
}  
  
void GlobalFunction2() {  
   CMyClass c = {2.0};  
   throw c;  
}  
  
int main() {  
   for ( int i = 1; i >= 0; --i ) {  
      try {  
         if ( i == 1 )  
            GlobalFunction2();  
         if ( i == 0 )  
            GlobalFunction();  
      }  
      catch ( CMyClass& catchC ) {  
         Console::WriteLine( "In 'catch(CMyClass& catchC)'" );  
         Console::WriteLine( catchC.d );  
      }  
      catch ( MyStruct^ catchException ) {  
         Console::WriteLine( "In 'catch(MyStruct^ catchException)'" );  
         Console::WriteLine( catchException->i );  
      }  
   }  
}  
```  
  
### <a name="output"></a>Sortie  
  
```  
In 'catch(CMyClass& catchC)'  
2  
In 'catch(MyStruct^ catchException)'  
11  
```  
  
### <a name="order-of-unwinding-for-c-objects"></a>Ordre de désempilage des objets C++  
 Le déroulement se produit pour tous les objets C++ avec des destructeurs qui peut se trouver sur la pile d’exécution entre la fonction de levée et la fonction de gestion. Étant donné que les types CLR sont alloués sur le tas, le déroulement ne concerne pas les.  
  
 L’ordre des événements pour une exception levée est comme suit :  
  
1.  Le runtime parcourt la pile de recherche de la clause catch appropriée, ou dans le cas de gestion structurée des exceptions, une à l’exception de filtre pour la gestion structurée des exceptions, pour intercepter l’exception. Clauses catch sont recherchés en premier dans l’ordre lexical et puis dynamiquement vers le bas la pile des appels.  
  
2.  Une fois que le gestionnaire approprié est trouvé, la pile est déroulée à ce point. Pour chaque appel de fonction sur la pile, ses objets locaux sont détruites et __finally blocs sont exécutés à partir de la plupart imbriqué vers l’extérieur.  
  
3.  Une fois que la pile est déroulée, la clause catch est exécutée.  
  
### <a name="catching-unmanaged-types"></a>Intercepter des Types non managés  
 Lorsqu’un type d’objet non managé est levé, il est encapsulé avec une exception de type [InteropServices::SEHException](https://msdn.microsoft.com/en-us/library/system.runtime.interopservices.sehexception.aspx). Lorsque vous recherchez approprié **catch** clause, il existe deux possibilités.  
  
-   Si un type C++ natif est rencontré, l’exception est désencapsulée et par rapport au type rencontré. Cette comparaison permet à un type C++ natif au cours de façon normale.  
  
-   Toutefois, si un **catch** clause de type **SEHException** ou une de ses classes de base est examiné en premier, la clause intercepte l’exception. Par conséquent, vous devez placer toutes les clauses catch qui interceptent les types C++ natifs tout d’abord, avant toute clause catch des types CLR.  
  
 Notez les points suivants :  
  
```  
catch(Object^)  
```  
  
 et  
  
```  
catch(...)  
```  
  
 les deux interceptera n’importe quel type levé, y compris les exceptions SEH.  
  
 Si un type non managé est intercepté par catch(Object^), il ne sera pas détruire l’objet levée.  
  
 Lors de la levée ou l’interception non gérés exceptions, nous vous recommandons d’utiliser le [/EHsc](../build/reference/eh-exception-handling-model.md) option du compilateur au lieu de **/EHs** ou **/EHa**.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des exceptions](../windows/exception-handling-cpp-component-extensions.md)   
 [safe_cast](../windows/safe-cast-cpp-component-extensions.md)   
 [Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)