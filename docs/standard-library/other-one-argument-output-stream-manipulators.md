---
title: Autres manipulateurs de flux de sortie à un argument | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- output streams, one-argument manipulators
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2cd9c9f643b6766dfca4f008f14c9d470a5bcc34
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853321"
---
# <a name="other-one-argument-output-stream-manipulators"></a>Autres manipulateurs de flux de sortie à un argument

L’exemple suivant utilise une classe `money`, qui est un type `long`. Le manipulateur `setpic` attache une chaîne « image » mise en forme à la classe qui peut être utilisée par l’opérateur d’insertion de flux surchargé de la classe `money`. La chaîne image est stockée comme variable statique dans la classe `money` au lieu d’être stockée comme membre d’une classe stream. Vous n’avez donc pas à dériver une nouvelle classe output stream.

## <a name="example"></a>Exemple

```cpp
// one_arg_output.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

typedef char* charp;

class money
{
private:
    long value;
    static char *szCurrentPic;
public:
    money( long val ) { value = val; }
    friend ostream& operator << ( ostream& os, money m ) {
        // A more complete function would merge the picture
        // with the value rather than simply appending it
        os << m.value << '[' << money::szCurrentPic << ']';
        return os;
    }
    static void setpic( char* szPic ) {
        money::szCurrentPic = new char[strlen( szPic ) + 1];
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );
    }
};

char *money::szCurrentPic;  // Static pointer to picture

void fb( ios_base& os, char * somename )
{
   money::setpic(somename);
/*
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
*/
}

_Smanip<charp>
   __cdecl setpic(char * somename)
   {
   return (_Smanip<charp>(&fb, somename));
   }

int main( )
{
    money amt = (long)35235.22;
    cout << setiosflags( ios::fixed );
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;
}
```

## <a name="see-also"></a>Voir aussi

[Manipulateurs personnalisés avec arguments](../standard-library/custom-manipulators-with-arguments.md)<br/>
