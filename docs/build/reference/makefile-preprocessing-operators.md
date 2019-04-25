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
ms.openlocfilehash: 4101c2fe30bcba44e9b69ed4d6d022845e6e8904
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321577"
---
# <a name="makefile-preprocessing-operators"></a>Opérateurs de prétraitement d'un makefile

Les expressions de prétraitement makefile peuvent utiliser des opérateurs qui agissent sur des valeurs constantes, les codes de sortie des commandes, chaînes, macros et chemins d’accès du système de fichiers. Pour évaluer l’expression, le préprocesseur commence par développer les macros, puis il exécute les commandes et il effectue enfin les opérations. Les opérations sont évaluées dans l'ordre de leur groupement explicite entre parenthèses, puis dans l'ordre de priorité des opérateurs. Il en résulte une valeur constante.

Le **défini par** opérateur est un opérateur logique qui agit sur un nom de macro. L’expression **DEFINED (**_nom_macro_**)** a la valeur true si *nom_macro* est défini, même si elle n’a pas de valeur assignée. **Défini par** en association avec **! IF** ou **! ELSE IF** équivaut à **! IFDEF** ou **! IFDEF ELSE**. Toutefois, contrairement à ces directives, **défini par** peut être utilisé dans des expressions complexes.

Le **EXIST** opérateur est un opérateur logique qui agit sur un chemin d’accès de système de fichiers. **EXIST (**_chemin d’accès_**)** a la valeur true si *chemin d’accès* existe. Le résultat à partir de **EXIST** peut être utilisé dans des expressions binaires. Si *chemin d’accès* contient des espaces, placez-le entre guillemets doubles.

Pour comparer deux chaînes, utilisez l’égalité (**==**) opérateur ou l’inégalité (**! =**) opérateur. Placez les chaînes entre guillemets doubles.

Constantes entières peuvent utiliser les opérateurs unaires pour la négation numérique (**-**), un complément (**~**) et la négation logique (**!**).

Les expressions peuvent utiliser les opérateurs suivants. Les opérateurs de même priorité sont regroupés ensemble et les groupes sont répertoriés dans l'ordre de priorité décroissante. Les opérateurs unaires s’associent avec l’opérande de droite. Les opérateurs binaires de même priorité associent les opérandes de gauche à droite.

|Opérateur|Description|
|--------------|-----------------|
|**DEFINED (** *nom_macro* **)**|Génère une valeur logique pour l’état actuel de la définition de *nom_macro*.|
|**EXIST (** *chemin d’accès* **)**|Génère une valeur logique pour l’existence d’un fichier au *chemin d’accès*.|
|||
|**\!**|NOT logique unaire.|
|**~**|Complément à un unaire|
|**-**|Négation unaire|
|||
|**&#42;**|Multiplication|
|**/**|Division|
|**%**|Modulo (reste)|
|||
|**+**|Addition|
|**-**|Soustraction|
|||
|**\<\<**|Déplacement à gauche au niveau du bit|
|**>>**|Déplacement à droite au niveau du bit|
|||
|**\<=**|Inférieur ou égal à|
|**>=**|Supérieur ou égal à|
|**\<**|Inférieur à|
|**>**|Supérieur à|
|||
|**==**|Égalité|
|**\!=**|Inégalité|
|||
|**&**|AND au niveau du bit|
|**^**|XOR au niveau du bit|
|**&#124;**|OR au niveau du bit|
|||
|**&&**|AND logique|
|||
|**&#124;&#124;**|OR logique|

> [!NOTE]
> L’opérateur XOR au niveau du bit (**^**) est le même que le caractère d’échappement et doivent être échappés (en tant que **^^**) lorsqu’il est utilisé dans une expression.

## <a name="see-also"></a>Voir aussi

- [Expressions utilisées dans le prétraitement d’un makefile](expressions-in-makefile-preprocessing.md)