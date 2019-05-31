---
title: Mise en forme des chaînes et E/S (Modern C++)
description: Choix de la chaîne mise en forme d’e/s disponible moderne C++.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: e22c745798109a2dbef82297c45256593823f806
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450504"
---
# <a name="string-and-io-formatting-modern-c"></a>Mise en forme des chaînes et E/S (Modern C++)

C++[ \<iostream >](../standard-library/iostream.md) classes, les fonctions et opérateurs prennent en charge la chaîne mise en forme d’e/s. Par exemple, le code suivant montre comment définir `cout` à mettre en forme un entier à sortir au format hexadécimal. Tout d’abord, elle enregistre l’état actuel pour le réinitialiser par la suite, car une fois l’état du format est passé à `cout`, il reste ainsi jusqu'à modification. Elle ne s’applique uniquement à la ligne de code.

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

Cette approche est de type sécurisé et extensible, mais il est également complexe et détaillé.

## <a name="alternative-format-options"></a>Options de format autre

Comme alternative, vous pouvez utiliser `Boost.Format` à partir de la valorisation C++ bibliothèques, même si elle n’est pas standard. Vous pouvez télécharger une bibliothèque Boost depuis le [Boost](https://www.boost.org/) site Web.

Voici certains avantages de `Boost.Format` sont :

- Sécurisé : Type-safe et lève une exception pour les erreurs, par exemple, la spécification d’éléments trop ou trop peu.

- Extensible : Fonctionne pour n’importe quel type puisse être diffusé en continu.

- Pratique : Posix standard et chaînes de format similaires.

Bien que `Boost.Format` repose sur C++ [ \<iostream >](../standard-library/iostream-programming.md) installations, ce qui sont sécurisé et extensible, ils ne sont pas optimisé pour les performances. Lorsque vous avez besoin d’optimisation des performances, tenez compte des C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), qui sont rapides et faciles à utiliser. Toutefois, ils ne sont pas extensibles ou protégés contre les vulnérabilités. (Les versions sécurisées existent, mais elles entraînent une baisse des performances légères. Pour plus d’informations, consultez [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) et [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

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

[Bienvenue dans C++ (C++ moderne)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
