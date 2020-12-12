---
description: 'En savoir plus sur : fichiers de sortie binaires'
title: Fichiers de sortie binaires
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: acbefe8eb7f091bf3d323f25ff00464068d9b1f3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325516"
---
# <a name="binary-output-files"></a>Fichiers de sortie binaires

Les flux ont été conçus à l’origine pour le texte, par conséquent, le mode de sortie par défaut est le mode texte. En mode texte, le caractère de saut de ligne se développe en une paire retour chariot-saut de ligne. L’extension peut entraîner des problèmes, comme le montre ce qui suit :

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

Vous pouvez vous attendre à ce que ce programme génère la séquence d’octets {99, 0, 10, 0} ; au lieu de cela, il génère {99, 0, 13, 10, 0}, ce qui entraîne des problèmes pour un programme qui attend une entrée binaire. Si vous avez besoin d’une vraie sortie binaire, dans laquelle les caractères sont écrits non traduits, vous pouvez spécifier une sortie binaire à l’aide de l’argument du constructeur [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) `openmode` :

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>Voir aussi

[Flux de sortie](../standard-library/output-streams.md)
