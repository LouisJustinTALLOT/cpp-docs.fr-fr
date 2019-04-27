---
title: Référence de l’éditeur de liens MSVC
ms.date: 12/10/2018
ms.assetid: bb736587-d13b-4f3c-8982-3cc2c015c59c
ms.openlocfilehash: 3a9eebef0a264b0131311b5ca96011a4d56264a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62176627"
---
# <a name="linking"></a>Liaison

Dans un projet C++, le *liaison* étape est effectuée une fois que le compilateur a compilé le code source dans des fichiers objet (*.obj). L’éditeur de liens (link.exe) combine les fichiers objets en un seul fichier exécutable. 

Options de l’éditeur de liens peuvent être définies à l’intérieur ou en dehors de Visual Studio. Dans Visual Studio, vous accédez aux options de l’éditeur de liens en cliquant sur un nœud de projet dans **l’Explorateur de solutions** et en choisissant **propriétés** pour afficher les pages de propriétés. Choisissez **l’éditeur de liens** dans le volet gauche, développez le nœud et de voir toutes les options. 


## <a name="linker-command-line-syntax"></a>Syntaxe de ligne de commande de l’éditeur de liens

Lorsque vous exécutez le lien en dehors de Visual Studio, vous pouvez spécifier l’entrée dans une ou plusieurs façons :

- Sur la ligne de commande

- À l’aide de fichiers de commandes

- Dans les variables d’environnement

Options de processus premier lien spécifié dans la variable d’environnement LINK, suivi d’options dans l’ordre, elles sont spécifiées sur la ligne de commande et dans les fichiers de commandes. Si une option est répétée avec différents arguments, le dernier traité est prioritaire.

Options s’appliquent à la génération complète ; Aucun options ne peuvent être appliquées à des fichiers d’entrée spécifiques.

Pour exécuter le lien. EXE, utilisez la syntaxe de commande suivante :

```
LINK arguments
```

Le `arguments` incluent des options et des noms de fichiers et peuvent être spécifiés dans n’importe quel ordre. Les options sont traitées en premier, puis les fichiers. Utiliser un ou plusieurs espaces ou des tabulations pour séparer les arguments.

> [!NOTE]
>  Vous pouvez démarrer cet outil uniquement à partir de l’invite de commandes de Visual Studio. Vous ne pouvez pas le démarrer à partir d'une invite de commandes système ni de l'Explorateur de fichiers.

## <a name="command-line"></a>Ligne de commande

Sur la ligne de commande, une option est constituée d’un spécificateur d’option, un tiret (-) ou une barre oblique (/), suivi du nom de l’option. Noms d’options ne peuvent pas être abrégés. Certaines options acceptent un argument spécifié après le signe deux-points ( :)). Aucun espace ni les onglets ne sont autorisés dans une spécification d’option, à l’exception dans une chaîne entre guillemets dans l’option/comment. Spécifiez les arguments numériques en notation décimale ou en langage C. Les noms des options et leurs arguments de mot clé ou le nom de fichier ne sont pas sensible à la casse, mais les identificateurs en tant qu’arguments respectent la casse.

Pour transmettre un fichier à l’éditeur de liens, spécifiez le nom de fichier sur la ligne de commande après la commande de lien. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier, et vous pouvez utiliser des caractères génériques dans le nom de fichier. Si vous omettez le point (.) et l’extension de nom de fichier, le lien suppose .obj pour rechercher le fichier. LIEN n’utilise pas les extensions de nom de fichier ou l’absence d’eux pour émettre des hypothèses sur le contenu des fichiers ; Il détermine le type de fichier en examinant l’il et le traite en conséquence.

Link.exe retourne zéro pour la réussite (aucune erreur).  Sinon, l’éditeur de liens retourne le numéro d’erreur qui a interrompu le lien.  Par exemple, si l’éditeur de liens génère LNK1104, l’éditeur de liens retourne 1104.  En conséquence, le plus petit numéro d’erreur renvoyé en cas d’erreur par l’éditeur de liens est 1000.  Une valeur de retour de 128 représente un problème de configuration avec le système d’exploitation ou un fichier .config ; le chargeur n’a pas chargé link.exe ou c2.dll.

## <a name="link-command-files"></a>Fichiers de commandes LINK

Vous pouvez passer des arguments de ligne de commande pour le lien sous la forme d’un fichier de commandes. Pour spécifier un fichier de commandes pour l’éditeur de liens, utilisez la syntaxe suivante :

> **LIEN \@**  <em>/commandfile</em>

Le */commandfile* est le nom d’un fichier texte. Aucun espace ou un onglet n’est autorisé entre le signe arobase (**\@**) et le nom de fichier. Il n’existe aucune extension par défaut ; Vous devez spécifier le nom de fichier complet, y compris de n’importe quelle extension. Impossible d’utiliser des caractères génériques. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier. LIEN n’utilise pas une variable d’environnement pour rechercher le fichier.

Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des tabulations (comme sur la ligne de commande) et par les caractères de saut de ligne.

Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commandes. Vous pouvez utiliser plusieurs fichiers de commandes dans une commande de lien. LIEN accepte l’entrée de fichier de commandes comme si elle était spécifiée à cet emplacement sur la ligne de commande. Fichiers de commandes ne peuvent pas être imbriquées. LIEN renvoie le contenu des fichiers de commandes, à moins que le [/NOLOGO](nologo-suppress-startup-banner-linker.md) option est spécifiée.

## <a name="example"></a>Exemple

La commande suivante pour générer une DLL passe les noms des fichiers objets et bibliothèques dans des fichiers de commande distincte et utilise un troisième fichier de commandes pour la spécification de l’option /EXPORTS :

```cmd
link /dll @objlist.txt @liblist.txt @exports.txt
```

## <a name="link-environment-variables"></a>Variables d'environnement de LINK

L'outil LINK utilise les variables d'environnement suivantes :

- LIEN et \_lien\_, s’il est défini. L’outil LINK ajoute les options et les arguments définis dans la variable d’environnement LINK et ajoute les options et arguments définis dans le \_lien\_ variable d’environnement pour les arguments de ligne de commande avant le traitement.

- LIB, si elle est définie. L’outil LINK utilise le chemin d’accès LIB lors de la recherche pour un objet, bibliothèque ou un autre fichier spécifié sur la ligne de commande ou par le [/de BASE](base-base-address.md) option. Il utilise également le chemin d’accès LIB pour rechercher un fichier .pdb nommé dans un objet. La variable LIB peut contenir une ou plusieurs spécifications de chemin d'accès, séparées par des points-virgules. Un chemin d'accès doit pointer vers le sous-répertoire \lib de votre installation Visual C++.

- PATH, si l’outil doit exécuter CVTRES et ne peut pas trouver le fichier dans le même répertoire que LINK. (LINK requiert CVTRES pour lier un fichier .res.) PATH doit pointer vers le sous-répertoire \bin de votre installation Visual C++.

- TMP, pour spécifier un répertoire lors de la liaison de fichiers OMF ou .res.

## <a name="see-also"></a>Voir aussi

[Référence à la génération C/C++](c-cpp-building-reference.md)
[Options de l’éditeur de liens MSVC](linker-options.md)
[les fichiers de définition de Module (.def)](module-definition-dot-def-files.md)
[prise en charge de l’éditeur de liens pour DLL à chargement différé](linker-support-for-delay-loaded-dlls.md)
