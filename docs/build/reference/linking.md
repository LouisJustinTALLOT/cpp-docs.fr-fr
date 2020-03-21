---
title: Informations de référence sur l’éditeur de liens MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: d46874b5eaff889834df284ba90e6c6f196d8d66
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80079511"
---
# <a name="linking"></a>Liaison

Dans un C++ projet, l’étape de *liaison* est effectuée une fois que le compilateur a compilé le code source dans des fichiers objets (*. obj). L’éditeur de liens (Link. exe) combine les fichiers objets en un seul fichier exécutable.

Les options de l’éditeur de liens peuvent être définies à l’intérieur ou à l’extérieur de Visual Studio. Dans Visual Studio, vous accédez aux options de l’éditeur de liens en cliquant avec le bouton droit sur un nœud de projet dans **Explorateur de solutions** et en choisissant **Propriétés** pour afficher les pages de propriétés. Choisissez **éditeur de liens** dans le volet gauche pour développer le nœud et afficher toutes les options.

## <a name="linker-command-line-syntax"></a>Syntaxe de la ligne de commande de l’éditeur de liens

Quand vous exécutez un lien en dehors de Visual Studio, vous pouvez spécifier l’entrée d’une ou de plusieurs façons :

- Sur la ligne de commande

- Utilisation des fichiers de commandes

- Dans les variables d’environnement

LINK First traite les options spécifiées dans la variable d’environnement LINK, puis les options dans l’ordre dans lequel elles sont spécifiées sur la ligne de commande et dans les fichiers de commandes. Si une option est répétée avec des arguments différents, le dernier traité est prioritaire.

Les options s’appliquent à l’ensemble de la Build ; aucune option ne peut être appliquée à des fichiers d’entrée spécifiques.

Pour exécuter le lien. EXE, utilisez la syntaxe de commande suivante :

```
LINK arguments
```

Les `arguments` incluent des options et des noms de fichiers et peuvent être spécifiés dans n’importe quel ordre. Les options sont traitées en premier, puis fichiers. Utilisez un ou plusieurs espaces ou tabulations pour séparer les arguments.

> [!NOTE]
>  Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes de Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

## <a name="command-line"></a>Ligne de commande

Sur la ligne de commande, une option se compose d’un spécificateur d’option, un tiret (-) ou une barre oblique (/), suivi du nom de l’option. Les noms d’options ne peuvent pas être abrégés. Certaines options prennent un argument, spécifié après un signe deux-points ( :). Aucun espace ou tabulation n’est autorisé dans une spécification d’option, sauf dans une chaîne entre guillemets dans l’option/COMMENT. Spécifiez des arguments numériques en notation décimale ou de langage C. Les noms d’option et leurs arguments de mot clé ou de nom de fichier ne respectent pas la casse, mais les identificateurs en tant qu’arguments respectent la casse.

Pour passer un fichier à l’éditeur de liens, spécifiez le nom de fichier sur la ligne de commande après la commande LINK. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier, et vous pouvez utiliser des caractères génériques dans le nom de fichier. Si vous omettez le point (.) et l’extension de nom de fichier, LINK suppose que. obj pour rechercher le fichier. LINK n’utilise pas les extensions de nom de fichier ou l’absence de ces extensions pour faire des hypothèses sur le contenu des fichiers. il détermine le type de fichier en l’examinant et le traite en conséquence.

Link. exe retourne la valeur zéro en cas de réussite (aucune erreur).  Dans le cas contraire, l’éditeur de liens retourne le numéro d’erreur qui a arrêté le lien.  Par exemple, si l’éditeur de liens génère LNK1104, l’éditeur de liens retourne 1104.  En conséquence, le numéro d’erreur le plus bas retourné en cas d’erreur par l’éditeur de liens est 1000.  Une valeur de retour de 128 représente un problème de configuration avec le système d’exploitation ou un fichier. config ; le chargeur n’a pas chargé Link. exe ou C2. dll.

## <a name="link-command-files"></a>Fichiers de commandes LINK

Vous pouvez passer des arguments de ligne de commande à LINK sous la forme d’un fichier de commandes. Pour spécifier un fichier de commandes à l’éditeur de liens, utilisez la syntaxe suivante :

> **Lien \@** <em>fichiercommandes</em>

*Fichiercommandes* est le nom d’un fichier texte. Aucun espace ou tabulation n’est autorisé entre le signe arobase ( **\@** ) et le nom de fichier. Il n’y a pas d’extension par défaut ; vous devez spécifier le nom de fichier complet, y compris toute extension. Les caractères génériques ne peuvent pas être utilisés. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier. LINK n’utilise pas de variable d’environnement pour rechercher le fichier.

Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des tabulations (comme sur la ligne de commande) et par des caractères de saut de ligne.

Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commandes. Vous pouvez utiliser plusieurs fichiers de commandes dans une commande LINK. Le lien accepte l’entrée du fichier de commandes comme si elle avait été spécifiée à cet emplacement sur la ligne de commande. Les fichiers de commandes ne peuvent pas être imbriqués. LINK renvoie le contenu des fichiers de commandes, sauf si l’option [/nologo](nologo-suppress-startup-banner-linker.md) est spécifiée.

## <a name="example"></a>Exemple

La commande suivante pour générer une DLL passe les noms des fichiers objets et des bibliothèques dans des fichiers de commandes distincts et utilise un troisième fichier de commandes pour la spécification de l’option/EXPORTS :

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables d'environnement de LINK

L'outil LINK utilise les variables d'environnement suivantes :

- Liez et \_\_de liaison, si elle est définie. L’outil LINK ajoute les options et les arguments définis dans la variable d’environnement LINK, puis ajoute les options et les arguments définis dans le lien \_\_ variable d’environnement aux arguments de ligne de commande avant le traitement.

- LIB, si elle est définie. Les outils de liaison utilisent le chemin d’accès LIB pour rechercher un objet, une bibliothèque ou un autre fichier spécifié sur la ligne de commande ou par l’option [/base](base-base-address.md) . Il utilise également le chemin d’accès LIB pour rechercher un fichier .pdb nommé dans un objet. La variable LIB peut contenir une ou plusieurs spécifications de chemin d'accès, séparées par des points-virgules. Un chemin d'accès doit pointer vers le sous-répertoire \lib de votre installation Visual C++.

- PATH, si l’outil doit exécuter CVTRES et ne peut pas trouver le fichier dans le même répertoire que LINK. (LINK exige CVTRES pour lier un fichier. res.) Le chemin d’accès doit pointer vers le sous-répertoire C++ \bin de votre installation visuelle.

- TMP, pour spécifier un répertoire lors de la liaison de fichiers OMF ou .res.

## <a name="see-also"></a>Voir aussi

[C/C++ construction de références](c-cpp-building-reference.md)
options de l' [éditeur de liens MSVC](linker-options.md)
[les fichiers de définition de module (. def)](module-definition-dot-def-files.md)
la [prise en charge de l’éditeur de liens pour les dll à chargement différé](linker-support-for-delay-loaded-dlls.md)
