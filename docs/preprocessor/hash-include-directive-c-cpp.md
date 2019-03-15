---
title: '#Include, Directive (C/C++)'
ms.date: 11/04/2016
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 67a44574a5a72a7b7addc0ed3d7b51cd3eb5b984
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821386"
---
# <a name="include-directive-cc"></a>#include, directive (C/C++)

Indique au préprocesseur de traiter le contenu d'un fichier spécifique, comme s'il figurait dans le programme source à l'emplacement où figure la directive.

## <a name="syntax"></a>Syntaxe

```
#include  "path-spec"
#include  <path-spec>
```

## <a name="remarks"></a>Notes

Vous pouvez organiser les définitions de constantes et de macros dans des fichiers include, puis utiliser **#include** directives pour les ajouter à n’importe quel fichier source. Les fichiers Include sont également utiles pour incorporer des déclarations de variables externes et de types de données complexes. Les types peuvent être définis et nommés une seule fois dans un fichier Include créé à cet effet.

Le *spécification de chemin d’accès* est un nom de fichier qui peut éventuellement être précédé d’une spécification de répertoire. Le nom de fichier doit désigner un fichier existant. La syntaxe de la *path-spec* dépend du système d’exploitation sur lequel le programme est compilé.

Pour plus d’informations sur la façon de référencer des assemblys dans une application C++ qui est compilé à l’aide de [/CLR](../build/reference/clr-common-language-runtime-compilation.md), consultez [#using](../preprocessor/hash-using-directive-cpp.md).

Les deux formes de syntaxe provoquent le remplacement de cette directive par le contenu complet du fichier Include spécifié. La différence entre ces deux formes concerne l’ordre dans lequel le préprocesseur recherche les fichiers d’en-tête lorsque le chemin d’accès est spécifié de manière incomplète. Le tableau ci-dessous montre la différence entre les deux formes de syntaxe.

|Forme syntaxique|Action|
|---|------------|
|Forme avec guillemets|Le préprocesseur recherche les fichiers Include dans l'ordre suivant :<br/><br/> (1) dans le même répertoire que le fichier qui contient le **#include** instruction.<br/><br/> (2) dans les répertoires d’actuellement ouverts fichiers include, dans l’ordre inverse dans lequel ils ont été ouverts. La recherche commence dans le répertoire du fichier Include parent et continue vers le haut, dans les répertoires de tous les fichiers Include grands-parents.<br/><br/> (3) le long du tracé qui est spécifié par chaque **/I** option du compilateur.<br/><br/> (4) le long des tracés spécifiés par la variable d’environnement INCLUDE.|
|Forme avec crochets pointus|Le préprocesseur recherche les fichiers Include dans l'ordre suivant :<br/><br/> (1) le long du tracé qui est spécifié par chaque **/I** option du compilateur.<br/><br/> (2) lors de la compilation s’effectue sur la ligne de commande, avec les chemins d’accès spécifiés par la variable d’environnement INCLUDE.|

Le préprocesseur arrête de chercher dès qu'il trouve un fichier portant le nom spécifié. Si vous placez une spécification de chemin d’accès complet et non équivoque pour le fichier include entre guillemets doubles (**» «**), le préprocesseur recherche uniquement dans ce chemin d’accès et ignore les répertoires standards.

Si le nom de fichier placé entre guillemets doubles est un chemin d’accès incomplet, le préprocesseur commence la recherche dans le répertoire du fichier parent. Un fichier parent est le fichier qui contient le **#include** directive. Par exemple, si vous incluez un fichier nommé *fichier2* dans un fichier nommé *file1*, *file1* est le fichier parent.

Inclure les fichiers peuvent être « imbriqués ». Autrement dit, un **#include** directive peut apparaître dans un fichier nommé par un autre **#include** directive. Par exemple, *fichier2* peut inclure *fichier3*. Dans ce cas, *file1* serait toujours le parent de *fichier2*, mais il serait le « grand-parent » de *fichier3*.

Lorsque des fichiers Include sont imbriqués et que la compilation s'effectue à partir de la ligne de commande, la recherche dans les répertoires commence dans les répertoires du fichier parent, puis se poursuit dans les répertoires de tous les fichiers grands-parents. Autrement dit, la recherche commence par rapport au répertoire contenant la source actuellement traitée. Si le fichier est introuvable, la recherche se déplace vers les répertoires spécifiés par la [/I (autres répertoires include)](../build/reference/i-additional-include-directories.md) option du compilateur. Finalement, la recherche s'effectue dans les répertoires spécifiés par la variable d'environnement INCLUDE.

À partir de l’environnement de développement Visual Studio, la variable d’environnement INCLUDE est ignorée. Pour plus d’informations sur la façon de définir les répertoires dans lesquels sont recherchés les fichiers include, cela s’applique également à la variable d’environnement LIB, consultez [VC ++ Directories Property Page](../build/reference/vcpp-directories-property-page.md).

Cet exemple illustre l'inclusion d'un fichier à l'aide de crochets pointus :

```
#include <stdio.h>
```

Cet exemple ajoute le contenu du fichier nommé STDIO.H dans le programme source. Les crochets pointus au préprocesseur de rechercher les répertoires spécifiés par la variable d’environnement INCLUDE pour STDIO. H, une fois qu’il recherche dans les répertoires spécifiés par la **/I** option du compilateur.

L'exemple suivant illustre l'inclusion d'un fichier en utilisant la forme entre guillemets :

```
#include "defs.h"
```

Cet exemple ajoute dans le programme source le contenu du fichier spécifié par DEFS.H. Les guillemets indiquent que le préprocesseur doit chercher d'abord dans le répertoire contenant le fichier source parent.

L'imbrication des fichiers Include peut atteindre jusqu'à 10 niveaux. Lorsque l’imbriquée **#include** est traité, le préprocesseur continue à insérer le fichier include englobant dans le fichier source d’origine.

**Section spécifique à Microsoft**

Pour localiser les fichiers sources, le préprocesseur recherche tout d’abord les répertoires spécifiés par la **/I** option du compilateur. Si le **/I** option n’est pas présente ou échoue, le préprocesseur utilise la variable d’environnement INCLUDE pour rechercher tous les fichiers include entre crochets. La variable d’environnement INCLUDE et **/I** l’option du compilateur peuvent contenir plusieurs chemins d’accès, séparés par des points-virgules (**;**). Si plusieurs répertoires apparaît dans le cadre de la **/I** option ou au sein de la variable d’environnement INCLUDE, le préprocesseur les recherches effectuées dans l’ordre dans lequel ils apparaissent.

Par exemple, la commande

```
CL /ID:\MSVC\INCLUDE MYPROG.C
```

indique au préprocesseur de rechercher les fichiers Include tels que STDIO.H dans le répertoire D:\MSVC\INCLUDE\. Les commandes

```
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

ont le même effet. Si les deux jeux de recherches échouent, une erreur irrécupérable du compilateur est générée.

Si le nom de fichier est complètement spécifié pour un fichier Include et comporte un chemin d’accès comprenant un signe deux-points (par exemple, F:\MSVC\SPECIAL\INCL\TEST.H), le préprocesseur suit le chemin d’accès.

Pour les fichiers include spécifiés comme `#include "path-spec"`, recherche commence par le répertoire du fichier parent et se poursuit dans les répertoires de tous les fichiers grands-parents. Autrement dit, la recherche commence par rapport au répertoire qui contient le fichier source qui contient le **#include** directive qui est en cours de traitement. S'il n'existe aucun fichier grand-parent et que le fichier n'a pas été trouvé, la recherche se poursuit comme si le nom de fichier était placé entre crochets pointus.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)<br/>
[/I (autres répertoires include)](../build/reference/i-additional-include-directories.md)<br/>
