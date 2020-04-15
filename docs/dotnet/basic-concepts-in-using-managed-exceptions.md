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
ms.openlocfilehash: 6bc1e9c6d40599ae9a821179dcf56dbb7e21bf10
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372526"
---
# <a name="basic-concepts-in-using-managed-exceptions"></a>Concepts de base dans l'utilisation des exceptions managées

Ce sujet traite le traitement des exceptions dans les applications gérées. Autrement dit, une application qui est compilée avec l’option **compilateur /clr.**

## <a name="in-this-topic"></a>Dans cette rubrique

- [Exceptions de lancement sous /clr](#vcconbasicconceptsinusingmanagedexceptionsanchor1)

- [Essayez/Catch Blocks pour les extensions CLR](#vcconbasicconceptsinusingmanagedexceptionsanchor2)

## <a name="remarks"></a>Notes

Si vous compilez avec **l’option /clr,** vous pouvez <xref:System.Exception> gérer les exceptions CLR ainsi que la classe standard fournit de nombreuses méthodes utiles pour le traitement des exceptions CLR et est recommandé comme une classe de base pour les classes d’exception définies par l’utilisateur.

Attraper les types d’exception dérivés d’une interface n’est pas pris en charge sous **/clr**. En outre, l’heure courante de course de langue ne vous permet pas d’attraper des exceptions de débordement de pile ; une exception de débordement de pile mettra fin au processus.

Pour plus d’informations sur les différences dans le traitement des exceptions dans les applications gérées et non [gérées, voir Différences dans le comportement de traitement d’exception sous extensions gérées pour C .](../dotnet/differences-in-exception-handling-behavior-under-clr.md)

## <a name="throwing-exceptions-under-clr"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor1"></a>Exceptions de lancement sous /clr

L’expression de lancer de C est étendue pour jeter une poignée à un type CLR. L’exemple suivant crée un type d’exception personnalisé, puis jette une instance de ce type :

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

Un type de valeur doit être mis en boîte avant d’être jeté :

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

## <a name="trycatch-blocks-for-clr-extensions"></a><a name="vcconbasicconceptsinusingmanagedexceptionsanchor2"></a>Essayez/Catch Blocks pour les extensions CLR

La même structure de bloc de capture **d’essai**/**catch** peut être employée pour attraper des exceptions de CLR et indigènes :

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

### <a name="order-of-unwinding-for-c-objects"></a>Ordre de dénouement pour les objets C

Le dénouement se produit pour tous les objets C avec destructors qui peuvent être sur la pile de temps de fonctionnement entre la fonction de lancer et la fonction de manipulation. Étant donné que les types de CLR sont attribués sur le tas, le dénouement ne s’applique pas à eux.

L’ordre des événements pour une exception jetée est le suivant :

1. Le temps d’exécution marche la pile à la recherche de la clause de capture appropriée, ou dans le cas de SEH, un filtre à l’exception de SEH, pour attraper l’exception. Les clauses de capture sont recherchées d’abord dans l’ordre lexical, puis dynamiquement vers le bas de la pile d’appel.

1. Une fois que le gestionnaire correct est trouvé, la pile est dénouée à ce point. Pour chaque appel de fonction sur la pile, ses objets locaux sont détruits et __finally blocs sont exécutés, de la plupart imbriqués vers l’extérieur.

1. Une fois que la pile est dénouée, la clause de capture est exécutée.

### <a name="catching-unmanaged-types"></a>Attraper les types non-manés

Lorsqu’un type d’objet non traité est lancé, <xref:System.Runtime.InteropServices.SEHException>il est enveloppé à l’exception du type. Lors de la recherche de la clause **de capture** appropriée, il ya deux possibilités.

- Si un type natif de CMD est rencontré, l’exception est déballée et comparée au type rencontré. Cette comparaison permet de prendre un type CMD natif de la manière normale.

- Toutefois, si une clause de **capture** de type **SEHException** ou l’une de ses classes de base est examinée en premier, la clause interceptera l’exception. Par conséquent, vous devez placer toutes les clauses de capture qui attrapent les types natifs de CMD d’abord avant toute clause de capture des types de CLR.

Notez les points suivants :

```
catch(Object^)
```

and

```
catch(...)
```

attrapera tous les deux n’importe quel type jeté comprenant des exceptions SEH.

Si un type non menté est pris par la capture (Objet), il ne détruira pas l’objet lancé.

Lorsque vous lancez ou attrapez des exceptions non mentées, nous vous recommandons d’utiliser l’option [compilateur /EHsc](../build/reference/eh-exception-handling-model.md) au lieu de **/EHs** ou **/EHa**.

## <a name="see-also"></a>Voir aussi

[Gestion des exceptions](../extensions/exception-handling-cpp-component-extensions.md)<br/>
[safe_cast](../extensions/safe-cast-cpp-component-extensions.md)<br/>
[Gestion des exceptions](../cpp/exception-handling-in-visual-cpp.md)
