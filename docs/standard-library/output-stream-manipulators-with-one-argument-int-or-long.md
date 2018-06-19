---
title: Manipulateurs de flux de sortie à un argument (int ou long) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, int or long argument manipulators
ms.assetid: 338f3164-b5e2-4c5a-a605-7d9dc3629ca1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f3238ffcbd03f40c6eac0423d0212a65719fb33d
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853071"
---
# <a name="output-stream-manipulators-with-one-argument-int-or-long"></a>Manipulateurs de flux de sortie à un argument (int ou long)

La bibliothèque de classes iostream fournit un ensemble de macros permettant de créer des manipulateurs paramétrables. Les manipulateurs à un argument `int` ou `long` sont un cas particulier. Pour créer un manipulateur de flux de sortie qui accepte un seul argument `int` ou `long` (comme `setw`), utilisez la macro _Smanip, qui est définie dans \<iomanip>. Cet exemple définit un manipulateur `fillblank` qui insère un nombre spécifié d’espaces vides dans le flux :

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
