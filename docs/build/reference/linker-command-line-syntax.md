---
title: Syntaxe de la ligne de commande de l'Éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- linker [C++], syntax
- linker command line [C++]
- LINK tool [C++], command-line syntax
ms.assetid: e2a31e17-77bd-4e74-9305-75b105b26539
ms.openlocfilehash: 55171c1f16b43e08b5c4a6b078c82f4ed08855d5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422726"
---
# <a name="linker-command-line-syntax"></a>Syntaxe de la ligne de commande de l'Éditeur de liens

Pour exécuter le lien. EXE, utilisez la syntaxe de commande suivante :

```
LINK arguments
```

Le `arguments` incluent des options et des noms de fichiers et peuvent être spécifiés dans n’importe quel ordre. Les options sont traitées en premier, puis les fichiers. Utiliser un ou plusieurs espaces ou des tabulations pour séparer les arguments.

> [!NOTE]
>  Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes de Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

Sur la ligne de commande, une option est constituée d’un spécificateur d’option, un tiret (-) ou une barre oblique (/), suivi du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent un argument spécifié après le signe deux-points ( :)). Aucun espace ni les onglets ne sont autorisés dans une spécification d’option, à l’exception dans une chaîne entre guillemets dans l’option/comment. Spécifiez les arguments numériques en notation décimale ou en langage C. Les noms des options et leurs arguments de mot clé ou le nom de fichier ne sont pas sensible à la casse, mais les identificateurs en tant qu’arguments respectent la casse.

Pour transmettre un fichier à l’éditeur de liens, spécifiez le nom de fichier sur la ligne de commande après la commande de lien. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier, et vous pouvez utiliser des caractères génériques dans le nom de fichier. Si vous omettez le point (.) et l’extension de nom de fichier, le lien suppose .obj pour rechercher le fichier. LIEN n’utilise pas les extensions de nom de fichier ou l’absence d’eux pour émettre des hypothèses sur le contenu des fichiers ; Il détermine le type de fichier en examinant l’il et le traite en conséquence.

Link.exe retourne zéro pour la réussite (aucune erreur).  Sinon, l’éditeur de liens retourne le numéro d’erreur qui a interrompu le lien.  Par exemple, si l’éditeur de liens génère LNK1104, l’éditeur de liens retourne 1104.  En conséquence, le plus petit numéro d’erreur renvoyé en cas d’erreur par l’éditeur de liens est 1000.  Une valeur de retour de 128 représente un problème de configuration avec le système d’exploitation ou un fichier .config ; le chargeur n’a pas chargé link.exe ou c2.dll.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
