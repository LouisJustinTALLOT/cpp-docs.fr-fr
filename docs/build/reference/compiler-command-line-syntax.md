---
description: 'En savoir plus sur les éléments suivants : syntaxe du compilateur Command-Line'
title: Syntaxe Command-Line du compilateur MSVC
ms.date: 11/04/2016
helpviewer_keywords:
- syntax, CL compiler command line
- cl.exe compiler, command-line syntax
ms.assetid: acba2c1c-0803-4a3a-af25-63e849b930a2
ms.openlocfilehash: 91340aa543f0e79d3071b93921742b8147918b2e
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97182214"
---
# <a name="compiler-command-line-syntax"></a>Syntaxe de la ligne de commande du compilateur

La ligne de commande CL utilise la syntaxe suivante :

```
CL [option...] file... [option | file]... [lib...] [@command-file] [/link link-opt...]
```

Le tableau suivant décrit l’entrée de la commande CL.

|Entrée|Signification|
|-----------|-------------|
|*option*|Une ou plusieurs [options CL](compiler-options.md). Notez que toutes les options s’appliquent à tous les fichiers sources spécifiés. Les options sont spécifiées par une barre oblique (/) ou un tiret (-). Si une option accepte un argument, la description de l’option indique si un espace est autorisé entre l’option et les arguments. Les noms des options (à l’exception de l’option/HELP) respectent la casse. Pour plus d’informations, consultez [ordre des options CL](order-of-cl-options.md) .|
|`file`|Nom d’un ou plusieurs fichiers sources, fichiers. obj ou bibliothèques. CL compile les fichiers sources et passe les noms des fichiers. objet des bibliothèques à l’éditeur de liens. Pour plus d’informations, consultez [syntaxe du nom de fichier CL](cl-filename-syntax.md) .|
|*lib*|Un ou plusieurs noms de bibliothèques. CL passe ces noms à l’éditeur de liens.|
|*fichier de commandes*|Fichier qui contient plusieurs options et noms de fichiers. Pour plus d’informations, consultez [fichiers de commandes CL](cl-command-files.md) .|
|*lien-opt*|Une ou plusieurs [options de l’éditeur de liens MSVC](linker-options.md). CL passe ces options à l’éditeur de liens.|

Vous pouvez spécifier n’importe quel nombre d’options, de noms de fichiers et de noms de bibliothèque, à condition que le nombre de caractères de la ligne de commande ne dépasse pas 1024, la limite imposée par le système d’exploitation.

Pour plus d’informations sur la valeur de retour de cl.exe, consultez [valeur de retour de cl.exe](return-value-of-cl-exe.md) .

> [!NOTE]
> La limite d’entrée de ligne de commande de 1024 caractères n’est pas garantie pour rester la même dans les versions futures de Windows.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)
