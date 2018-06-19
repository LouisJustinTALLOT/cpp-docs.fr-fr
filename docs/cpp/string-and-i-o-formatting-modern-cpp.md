---
title: Chaîne et la mise en forme d’e-S (Modern C++) | Documents Microsoft
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
ms.openlocfilehash: 391648d71fa3d38a0f704a014c163b7f8b102e40
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32422382"
---
# <a name="string-and-io-formatting-modern-c"></a>Mise en forme des chaînes et E/S (Modern C++)
C++ [iostreams](../standard-library/iostream.md) compatibles avec la chaîne mise en forme d’e/s. Par exemple, le code suivant montre comment définir cout pour mettre en forme un entier et de sortie au format hexadécimal, tout d’abord l’enregistrement de l’état actuel et nouveau paramètre par la suite, car une fois la mise en forme de l’état est passé à cout, il reste de cette façon jusqu'à ce que modifié, pas seulement pour la ligne d’un du code.  
  
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
  
 Cela peut être entièrement trop lourdes dans de nombreux cas. En guise d’alternative, vous pouvez utiliser Boost.Format dans les bibliothèques de renforcement C++, même s’il est non standard. Vous pouvez télécharger n’importe quelle bibliothèque de renforcement de la [renforcement](http://www.boost.org/) site Web.  
  
 Les avantages de Boost.Format sont :  
  
-   Safe : Type-safe et lève une exception pour les erreurs, par exemple, la spécification d’éléments trop ou trop peu.  
  
-   Extensible : Works pour tout type qui peut être transmis en continu.  
  
-   Pratique : Posix Standard et les chaînes de format similaire.  
  
 Bien que Boost.Format repose sur le langage C++ [iostreams](../standard-library/iostream-programming.md), qui sont fiables et extensibles, ils ne sont pas optimisées sur les performances. Lorsque vous avez besoin d’optimisation des performances, envisagez de C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) et [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), qui sont rapides et faciles à utiliser. Toutefois, ils ne sont pas extensibles ou protégée contre les vulnérabilités. (Les versions sécurisées existent, mais elles entraînent une légère baisse des performances. Pour plus d’informations, consultez [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) et [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).  
  
 Le code suivant illustre certaines de renforcement de la mise en forme des fonctionnalités.  
  
```cpp  
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );  
    // s contains "hello hello world"    
  
    for( auto i = 0; i < names.size(); ++i )  
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];  
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789  
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321  
  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Bienvenue dans C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Référence du langage C++](../cpp/cpp-language-reference.md)   
 [Bibliothèque standard C++](../standard-library/cpp-standard-library-reference.md)   
 [\<iostream >](../standard-library/iostream.md)   
 [\<limites >](../standard-library/limits.md)   
 [\<iomanip>](../standard-library/iomanip.md)
