---
title: Construction d'objets de flux d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: f281741979680fc03d3f96d2dbfbac6e1feefdea
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228308"
---
# <a name="constructing-input-stream-objects"></a>Construction d'objets de flux d'entrée

Si vous utilisez uniquement l’objet `cin`, vous n’avez pas besoin de construire un flux d’entrée. Vous devez construire un flux d’entrée si vous utilisez les éléments suivants :

- [Constructeurs de flux de fichier d’entrée](#vclrfinputfilestreamconstructorsanchor8)

- [Constructeurs de flux de chaîne d’entrée](#vclrfinputstringstreamconstructorsanchor9)

## <a name="input-file-stream-constructors"></a><a name="vclrfinputfilestreamconstructorsanchor8"></a> Constructeurs de flux de fichier d’entrée

Il existe deux façons de créer un flux de fichier d’entrée :

- Utilisez le **`void`** constructeur d’argument, puis appelez la `open` fonction membre :

   ```cpp
   ifstream myFile; // On the stack
   myFile.open("filename");

   ifstream* pmyFile = new ifstream; // On the heap
   pmyFile->open("filename");
   ```

- Spécifiez un nom de fichier et des indicateurs de mode dans l’appel du constructeur, pour l’ouverture du fichier pendant le processus de construction :

   ```cpp
   ifstream myFile("filename");
   ```

## <a name="input-string-stream-constructors"></a><a name="vclrfinputstringstreamconstructorsanchor9"></a> Constructeurs de flux de chaîne d’entrée

Les constructeurs de flux de chaîne d’entrée nécessitent l’adresse du stockage préalloué et préinitialisé :

```cpp
string s("123.45");

double amt;
istringstream myString(s);

//istringstream myString("123.45") also works
myString>> amt; // amt contains 123.45
```

## <a name="see-also"></a>Voir aussi

[Flux d’entrée](../standard-library/input-streams.md)
