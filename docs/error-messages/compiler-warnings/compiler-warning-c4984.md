---
description: 'En savoir plus sur : avertissement du compilateur C4984'
title: Avertissement du compilateur C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 5a6708a1063baf8fa4b5feece65eabd93df7bbeb
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325998"
---
# <a name="compiler-warning-c4984"></a>Avertissement du compilateur C4984

> 'If constexpr’est une extension de langage C++ 17

## <a name="remarks"></a>Notes

Le compilateur a trouvé une `if constexpr` expression dans le code compilé à l’aide de la norme c++ 14 par défaut. Cette expression est spécifiée à partir de la norme C++ 17. Si vous avez besoin de la compatibilité C++ 11 ou C++ 14, cette expression n’est pas portable.

C4984 est émis en tant qu’erreur par défaut, mais il s’agit de suppressible. Pour activer cette expression en compilant votre code en C++ 17, utilisez [/std : c++ 17 ou/std : C + + latest](../../build/reference/std-specify-language-standard-version.md). Pour utiliser l' `if constexpr` expression dans le code compilé pour c++ 14 en tant qu’extension Microsoft, vous pouvez supprimer, désactiver ou modifier le niveau d’avertissement du message d’erreur. Vous pouvez utiliser [/wd4984](../../build/reference/compiler-option-warning-level.md) pour désactiver C4984 ou __/w__*n*__4984__ pour l’activer en tant qu’avertissement de niveau *n* au lieu d’une erreur. Sinon, utilisez [#pragma avertissement (supprimer : 4984)](../../preprocessor/warning.md) avant la ligne qui provoque l’avertissement dans votre fichier source.

Cet avertissement est disponible à partir de Visual Studio 2017 version 15,3. Pour plus d’informations sur la façon de désactiver les avertissements introduits dans une version particulière du compilateur ou une version ultérieure, consultez [avertissements du compilateur par version du compilateur](compiler-warnings-by-compiler-version.md).

## <a name="example"></a>Exemple

Cet exemple génère C4984 et montre comment le résoudre :

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
