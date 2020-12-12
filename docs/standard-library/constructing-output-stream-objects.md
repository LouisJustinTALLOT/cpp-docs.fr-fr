---
description: 'En savoir plus sur : construction d’objets de flux de sortie'
title: Construction d'objets de flux de sortie
ms.date: 11/04/2016
helpviewer_keywords:
- output stream objects
ms.assetid: 93c8eab6-610c-4f48-b76d-1d960cac7641
ms.openlocfilehash: e730e4cb675b216fa56b5624feb69fadcd61400a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97233641"
---
# <a name="constructing-output-stream-objects"></a>Construction d'objets de flux de sortie

Si vous utilisez uniquement les objets prédéfinis `cout`, `cerr` ou `clog`, vous n’avez pas besoin de construire un flux de sortie. Vous devez utiliser des constructeurs pour les éléments suivants :

- [Constructeurs de flux de fichier de sortie](#vclrfoutputfilestreamconstructorsanchor1)

- [Constructeurs de flux de chaîne de sortie](#vclrfoutputstringstreamconstructorsanchor2)

## <a name="output-file-stream-constructors"></a><a name="vclrfoutputfilestreamconstructorsanchor1"></a> Constructeurs de flux de fichier de sortie

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

## <a name="output-string-stream-constructors"></a><a name="vclrfoutputstringstreamconstructorsanchor2"></a> Constructeurs de flux de chaîne de sortie

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
