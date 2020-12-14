---
description: 'En savoir plus sur : spécification du chemin d’accès'
title: Spécification du nom de chemin
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: a8c55822bcb19864955ffa37ef2dd4cb18765ae5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224528"
---
# <a name="specifying-the-pathname"></a>Spécification du nom de chemin

Chaque option de fichier de sortie accepte un argument *pathname* qui peut spécifier un emplacement et un nom pour le fichier de sortie. L’argument peut inclure un nom de lecteur, un répertoire et un nom de fichier. Aucun espace n’est autorisé entre l’option et l’argument.

Si *pathname* inclut un nom de fichier sans extension, le compilateur donne à la sortie une extension par défaut. Si le *chemin d’accès* comprend un répertoire, mais pas de nom de fichier, le compilateur crée un fichier avec un nom par défaut dans le répertoire spécifié. Le nom par défaut est basé sur le nom de base du fichier source et une extension par défaut basée sur le type du fichier de sortie. Si vous ne spécifiez pas complètement *pathname* , le compilateur crée un fichier avec un nom par défaut dans un répertoire par défaut.

L’argument *pathname* peut également être un nom de périphérique (aux, con, PRN ou nul) au lieu d’un nom de fichier. N’utilisez pas d’espace entre l’option et le nom de l’appareil ou un signe deux-points dans le nom de l’appareil.

|Nom de l’appareil|Représente|
|-----------------|----------------|
|AUX|Appareil auxiliaire|
|CON|Console|
|PRN|Imprimante|
|NUL|Appareil null (aucun fichier créé)|

## <a name="example"></a>Exemple

La ligne de commande suivante envoie un mappage à l’imprimante :

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
