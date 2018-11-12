---
title: Gérer les exceptions structurées en C++
ms.date: 08/14/2018
helpviewer_keywords:
- structured exception handling [C++], vs. C++ exception handling
- structured exception handling [C++], vs. unstructured
- exceptions [C++], wrapper class
- C++ exception handling [C++], vs. structured exception handling
- wrapper classes [C++], C exception
ms.assetid: f21d1944-4810-468e-b02a-9f77da4138c9
ms.openlocfilehash: 2c4f1a8c3729e2b4d49a0152425e57717f7e9997
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482847"
---
# <a name="handle-structured-exceptions-in-c"></a>Gérer les exceptions structurées en C++

La principale différence entre C gestion structurée des exceptions (SEH) et la gestion des exceptions C++ est que la C++ exceptions modèle traite des types, lors de la C modèle de gestion structurée des exceptions traite des exceptions d’un type ; plus précisément, **unsigned int**. Autrement dit, les exceptions C sont identifiées par une valeur entière non signée, tandis que les exceptions C++ sont identifiées par le type de données. Lorsqu’une exception structurée est déclenchée dans C, chaque gestionnaire possible exécute un filtre qui examine le contexte d’exception C et détermine s’il faut accepter l’exception, passer à un autre gestionnaire ou l’ignorer. Lorsqu'une exception est levée en C++, elle peut être de n'importe quelle type.

La deuxième différence est que le modèle de gestion des exceptions structurées C est appelé *asynchrone*, car les exceptions se produisent secondaire pour le flux de contrôle normal. La mécanisme d’exceptions C++ sont entièrement *synchrone*, ce qui signifie que les exceptions produisent uniquement lorsqu’elles sont levées.

Lorsque vous utilisez le [/EHs ou /EHsc](../build/reference/eh-exception-handling-model.md) option du compilateur, aucun handle structurée des exceptions gestionnaires exception C++. Ces exceptions sont traitées uniquement par **__catch** structurées de gestionnaires d’exceptions ou **__finally** structuré des gestionnaires de terminaisons. Pour plus d’informations, consultez [structurée des exceptions (C/C++)](structured-exception-handling-c-cpp.md).

Sous le [/EHa](../build/reference/eh-exception-handling-model.md) option du compilateur, si une exception C est levée dans un programme C++, elle peut être gérée par un gestionnaire d’exceptions structuré avec son filtre associé ou par un C++ **catch** gestionnaire, plus petite étant retenue dynamiquement proche le contexte d’exception. Par exemple, le programme C++ suivant lève une exception de C à l’intérieur d’un C++ **essayez** contexte :

## <a name="example---catch-a-c-exception-in-a-c-catch-block"></a>Exemple - bloc intercepter l’exception Catch un C dans C++

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

## <a name="c-exception-wrapper-classes"></a>Classes de wrapper d’exception C

Dans un exemple simple à l’exemple ci-dessus, l’exception C peut être interceptée uniquement par les points de suspension (**...** ) **catch** gestionnaire. Aucune information sur le type ou la nature de l'exception n'est communiquée au gestionnaire. Bien que cette méthode fonctionne, dans certains cas vous souhaiterez peut-être définir une transformation entre les modèles de deux exceptions afin que chaque exception C soit associée à une classe spécifique. Pour cela, vous pouvez définir une classe « wrapper » d'exception C, qui peut être utilisée ou dont il est possible de dériver pour attribuer un type de classe spécifique à l'exception C. En procédant ainsi, chaque exception C peut être gérée séparément par un C++ spécifiques **catch** gestionnaire, et non la totalité d'entre elles dans un gestionnaire unique.

Votre classe wrapper peut avoir une interface constituée de certaines fonctions membres qui déterminent la valeur de l'exception et qui accèdent aux informations de contexte d'exception étendues fournies par le modèle d'exception C. Vous souhaiterez également définir un constructeur par défaut et un constructeur qui accepte un **unsigned int** argument (pour fournir pour la représentation d’exception C sous-jacente) et un constructeur de copie au niveau du bit. Voici une implémentation possible d’une classe de wrapper d’exception C :

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

Pour utiliser cette classe, installez une fonction de traduction d’exception C personnalisée qui est appelée par la mécanisme chaque fois qu’une exception C est levée d’exceptions internes. Dans votre fonction de traduction, vous pouvez lever n’importe quelle exception typée (peut-être un `SE_Exception` type ou un type de classe dérivé `SE_Exception`) qui peut être interceptée par un C++ approprié **catch** gestionnaire. La fonction de traduction peut simplement retourner, ce qui signifie qu'elle n'a pas géré l'exception. Si la fonction de traduction proprement dite lève une exception C, [Terminer](../c-runtime-library/reference/terminate-crt.md) est appelée.

Pour spécifier une fonction de traduction personnalisée, appelez le [_set_se_translator](../c-runtime-library/reference/set-se-translator.md) fonction portant le nom de votre fonction de traduction comme unique argument. La fonction de traduction que vous écrivez est appelée une fois pour chaque appel de fonction sur la pile a **essayez** blocs. Il n’existe aucune fonction de traduction par défaut ; Si vous ne spécifiez pas une en appelant **_set_se_translator**, l’exception C peut uniquement être interceptée par un bouton de sélection **catch** gestionnaire.

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

[Mélange d’exceptions C (structurées) et des exceptions C++](../cpp/mixing-c-structured-and-cpp-exceptions.md)
