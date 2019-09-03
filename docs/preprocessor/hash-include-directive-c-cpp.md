---
title: '#include, directive (C/C++)'
ms.date: 08/29/2019
f1_keywords:
- '#include'
helpviewer_keywords:
- preprocessor, directives
- '#include directive'
- include directive (#include)
ms.assetid: 17067dc0-8db1-4f2d-b43e-ec12ecf83238
ms.openlocfilehash: 0792f522427e5658de992969745878894fbd454d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220251"
---
# <a name="include-directive-cc"></a>#include, directive (CC++/)

Indique au préprocesseur de traiter le contenu d'un fichier spécifique, comme s'il figurait dans le programme source à l'emplacement où figure la directive.

## <a name="syntax"></a>Syntaxe

> **#include** "*path-spec*" \
> **#include** *chemin d’accès-spécification* \<>

## <a name="remarks"></a>Notes

Vous pouvez organiser les définitions de constantes et de macros dans des fichiers include, puis utiliser des directives de **#include** pour les ajouter à n’importe quel fichier source. Les fichiers Include sont également utiles pour incorporer des déclarations de variables externes et de types de données complexes. Les types peuvent être définis et nommés une seule fois dans un fichier Include créé à cet effet.

*Path-spec* est un nom de fichier qui peut éventuellement être précédé d’une spécification de répertoire. Le nom de fichier doit désigner un fichier existant. La syntaxe de *path-spec* dépend du système d’exploitation sur lequel le programme est compilé.

Pour plus d’informations sur la façon de référencer des assemblys dans une C++ application compilée à l’aide de [/clr](../build/reference/clr-common-language-runtime-compilation.md), consultez [#using](../preprocessor/hash-using-directive-cpp.md).

Les deux formes de syntaxe provoquent le remplacement de cette directive par le contenu complet du fichier Include spécifié. La différence entre ces deux formes concerne l’ordre dans lequel le préprocesseur recherche les fichiers d’en-tête lorsque le chemin d’accès est spécifié de manière incomplète. Le tableau ci-dessous montre la différence entre les deux formes de syntaxe.

|Forme syntaxique|Action|
|---|------------|
|Forme avec guillemets|Le préprocesseur recherche les fichiers Include dans l'ordre suivant :<br/><br/> 1) dans le même répertoire que le fichier qui contient l’instruction **#include** .<br/><br/> 2) dans les répertoires des fichiers include actuellement ouverts, dans l’ordre inverse dans lequel ils ont été ouverts. La recherche commence dans le répertoire du fichier Include parent et continue vers le haut, dans les répertoires de tous les fichiers Include grands-parents.<br/><br/> 3) sur le chemin d’accès spécifié par chaque option du compilateur **/i** .<br/><br/> 4) le long des chemins d’accès spécifiés par la variable d’environnement INCLUDe.|
|Forme avec crochets pointus|Le préprocesseur recherche les fichiers Include dans l'ordre suivant :<br/><br/> 1) le long du chemin d’accès spécifié par chaque option du compilateur **/i** .<br/><br/> 2) lors de la compilation sur la ligne de commande, le long des chemins d’accès spécifiés par la variable d’environnement INCLUDe.|

Le préprocesseur arrête de chercher dès qu'il trouve un fichier portant le nom spécifié. Si vous placez une spécification de chemin d’accès complète et non équivoque pour le fichier include entre`" "`guillemets doubles (), le préprocesseur effectue une recherche uniquement dans cette spécification de chemin d’accès et ignore les répertoires standard.

Si le nom de fichier placé entre guillemets doubles est un chemin d’accès incomplet, le préprocesseur commence la recherche dans le répertoire du fichier parent. Un fichier parent est le fichier qui contient la directive **#include** . Par exemple, si vous incluez un fichier nommé *fichier2* dans un fichier nommé *fichier1*, *fichier1* est le fichier parent.

Les fichiers include peuvent être «imbriqués»: Une directive **#include** peut apparaître dans un fichier nommé par une autre directive **#include** . Par exemple, *fichier2* peut inclure *fichier3*. Dans ce cas, *fichier1* est toujours le parent de *fichier2*, mais il s’agit du «grand-parent» de *fichier3*.

Lorsque des fichiers include sont imbriqués et que la compilation se produit sur la ligne de commande, la recherche dans les répertoires commence dans les répertoires du fichier parent. Ensuite, il passe par les répertoires de tous les fichiers grand-parent. Autrement dit, la recherche commence par rapport au répertoire contenant la source actuellement traitée. Si le fichier est introuvable, la recherche se déplace vers les répertoires spécifiés par l’option de compilateur [/i (autres répertoires Include)](../build/reference/i-additional-include-directories.md) . Finalement, la recherche s'effectue dans les répertoires spécifiés par la variable d'environnement INCLUDE.

Dans l’environnement de développement Visual Studio, la variable d’environnement INCLUDe est ignorée. Pour plus d’informations sur la façon de définir les répertoires dans lesquels sont recherchés les fichiers include et les fichiers de bibliothèque, consultez la [page de propriétés Répertoires VC + +](../build/reference/vcpp-directories-property-page.md).

Cet exemple illustre l'inclusion d'un fichier à l'aide de crochets pointus :

```C
#include <stdio.h>
```

Cet exemple ajoute le contenu du fichier nommé STDIO.H dans le programme source. Les crochets angulaires font en sorte que le préprocesseur recherche les répertoires spécifiés par la variable d’environnement INCLUDe pour STDIO. H, après avoir effectué une recherche dans les répertoires spécifiés par l’option du compilateur **/i** .

L'exemple suivant illustre l'inclusion d'un fichier en utilisant la forme entre guillemets :

```C
#include "defs.h"
```

Cet exemple ajoute dans le programme source le contenu du fichier spécifié par DEFS.H. Les guillemets indiquent que le préprocesseur doit chercher d'abord dans le répertoire contenant le fichier source parent.

L'imbrication des fichiers Include peut atteindre jusqu'à 10 niveaux. Lorsque le **#include** imbriqué est traité, le préprocesseur continue à insérer le fichier include englobant dans le fichier source d’origine.

**Section spécifique à Microsoft**

Pour localiser les fichiers sources les, le préprocesseur commence par Rechercher les répertoires spécifiés par l’option du compilateur **/i** . Si l’option **/i** n’est pas présente ou si elle échoue, le préprocesseur utilise la variable d’environnement include pour rechercher tous les fichiers include entre crochets pointus. La variable d’environnement INCLUDe et l’option de compilateur **/i** peuvent contenir plusieurs chemins d’accès, séparés par des points-virgules ( **;** ). Si plusieurs répertoires s’affichent dans le cadre de l’option **/i** ou dans la variable d’environnement include, le préprocesseur les recherche dans l’ordre dans lequel ils apparaissent.

Par exemple, la commande

```cmd
CL /ID:\MSVC\INCLUDE MYPROG.C
```

indique au préprocesseur de rechercher les fichiers Include tels que STDIO.H dans le répertoire D:\MSVC\INCLUDE\. Les commandes

```cmd
SET INCLUDE=D:\MSVC\INCLUDE
CL MYPROG.C
```

ont le même effet. Si les deux jeux de recherches échouent, une erreur irrécupérable du compilateur est générée.

Si le nom de fichier est complètement spécifié pour un fichier Include et comporte un chemin d’accès comprenant un signe deux-points (par exemple, F:\MSVC\SPECIAL\INCL\TEST.H), le préprocesseur suit le chemin d’accès.

Pour les fichiers include spécifiés `#include "path-spec"`en tant que, la recherche dans les répertoires commence par le répertoire du fichier parent, puis se poursuit par les répertoires de tous les fichiers grand-parent. Autrement dit, la recherche commence par rapport au répertoire qui contient le fichier source qui contient la directive **#include** en cours de traitement. S'il n'existe aucun fichier grand-parent et que le fichier n'a pas été trouvé, la recherche se poursuit comme si le nom de fichier était placé entre crochets pointus.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Directives de préprocesseur](../preprocessor/preprocessor-directives.md)\
[/I (autres répertoires Include)](../build/reference/i-additional-include-directories.md)
