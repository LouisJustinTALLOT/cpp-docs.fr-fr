---
title: Mise en forme des chaînes et E/S (Modern C++)
description: Choix pour les e/s de chaîne mises en C++forme disponibles dans moderne.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: 7ea858a8a8126d3754783edee0dd3ea5409e5f73
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898832"
---
# <a name="string-and-io-formatting-modern-c"></a>Mise en forme des chaînes et E/S (Modern C++)

C++\<les classes, les fonctions et les opérateurs [> iostream](../standard-library/iostream.md) prennent en charge les e/s de chaîne mises en forme. Par exemple, le code suivant montre comment définir `cout` pour mettre en forme un entier en sortie au format hexadécimal. Tout d’abord, elle enregistre l’état actuel pour la réinitialiser par la suite, car une fois que l’état de mise en forme est passé à `cout`, elle reste jusqu’à ce que la modification soit possible. Elle ne s’applique pas simplement à une seule ligne de code.

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

Cette approche est de type sécurisé et extensible, mais elle est également complexe et détaillée.

## <a name="alternative-format-options"></a>Options de format alternatives

Vous pouvez également utiliser `Boost.Format` à partir des bibliothèques Boost C++ , même s’il n’est pas standard. Vous pouvez télécharger n’importe quelle Bibliothèque Boost à partir du site Web [Boost](https://www.boost.org/) .

Voici quelques avantages de `Boost.Format` :

- Safe : de type sécurisé et lève une exception pour les erreurs, par exemple, la spécification d’un trop petit nombre ou d’un trop grand nombre d’éléments.

- Extensible : fonctionne pour tout type qui peut être transmis en continu.

- Pratique : POSIX standard et chaînes de format similaires.

Bien que `Boost.Format` repose sur C++ [\<des fonctionnalités iostream >](../standard-library/iostream-programming.md) , qui sont sûres et extensibles, elles ne sont pas optimisées pour les performances. Lorsque vous avez besoin d’une optimisation des performances, pensez à C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), qui sont rapides et faciles à utiliser. Toutefois, ils ne sont pas extensibles ni sûrs contre les vulnérabilités. Les versions sécurisées existent, mais elles réduisent légèrement les performances. Pour plus d’informations, consultez [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) et [sprintf_s, _sprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md), swprintf_s, _swprintf_s_l).

Le code suivant illustre quelques-unes des fonctionnalités de mise en forme de Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Voir aussi

[Bienvenue dansC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Informations de référence sur le langage C++](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque C++ standard](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
