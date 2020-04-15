---
title: Syntaxe de la ligne de commande du compilateur MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 6a56474b537d78a3d0bea8a74d9082007cd2e295
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320543"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe de la ligne de commande du compilateur

La ligne de commande CL utilise la syntaxe suivante :

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Le tableau suivant décrit l’entrée à la commande CL.

|Entrée|Signification|
|-----------|-------------|
|*Option*|Une ou plusieurs [options CL](compiler-options.md). Notez que toutes les options s’appliquent à tous les fichiers sources spécifiés. Les options sont spécifiées soit par une barre oblique avant (/) soit par un tableau de bord (-). Si une option prend un argument, la description de l’option documente si un espace est autorisé entre l’option et les arguments. Les noms d’options (à l’exception de l’option /HELP) sont sensibles aux cas. Voir [Order of CL Options](order-of-cl-options.md) pour plus d’informations.|
|`file`|Le nom d’un ou plusieurs fichiers sources, fichiers .obj, ou bibliothèques. CL compile les fichiers source et transmet les noms des fichiers et bibliothèques .obj au lien. Voir [CL Filename Syntax](cl-filename-syntax.md) pour plus d’informations.|
|*Lib*|Un ou plusieurs noms de bibliothèque. CL transmet ces noms au lien.|
|*fichier de commande*|Un fichier qui contient plusieurs options et noms de fichiers. Consultez [les fichiers de commandement cl](cl-command-files.md) pour plus d’informations.|
|*lien-opt*|Une ou plusieurs [options MSVC Linker](linker-options.md). CL transmet ces options au lien.|

Vous pouvez spécifier n’importe quel nombre d’options, noms de fichiers et noms de bibliothèque, tant que le nombre de caractères sur la ligne de commande ne dépasse pas 1024, la limite dictée par le système d’exploitation.

Pour plus d’informations sur la valeur de retour de cl.exe, voir [Valeur de retour de cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> La limite d’entrée de la ligne de commande de 1024 caractères n’est pas garantie de rester la même dans les versions futures de Windows.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)
