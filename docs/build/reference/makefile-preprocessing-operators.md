---
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
ms.openlocfilehash: 212f39ee62008b391977aaa91d5c8c4fadfd9730
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336471"
---
# <a name="makefile-preprocessing-operators"></a>Opérateurs de prétraitement d'un makefile

Les expressions de prétraitement makefile peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, chaînes, macros et chemins d’accès du système de fichiers. Pour évaluer l’expression, le préprocesseur commence par développer les macros, puis il exécute les commandes et il effectue enfin les opérations. Les opérations sont évaluées dans l'ordre de leur groupement explicite entre parenthèses, puis dans l'ordre de priorité des opérateurs. Il en résulte une valeur constante.

**L’opérateur DEFINED** est un opérateur logique qui agit sur un nom macro. L’expression **DEFINED**_(macroname)_**)** est vraie si *la macroname* est définie, même si elle n’a pas de valeur assignée. **DEFINED** en combinaison avec **! SI** ou **! ELSE IF** est équivalent à **! IFDEF** ou **! SINON IFDEF**. Cependant, contrairement à ces directives, **DEFINED** peut être utilisé dans des expressions complexes.

**L’opérateur EXIST** est un opérateur logique qui agit sur une trajectoire de système de fichiers. **EXIST (**_chemin_**)** est vrai si le *chemin* existe. Le résultat **d’EXIST** peut être utilisé dans les expressions binaires. Si *le chemin* contient des espaces, l’enfermer en double guillemets.

Pour comparer deux chaînes, utilisez**==** l’opérateur d’égalité () ou l’opérateur**d’inégalité**( ! ) . Placez les chaînes entre guillemets doubles.

Integer constants peuvent utiliser les opérateurs unary pour la négation numérique (**-**), son complément (**~**), et la négation logique (**!**).

Les expressions peuvent utiliser les opérateurs suivants. Les opérateurs de même priorité sont regroupés ensemble et les groupes sont répertoriés dans l'ordre de priorité décroissante. Les opérateurs unaires s’associent avec l’opérande de droite. Les opérateurs binaires de même priorité associent les opérandes de gauche à droite.

|Opérateur|Description|
|--------------|-----------------|
|**DEFINED(** *macroname* **)**|Produit une valeur logique pour l’état de définition actuelle de *la macroname*.|
|**EXIST (** *chemin* **)**|Produit une valeur logique pour l’existence d’un fichier sur *le chemin*.|
|||
|**!**|NOT logique unaire.|
|**~**|Unary son complément.|
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
|**\<=**|Inférieur ou égal à|
|**>=**|Supérieur ou égal à|
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
> L’opérateur bitwise**^** XOR ( ) est le même que **^^** le caractère d’évasion, et doit être échappé (comme ) quand il est utilisé dans une expression.

## <a name="see-also"></a>Voir aussi

- [Expressions dans Makefile Preprocessing](expressions-in-makefile-preprocessing.md)
