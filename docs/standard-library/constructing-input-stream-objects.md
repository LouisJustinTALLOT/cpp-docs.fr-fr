---
title: Construction d'objets de flux d'entrée
ms.date: 11/04/2016
helpviewer_keywords:
- input stream objects
ms.assetid: ab94866e-6ffe-4f15-b4db-0bd23e636075
ms.openlocfilehash: c000a9e927169ef710554372217ba15089ee11b8
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457296"
---
# <a name="constructing-input-stream-objects"></a>Construction d'objets de flux d'entrée

Si vous utilisez uniquement l’objet `cin`, vous n’avez pas besoin de construire un flux d’entrée. Vous devez construire un flux d’entrée si vous utilisez les éléments suivants :

- [Constructeurs de flux de fichier d’entrée](#vclrfinputfilestreamconstructorsanchor8)

- [Constructeurs de flux de chaîne d’entrée](#vclrfinputstringstreamconstructorsanchor9)

## <a name="vclrfinputfilestreamconstructorsanchor8"></a> Constructeurs de flux de fichier d’entrée

Il existe deux façons de créer un flux de fichier d’entrée :

- Utilisez le constructeur d’argument **void** , puis appelez `open` la fonction membre:

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

## <a name="vclrfinputstringstreamconstructorsanchor9"></a> Constructeurs de flux de chaîne d’entrée

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
