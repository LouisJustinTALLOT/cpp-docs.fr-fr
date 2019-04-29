---
title: Manipulateurs de flux de sortie à un argument (int ou long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: e093512af2741329c58db0b613453f3388bacdf2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370799"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulateurs de flux de sortie à un argument (int ou long)

La bibliothèque de classes iostream fournit un ensemble de macros permettant de créer des manipulateurs paramétrables. Manipulateurs avec un seul **int** ou **long** argument constituent un cas particulier. Pour créer un manipulateur de flux de sortie qui accepte un seul **int** ou **long** argument (comme `setw`), vous devez utiliser la macro _Smanip, qui est définie dans \<iomanip >. Cet exemple définit un manipulateur `fillblank` qui insère un nombre spécifié d’espaces vides dans le flux :

## <a name="example"></a>Exemple

```cpp
// output_stream_manip.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
using namespace std;

void fb( ios_base& os, int l )
{
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
}

_Smanip<int>
   __cdecl fillblank(int no)
   {
   return (_Smanip<int>(&fb, no));
   }

int main( )
{
   cout << "10 blanks follow" << fillblank( 10 ) << ".\n";
}
```

## <a name="see-also"></a>Voir aussi

[Manipulateurs personnalisés avec arguments](../standard-library/custom-manipulators-with-arguments.md)<br/>
