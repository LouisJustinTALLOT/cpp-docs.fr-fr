---
title: Concepts de base dans l'utilisation des exceptions managées
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch exception handling, managed applications
- __finally keyword, managed exceptions
- exceptions, managed
- try-catch exception handling
- catch blocks
- throwing exceptions, managed exceptions
- Visual C++, handling managed exceptions
ms.assetid: 40ce8931-1ecc-491a-815f-733b23fcba35
ms.openlocfilehash: 4eeec5db00ceca5429f4a3a270e1b249a8955249
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230920"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Concepts de base dans l'utilisation des exceptions managées

Cette rubrique traite de la gestion des exceptions dans les applications managées. Autrement dit, une application compilée avec l’option de compilateur **/CLR** .

## <a name="in-this-topic"></a>Dans cette rubrique

- [Levée d’exceptions sous/CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Blocs try/catch pour les extensions CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Notes

Si vous compilez avec l’option **/CLR** , vous pouvez gérer les exceptions CLR, ainsi que la classe standard, qui <xref:System.Exception> fournit de nombreuses méthodes utiles pour traiter les exceptions CLR et est recommandée comme classe de base pour les classes d’exceptions définies par l’utilisateur.

L’interception des types d’exception dérivés d’une interface n’est pas prise en charge sous **/CLR**. En outre, la common language runtime ne vous permet pas d’intercepter les exceptions de dépassement de capacité de la pile. une exception de dépassement de capacité de la pile met fin au processus.

Pour plus d’informations sur les différences de gestion des exceptions dans les applications managées et non managées, consultez [différences dans le comportement de gestion des exceptions sous extensions managées pour C++](../dotnet/differences-in-exception-handling-behavior-under-clr.md).

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Levée d’exceptions sous/CLR

L’expression Throw C++ est étendue pour lever un handle vers un type CLR. L’exemple suivant crée un type d’exception personnalisé, puis lève une instance de ce type :

```cpp
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

Un type valeur doit être boxed avant d’être levé :

```cpp
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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Blocs try/catch pour les extensions CLR

La même **`try`** / **`catch`** structure de bloc peut être utilisée pour intercepter les exceptions CLR et natives :

```cpp
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

### <a name="output"></a>Output

```
In 'catch(CMyClass& catchC)'
2
In 'catch(MyStruct^ catchException)'
11
```

### <a name="order-of-unwinding-for-c-objects"></a>Ordre de déroulement pour les objets C++

Le déroulement se produit pour tous les objets C++ avec des destructeurs qui peuvent se trouver sur la pile Runtime entre la fonction de levée et la fonction de gestion. Étant donné que les types CLR sont alloués sur le tas, le déroulement ne s’applique pas à eux.

L’ordre des événements pour une exception levée est le suivant :

1. Le runtime parcourt la pile à la recherche de la clause catch appropriée, ou, dans le cas de SEH, un filtre Except pour SEH, afin d’intercepter l’exception. Les clauses catch sont recherchées en premier dans l’ordre lexical, puis diminuent dynamiquement la pile des appels.

1. Une fois que le gestionnaire approprié est trouvé, la pile est déroulée jusqu’à ce point. Pour chaque appel de fonction sur la pile, ses objets locaux sont détruits et __finally blocs sont exécutés, de la plus imbriquée à l’extérieur.

1. Une fois que la pile est déroulée, la clause catch est exécutée.

### <a name="catching-unmanaged-types"></a>Interception de types non managés

Lorsqu’un type d’objet non managé est levé, il est encapsulé avec une exception de type <xref:System.Runtime.InteropServices.SEHException> . Lors de la recherche de la **`catch`** clause appropriée, il existe deux possibilités.

- Si un type C++ natif est rencontré, l’exception est désencapsulée et comparée au type rencontré. Cette comparaison permet d’intercepter un type C++ natif de manière normale.

- Toutefois, si une **`catch`** clause de type **SEHException** ou l’une de ses classes de base est examinée en premier, la clause intercepte l’exception. Par conséquent, vous devez placer toutes les clauses catch qui interceptent les types C++ natifs avant toute clause catch de types CLR.

Notez les points suivants :

```
catch(Object^)
```

et

```
catch(...)
```

interceptent tous deux le type levé, y compris les exceptions SEH.

Si un type non managé est intercepté par catch (Object ^), il ne détruit pas l’objet levé.

Lors de la génération ou de l’interception des exceptions non managées, nous vous recommandons d’utiliser l’option de compilateur [/EHsc](../build/reference/eh-exception-handling-model.md) au lieu de **/EHS** ou **/EHa**.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)
