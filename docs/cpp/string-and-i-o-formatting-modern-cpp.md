---
title: Chaîne et la mise en forme des e / S (Modern C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8d73e42beb086f3db3e6a6fd060048fcb700156c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099822"
---
# <a name="string-and-io-formatting-modern-c"></a>Mise en forme des chaînes et E/S (Modern C++)

C++ [iostreams](../standard-library/iostream.md) compatibles avec la chaîne mise en forme d’e/s. Par exemple, le code suivant montre comment définir cout pour mettre en forme un entier à sortir au format hexadécimal, tout d’abord l’enregistrement de l’état actuel et nouveau paramètre par la suite, car une fois la mise en forme de l’état est passée à cout, il reste ainsi jusqu'à modification, pas seulement pour la ligne par ligne du code.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main() 
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex 
        << uppercase 
        << setw(8) 
        << setfill('0') 
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

Cela peut être réellement trop fastidieux dans de nombreux cas. Comme alternative, vous pouvez utiliser Boost.Format des bibliothèques Boost C++, même si elle n’est pas standard. Vous pouvez télécharger une bibliothèque Boost depuis le [Boost](http://www.boost.org/) site Web.

Voici certains avantages de Boost.Format sont :

- Sécurisé : Type-safe et lève une exception pour les erreurs, par exemple, la spécification d’éléments trop ou trop peu.

- Extensible : Fonctionne pour n’importe quel type puisse être diffusé en continu.

- Pratique : Norme Posix standard et chaînes de format similaires.

Bien que Boost.Format soit généré en C++ [iostreams](../standard-library/iostream-programming.md), qui est sécurisé et extensible, ils ne sont pas optimisé pour les performances. Lorsque vous avez besoin d’optimisation des performances, tenez compte des C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), qui sont rapides et faciles à utiliser. Toutefois, ils ne sont pas extensibles ou protégés contre les vulnérabilités. (Les versions sécurisées existent, mais elles entraînent une baisse des performances légères. Pour plus d’informations, consultez [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) et [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Le code suivant illustre certaines de la valorisation de fonctionnalités de mise en forme.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"  

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Voir aussi

[Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)