---
title: Construction d'objets de flux de sortie
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: d7bec211f30986deccc869a879dd5155ea70996b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457288"
---
# <a name="constructing-output-stream-objects"></a>Construction d'objets de flux de sortie

Si vous utilisez uniquement les objets prédéfinis `cout`, `cerr` ou `clog`, vous n’avez pas besoin de construire un flux de sortie. Vous devez utiliser des constructeurs pour les éléments suivants :

- [Constructeurs de flux de fichier de sortie](#vclrfoutputfilestreamconstructorsanchor1)

- [Constructeurs de flux de chaîne de sortie](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="vclrfoutputfilestreamconstructorsanchor1"></a> Constructeurs de flux de fichier de sortie

Vous pouvez construire un flux de fichier de sortie de deux façons :

- Utilisez le constructeur par défaut, puis appelez la fonction membre `open`.

   ```cpp
   ofstream myFile; // Static or on the stack
   myFile.open("filename");

   ofstream* pmyFile = new ofstream; // On the heap
   pmyFile->open("filename");
   ```

- Spécifiez un nom de fichier et des indicateurs de mode dans l’appel du constructeur.

   ```cpp
   ofstream myFile("filename", ios_base::out);
   ```

## <a name="vclrfoutputstringstreamconstructorsanchor2"></a> Constructeurs de flux de chaîne de sortie

Pour construire un flux de chaîne de sortie, vous pouvez utiliser `ostringstream` de la façon suivante :

```cpp
using namespace std;
// ...
ostringstream myString;
myString << "this is a test" << ends;

string sp = myString.str(); // Obtain string
cout << sp << endl;
```

Le « manipulateur » `ends` ajoute le caractère null de fin nécessaire à la chaîne.

## <a name="see-also"></a>Voir aussi

[Flux de sortie](../standard-library/output-streams.md)
