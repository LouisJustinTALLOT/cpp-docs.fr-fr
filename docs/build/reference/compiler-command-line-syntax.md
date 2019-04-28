---
title: Syntaxe de ligne de commande du compilateur MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 5cee76d5c053dbcfef33a191dc38a958338e4a82
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62294341"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe de la ligne de commande du compilateur

La ligne de commande CL utilise la syntaxe suivante :

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Le tableau suivant décrit les entrées de la commande CL.

|Entrée|Signification|
|-----------|-------------|
|*option*|Un ou plusieurs [options CL](compiler-options.md). Notez que toutes les options s’appliquent à tous les fichiers source spécifié. Options sont spécifiées par une barre oblique (/) ou un tiret (-). Si une option accepte un argument, les documents de description de cette option si un espace est autorisé entre l’option et les arguments. Les noms des options (à l’exception de l’option /HELP) respectent la casse. Consultez [ordre des Options CL](order-of-cl-options.md) pour plus d’informations.|
|`file`|Le nom d’un ou plusieurs fichiers sources, les fichiers .obj ou des bibliothèques. CL compile des fichiers source et passe les noms des fichiers .obj et des bibliothèques à l’éditeur de liens. Consultez [syntaxe de nom de fichier CL](cl-filename-syntax.md) pour plus d’informations.|
|*lib*|Un ou plusieurs noms de bibliothèque. CL passe ces noms à l’éditeur de liens.|
|*command-file*|Un fichier qui contient plusieurs options et les noms de fichiers. Consultez [fichiers de commandes CL](cl-command-files.md) pour plus d’informations.|
|*link-opt*|Un ou plusieurs [Options de l’éditeur de liens MSVC](linker-options.md). CL passe ces options à l’éditeur de liens.|

Vous pouvez spécifier n’importe quel nombre d’options, les noms de fichiers et les noms de bibliothèques, tant que le nombre de caractères sur la ligne de commande ne dépasse pas 1 024, la limite imposée par le système d’exploitation.

Pour plus d’informations sur la valeur de retour de cl.exe, consultez [valeur de retour de cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
>  Limite de 1 024 caractères d’entrée de ligne de commande n’est pas garantie reste la même dans les versions futures de Windows.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)
