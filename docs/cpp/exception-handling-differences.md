---
title: Gérer les exceptions structurées en C++
description: Comment gérer des exceptions structurées à C++ l’aide du modèle de gestion des exceptions.
ms.date: 09/19/2019
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 0c0e458f576325034d77676d247020adedfa33e5
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158739"
---
# <a name="handle-structured-exceptions-in-c"></a>Gérer les exceptions structurées en C++

La principale différence entre la gestion structurée des exceptions (SEH C++ ) et la gestion des C++ exceptions est que le modèle de gestion des exceptions traite les types, tandis que le modèle de gestion structurée des exceptions c traite les exceptions d’un type. plus précisément, **unsigned int**. Autrement dit, les exceptions C sont identifiées par une valeur entière non signée, tandis que les exceptions C++ sont identifiées par le type de données. Lorsqu’une exception structurée est levée en C, chaque gestionnaire possible exécute un filtre qui examine le contexte de l’exception C et détermine s’il faut accepter l’exception, la passer à un autre gestionnaire ou l’ignorer. Lorsqu'une exception est levée en C++, elle peut être de n'importe quelle type.

La deuxième différence est que le modèle de gestion structurée des exceptions C est connu sous le terme de asynchrone, car les exceptions se produisent de *manière*secondaire dans le déroulement normal du contrôle. Le C++ mécanisme de gestion des exceptions est entièrement *synchrone*, ce qui signifie que les exceptions se produisent uniquement lorsqu’elles sont levées.

Quand vous utilisez l’option de compilateur [/EHS ou/EHsc](../build/reference/eh-exception-handling-model.md) , C++ aucun gestionnaire d’exceptions ne gère les exceptions structurées. Ces exceptions sont gérées uniquement par les gestionnaires d’exceptions structurés par des **_ _** ou les gestionnaires de terminaison structurés par _ _ **finally** . Pour plus d’informations, consultez [gestion structurée desC++exceptions (C/)](structured-exception-handling-c-cpp.md).

Avec l’option de compilateur [/EHa](../build/reference/eh-exception-handling-model.md) , si une exception C est levée dans C++ un programme, elle peut être gérée par un gestionnaire d’exceptions structurées avec son filtre C++ associé ou par un gestionnaire **catch** , selon la valeur la plus proche de l’exception. contexte. Par exemple, cet exemple C++ de programme génère une exception C dans C++ un contexte **try** :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Exemple : intercepter une exception C dans C++ un bloc catch

```cpp
// exceptions_Exception_Handling_Differences.cpp
// compile with: /EHa
#include <iostream>

using namespace std;
void SEHFunc( void );

int main() {
   try {
      SEHFunc();
   }
   catch( ... ) {
      cout << "Caught a C exception."<< endl;
   }
}

void SEHFunc() {
   __try {
      int x, y = 0;
      x = 5 / y;
   }
   __finally {
      cout << "In finally." << endl;
   }
}
```

```Output
In finally.
Caught a C exception.
```

## <a name="c-exception-wrapper-classes"></a>Classes wrapper d’exception C

Dans un exemple simple comme celui ci-dessus, l’exception C peut être interceptée uniquement par des points de suspension ( **...** ) gestionnaire **catch** . Aucune information sur le type ou la nature de l'exception n'est communiquée au gestionnaire. Cette méthode fonctionne, dans certains cas, vous pouvez définir une transformation entre les deux modèles de gestion des exceptions afin que chaque exception C soit associée à une classe spécifique. Pour en transformer un, vous pouvez définir une classe « wrapper » d’exception C, qui peut être utilisée ou dérivée de pour attribuer un type de classe spécifique à une exception C. En procédant ainsi, chaque exception C peut être gérée séparément par C++ un gestionnaire **catch** spécifique, au lieu de toutes les deux dans un seul gestionnaire.

Votre classe wrapper peut avoir une interface constituée de certaines fonctions membres qui déterminent la valeur de l'exception et qui accèdent aux informations de contexte d'exception étendues fournies par le modèle d'exception C. Vous pouvez également définir un constructeur par défaut et un constructeur qui accepte un argument **int non signé** (pour fournir la représentation d’exception C sous-jacente) et un constructeur de copie au niveau du bit. Voici une implémentation possible d’une classe wrapper d’exception C :

```cpp
// exceptions_Exception_Handling_Differences2.cpp
// compile with: /c
class SE_Exception {
private:
   SE_Exception() {}
   SE_Exception( SE_Exception& ) {}
   unsigned int nSE;
public:
   SE_Exception( unsigned int n ) : nSE( n ) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() {
      return nSE;
   }
};
```

Pour utiliser cette classe, installez une fonction de traduction d’exception C personnalisée appelée par le mécanisme de gestion des exceptions interne chaque fois qu’une exception C est levée. Dans votre fonction de traduction, vous pouvez lever n’importe quelle exception typée (peut- `SE_Exception` être un type ou un type de classe dérivé de `SE_Exception`) qui peut C++ être interceptée par un gestionnaire **catch** correspondant approprié. La fonction de traduction peut retourner à la place, ce qui indique qu’elle n’a pas géré l’exception. Si la fonction de traduction elle-même lève une exception C, [Terminate](../c-runtime-library/reference/terminate-crt.md) est appelé.

Pour spécifier une fonction de traduction personnalisée, appelez la fonction _ [set_se_translator](../c-runtime-library/reference/set-se-translator.md) avec le nom de votre fonction de traduction comme argument unique. La fonction de traduction que vous écrivez est appelée une fois pour chaque appel de fonction sur la pile qui a des blocs **try** . Il n’existe aucune fonction de traduction par défaut ; Si vous n’en spécifiez pas un en appelant _ **set_se_translator**, l’exception C peut uniquement être interceptée par un gestionnaire **catch** de sélection.

## <a name="example---use-a-custom-translation-function"></a>Exemple : utilisation d’une fonction de traduction personnalisée

Par exemple, le code suivant installe une fonction de traduction personnalisée, puis lève une exception C qui est encapsulée par la classe `SE_Exception` :

```cpp
// exceptions_Exception_Handling_Differences3.cpp
// compile with: /EHa
#include <stdio.h>
#include <eh.h>
#include <windows.h>

class SE_Exception {
private:
   SE_Exception() {}
   unsigned int nSE;
public:
   SE_Exception( SE_Exception& e) : nSE(e.nSE) {}
   SE_Exception(unsigned int n) : nSE(n) {}
   ~SE_Exception() {}
   unsigned int getSeNumber() { return nSE; }
};

void SEFunc() {
    __try {
        int x, y = 0;
        x = 5 / y;
    }
    __finally {
        printf_s( "In finally\n" );
    }
}

void trans_func( unsigned int u, _EXCEPTION_POINTERS* pExp ) {
    printf_s( "In trans_func.\n" );
    throw SE_Exception( u );
}

int main() {
    _set_se_translator( trans_func );
    try {
        SEFunc();
    }
    catch( SE_Exception e ) {
        printf_s( "Caught a __try exception with SE_Exception.\n" );
        printf_s( "nSE = 0x%x\n", e.getSeNumber() );
    }
}
```

```Output
In trans_func.
In finally
Caught a __try exception with SE_Exception.
nSE = 0xc0000094
```

## <a name="see-also"></a>Voir aussi

[Mélange de C (structuré) C++ et des exceptions](../cpp/mixing-c-structured-and-cpp-exceptions.md)
