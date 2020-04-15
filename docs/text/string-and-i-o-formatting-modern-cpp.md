---
title: Mise en forme des chaînes et E/S (Modern C++)
description: Choix pour la chaîne formatée I/O disponible en C moderne.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375771"
---
# <a name="string-and-io-formatting-modern-c"></a>Mise en forme des chaînes et E/S (Modern C++)

Les classes, les fonctions et les opérateurs de Cmd [ \<iostream>](../standard-library/iostream.md) supportent la chaîne formatée I/O. Par exemple, le code suivant `cout` montre comment définir pour formater un intégriste à la sortie en hexadecimal. Tout d’abord, il sauve l’état actuel de le `cout`réinitialiser par la suite, parce qu’une fois l’état de format est passé à , il reste de cette façon jusqu’à ce que changé. Il ne s’applique pas seulement à la seule ligne de code.

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

Cette approche est sans danger de type et extensible, mais elle est aussi complexe et verbeuse.

## <a name="alternative-format-options"></a>Options de format alternatif

Comme alternative, vous `Boost.Format` pouvez utiliser à partir des bibliothèques Boost C, même si elle n’est pas standard. Vous pouvez télécharger n’importe quelle bibliothèque Boost à partir du site Web [Boost.](https://www.boost.org/)

Voici quelques `Boost.Format` avantages :

- Coffre-fort : Type-sûr, et jette une exception pour les erreurs, par exemple, la spécification de trop peu ou trop d’éléments.

- Extensible: Fonctionne pour n’importe quel type qui peut être écouté.

- Pratique : POSIX standard et chaînes de format similaires.

Bien `Boost.Format` qu’elle soit construite sur des installations [ \<>de c.d’iostream,](../standard-library/iostream-programming.md) qui sont sûres et extensibles, elles ne sont pas optimisées pour les performances. Lorsque vous avez besoin d’optimisation des performances, considérez C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), qui sont rapides et faciles à utiliser. Cependant, ils ne sont pas extensibles ou à l’abri des vulnérabilités. (Des versions sûres existent, mais elles encourent une légère pénalité de performance. Pour plus d’informations, voir [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) et [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

Le code suivant démontre certaines des fonctionnalités de formatage Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Voir aussi

[Bienvenue à C](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Référence linguistique de CMD](../cpp/cpp-language-reference.md)<br/>
[Bibliothèque standard de CMD](../standard-library/cpp-standard-library-reference.md)<br/>
[\<>iostream](../standard-library/iostream.md)<br/>
[\<limites>](../standard-library/limits.md)<br/>
[\<>iomanip](../standard-library/iomanip.md)
