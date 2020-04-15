---
title: Informations de référence sur l’éditeur de liens MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 2503e212e7325fc97f9057861cb85d5cf0571094
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336497"
---
# <a name="linking"></a>Liaison

Dans le cadre d’un projet CD, *l’étape de liaison* est effectuée après que le compilateur a compilé le code source dans les fichiers d’objets (obj). Le linker (link.exe) combine les fichiers d’objets en un seul fichier exécutable.

Les options Linker peuvent être définies à l’intérieur ou à l’extérieur de Visual Studio. Au sein de Visual Studio, vous accédez aux options de linker en cliquant à droite sur un nœud de projet dans **Solution Explorer** et en choisissant **des propriétés** pour afficher les pages de propriété. Choisissez **Linker** dans le volet gauche pour étendre le nœud et voir toutes les options.

## <a name="linker-command-line-syntax"></a>Syntaxe de ligne de commande Linker

Lorsque vous exécutez LINK en dehors de Visual Studio, vous pouvez spécifier l’entrée d’une ou plusieurs façons :

- Sur la ligne de commande

- Utilisation de fichiers de commande

- Dans les variables de l’environnement

LINK premiers processus options spécifiées dans la variable de l’environnement LINK, suivies d’options dans l’ordre, ils sont spécifiés sur la ligne de commande et dans les fichiers de commande. Si une option est répétée avec des arguments différents, la dernière traitée a préséance.

Les options s’appliquent à l’ensemble de la construction; aucune option ne peut être appliquée à des fichiers d’entrée spécifiques.

Pour exécuter LINK. EXE, utilisez la syntaxe de commande suivante :

```
LINK arguments
```

Les `arguments` options et les noms de fichiers comprennent et peuvent être spécifiés dans n’importe quel ordre. Les options sont traitées d’abord, puis les fichiers. Utilisez un ou plusieurs espaces ou onglets pour séparer les arguments.

> [!NOTE]
> Vous pouvez démarrer cet outil uniquement à partir de l’invite de commande Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

## <a name="command-line"></a>Ligne de commande

Sur la ligne de commande, une option se compose d’un spécificateur d’option, soit d’un tiret (-) soit d’une barre oblique avant (/), suivi du nom de l’option. Les noms d’options ne peuvent pas être abrégés. Certaines options prennent un argument, spécifié après un côlon (:). Aucun espace ou onglet n’est autorisé dans une spécification d’option, sauf dans une chaîne citée dans l’option /COMMENT. Spécifier les arguments numériques dans la notation décimale ou en langue C. Les noms d’options et leurs arguments de mot clé ou de nom de fichier ne sont pas sensibles aux cas, mais les identificateurs en tant qu’arguments sont sensibles aux cas.

Pour transmettre un fichier au lien, spécifiez le nom de fichier sur la ligne de commande après la commande LINK. Vous pouvez spécifier un chemin absolu ou relatif avec le nom de fichier, et vous pouvez utiliser des wildcards dans le nom de fichier. Si vous ometez le point (.) et l’extension du nom de fichier, LINK suppose .obj dans le but de trouver le fichier. LINK n’utilise pas d’extensions de nom de fichier ou l’absence d’entre elles pour faire des hypothèses sur le contenu des fichiers; il détermine le type de fichier en l’examinant et le traite en conséquence.

link.exe renvoie zéro pour le succès (pas d’erreurs).  Dans le cas contraire, le lien retourne le numéro d’erreur qui a arrêté le lien.  Par exemple, si le linker génère LNK1104, le linker renvoie 1104.  Par conséquent, le nombre d’erreurs le plus bas retourné sur une erreur par le lien est de 1000.  Une valeur de retour de 128 représente un problème de configuration avec le système d’exploitation ou un fichier .config; le chargeur n’a pas charger soit link.exe ou c2.dll.

## <a name="link-command-files"></a>Fichiers de commandes LINK

Vous pouvez passer des arguments de ligne de commande à LINK sous la forme d’un fichier de commande. Pour spécifier un fichier de commande au lien, utilisez la syntaxe suivante :

> **Fichier \@ ** <em>de commande</em> LINK

Le *fichier de commande* est le nom d’un fichier texte. Aucun espace ou onglet n’est**\@** autorisé entre le signe à l’affiche ( ) et le nom de fichier. Il n’y a pas d’extension par défaut; vous devez spécifier le nom de fichier complet, y compris toute extension. Les wildcards ne peuvent pas être utilisés. Vous pouvez spécifier un chemin absolu ou relatif avec le nom de fichier. LINK n’utilise pas de variable d’environnement pour rechercher le fichier.

Dans le fichier de commande, les arguments peuvent être séparés par des espaces ou des onglets (comme sur la ligne de commande) et par des caractères newline.

Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commande. Vous pouvez utiliser plus d’un fichier de commande dans une commande LINK. LINK accepte l’entrée du fichier de commande comme si elle avait été spécifiée à cet endroit sur la ligne de commande. Les fichiers de commandement ne peuvent pas être imbriqués. LINK fait écho au contenu des fichiers de commande, à moins que l’option [/NOLOGO](nologo-suppress-startup-banner-linker.md) ne soit spécifiée.

## <a name="example"></a>Exemple

La commande suivante pour construire un DLL passe les noms des fichiers d’objets et des bibliothèques dans des fichiers de commande distincts et utilise un troisième fichier de commande pour la spécification de l’option /EXPORTS:

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables d'environnement de LINK

L'outil LINK utilise les variables d'environnement suivantes :

- LINK \_et\_LINK , si défini. L’outil LINK prépend les options et les arguments définis dans la variable \_\_ de l’environnement LINK et annexe les options et les arguments définis dans l’environnement LINK variable aux arguments de la ligne de commande avant le traitement.

- LIB, si elle est définie. Les outils LINK utilisent le chemin LIB lors de la recherche d’un objet, d’une bibliothèque ou d’un autre fichier spécifié sur la ligne de commande ou par l’option [/BASE.](base-base-address.md) Il utilise également le chemin d’accès LIB pour rechercher un fichier .pdb nommé dans un objet. La variable LIB peut contenir une ou plusieurs spécifications de chemin d'accès, séparées par des points-virgules. Un chemin d'accès doit pointer vers le sous-répertoire \lib de votre installation Visual C++.

- PATH, si l’outil doit exécuter CVTRES et ne peut pas trouver le fichier dans le même répertoire que LINK. (LINK exige que CVTRES lient un fichier .res.) PATH doit indiquer la sous-direction de votre installation Visual C.

- TMP, pour spécifier un répertoire lors de la liaison de fichiers OMF ou .res.

## <a name="see-also"></a>Voir aussi

[C/CMd Building Reference](c-cpp-building-reference.md)
[MSVC Linker Options](linker-options.md)
[Module-Definition (.def) Files](module-definition-dot-def-files.md)
[Linker Support for Delay-Loaded DLL](linker-support-for-delay-loaded-dlls.md)
