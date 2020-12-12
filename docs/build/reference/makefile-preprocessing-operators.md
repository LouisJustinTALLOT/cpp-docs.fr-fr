---
description: 'En savoir plus sur : les opérateurs de prétraitement d’un Makefile'
title: Opérateurs de prétraitement d'un makefile
ms.date: 06/14/2018
helpviewer_keywords:
- operators [C++], makefile preprocessing
- EXIST operator
- preprocessing NMAKE makefile operators
- NMAKE program, operators
- DEFINED operator
- makefiles, preprocessing operators
ms.assetid: a46e4d39-afdb-43c1-ac3b-025d33e6ebdb
ms.openlocfilehash: 7cf68511eec26a9049a4b44f62126a28ddbf0282
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190781"
---
# <a name="makefile-preprocessing-operators"></a>Opérateurs de prétraitement d'un makefile

Les expressions de prétraitement makefile peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, chaînes, macros et chemins d’accès du système de fichiers. Pour évaluer l’expression, le préprocesseur commence par développer les macros, puis il exécute les commandes et il effectue enfin les opérations. Les opérations sont évaluées dans l'ordre de leur groupement explicite entre parenthèses, puis dans l'ordre de priorité des opérateurs. Il en résulte une valeur constante.

L’opérateur **défini** est un opérateur logique qui agit sur un nom de macro. L’expression **définie (**_nommacro_**)** a la valeur true si *macroname* est défini, même s’il n’a pas de valeur assignée. **Défini** en association avec **! Si** ou **! ELSE si** est équivalent à **! IFDEF** ou **! SINON IFDEF**. Toutefois, contrairement à ces directives, **defined** peut être utilisé dans des expressions complexes.

L’opérateur **exist** est un opérateur logique qui agit sur un chemin d’accès au système de fichiers. **Exist (**_path_**)** a la valeur true si le *chemin d’accès* existe. Le résultat de **exist** peut être utilisé dans des expressions binaires. Si le *chemin d’accès* contient des espaces, placez-le entre guillemets doubles.

Pour comparer deux chaînes, utilisez l’opérateur d’égalité ( **==** ) ou l’opérateur d’inégalité (**! =**). Placez les chaînes entre guillemets doubles.

Les constantes entières peuvent utiliser les opérateurs unaires pour la négation numérique ( **-** ), le complément à un ( **~** ) et la négation logique (**!**).

Les expressions peuvent utiliser les opérateurs suivants. Les opérateurs de même priorité sont regroupés ensemble et les groupes sont répertoriés dans l'ordre de priorité décroissante. Les opérateurs unaires s’associent avec l’opérande de droite. Les opérateurs binaires de même priorité associent les opérandes de gauche à droite.

|Opérateur|Description|
|--------------|-----------------|
|**Défini (** *nommacro* **)**|Produit une valeur logique pour l’état actuel de la définition de *nommacro*.|
|**Exist (** *chemin* **)**|Produit une valeur logique pour l’existence d’un fichier dans le *chemin d’accès*.|
|||
|**!**|NOT logique unaire.|
|**~**|Complément à 1 unaire.|
|**-**|Négation unaire|
|||
|**&#42;**|Multiplication.|
|**/**|Division.|
|**%**|Modulo (reste)|
|||
|**+**|Addition.|
|**-**|Soustraction.|
|||
|**\<\<**|Déplacement à gauche au niveau du bit|
|**>>**|Déplacement à droite au niveau du bit|
|||
|**\<=**|Inférieur ou égal à.|
|**>=**|Supérieur ou égal à.|
|**\<**|Inférieur à.|
|**>**|Supérieur à.|
|||
|**==**|Égalité|
|**!=**|Inégalité|
|||
|**&**|Opérateur AND au niveau du bit.|
|**^**|XOR au niveau du bit.|
|**&#124;**|Opérateur OR au niveau du bit.|
|||
|**&&**|AND logique.|
|||
|**&#124;&#124;**|OR logique.|

> [!NOTE]
> L’opérateur de bits XOR ( **^** ) est le même que le caractère d’échappement et doit être placé dans une séquence d’échappement (comme **^^** ) lorsqu’il est utilisé dans une expression.

## <a name="see-also"></a>Voir aussi

- [Expressions dans le prétraitement d’un Makefile](expressions-in-makefile-preprocessing.md)
