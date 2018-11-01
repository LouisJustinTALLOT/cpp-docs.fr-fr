---
title: Spécification du nom de chemin
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: f83adcb87994d13edd1c1579183377a365e2051e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638358"
---
# <a name="specifying-the-pathname"></a>Spécification du nom de chemin

Chaque option de fichier de sortie accepte un *pathname* argument peut spécifier un emplacement et un nom pour le fichier de sortie. L’argument peut inclure un nom de lecteur, le répertoire et le nom de fichier. Aucun espace n’est autorisé entre l’option et l’argument.

Si *pathname* inclut un nom de fichier sans extension, le compilateur donne le résultat une extension par défaut. Si *pathname* inclut un répertoire, mais aucun nom de fichier, le compilateur crée un fichier avec un nom par défaut dans le répertoire spécifié. Le nom par défaut est basé sur le nom de base du fichier source et une extension par défaut en fonction du type du fichier de sortie. Si vous omettez *pathname* entièrement, le compilateur crée un fichier avec un nom par défaut dans un répertoire par défaut.

Vous pouvez également le *pathname* argument peut être un nom de périphérique (AUX, CON, PRN ou NUL) au lieu d’un nom de fichier. N’utilisez pas d’espace entre l’option et le nom du périphérique ou un signe deux-points comme partie du nom du périphérique.

|Nom de l’appareil|Représente|
|-----------------|----------------|
|AUX|APPAREIL auxiliaire|
|CON|Console|
|PRN|Imprimante|
|NUL|Périphérique NULL (aucun fichier créé)|

## <a name="example"></a>Exemple

La ligne de commande suivante envoie un fichier de mappage à l’imprimante :

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](../../build/reference/output-file-f-options.md)<br/>
[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)