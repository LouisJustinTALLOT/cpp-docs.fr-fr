---
title: Fichiers de commandes LINK
ms.date: 09/05/2018
f1_keywords:
- link
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
ms.openlocfilehash: 3a116736a6ed00ea4d378e68c6f515aa96ea2f99
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676445"
---
# <a name="link-command-files"></a>Fichiers de commandes LINK

Vous pouvez passer des arguments de ligne de commande pour le lien sous la forme d’un fichier de commandes. Pour spécifier un fichier de commandes pour l’éditeur de liens, utilisez la syntaxe suivante :

> **LIEN \@**  <em>/commandfile</em>

Le */commandfile* est le nom d’un fichier texte. Aucun espace ou un onglet n’est autorisé entre le signe arobase (**\@**) et le nom de fichier. Il n’existe aucune extension par défaut ; Vous devez spécifier le nom de fichier complet, y compris de n’importe quelle extension. Impossible d’utiliser des caractères génériques. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier. LIEN n’utilise pas une variable d’environnement pour rechercher le fichier.

Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des tabulations (comme sur la ligne de commande) et par les caractères de saut de ligne.

Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commandes. Vous pouvez utiliser plusieurs fichiers de commandes dans une commande de lien. LIEN accepte l’entrée de fichier de commandes comme si elle était spécifiée à cet emplacement sur la ligne de commande. Fichiers de commandes ne peuvent pas être imbriquées. LIEN renvoie le contenu des fichiers de commandes, à moins que le [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md) option est spécifiée.

## <a name="example"></a>Exemple

La commande suivante pour générer une DLL passe les noms des fichiers objets et bibliothèques dans des fichiers de commande distincte et utilise un troisième fichier de commandes pour la spécification de l’option /EXPORTS :

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)