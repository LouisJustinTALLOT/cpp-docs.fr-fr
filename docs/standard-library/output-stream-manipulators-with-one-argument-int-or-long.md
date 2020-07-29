---
title: Manipulateurs de flux de sortie à un argument (int ou long)
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
ms.openlocfilehash: 203797eef95e3dab0c079e35baefcea99c3b966d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217660"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulateurs de flux de sortie à un argument (int ou long)

La bibliothèque de classes iostream fournit un ensemble de macros permettant de créer des manipulateurs paramétrables. Les manipulateurs avec un **`int`** seul **`long`** argument ou sont un cas spécial. Pour créer un manipulateur de flux de sortie qui accepte **`int`** un **`long`** argument unique ou (comme `setw` ), vous devez utiliser la macro _Smanip, qui est définie dans \<iomanip> . Cet exemple définit un manipulateur `fillblank` qui insère un nombre spécifié d’espaces vides dans le flux :

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

[Manipulateurs personnalisés avec arguments](../standard-library/custom-manipulators-with-arguments.md)
