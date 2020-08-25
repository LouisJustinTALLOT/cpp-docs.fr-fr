---
title: '&lt;iomanip&gt;'
ms.date: 11/04/2016
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
ms.openlocfilehash: f3f6c4886d22c7cd12b29950c114fbcde8905c28
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845742"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Incluez l'en-tête standard `iostreams`\<iomanip> pour définir plusieurs manipulateurs qui acceptent chacun un argument unique.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iomanip>
```

## <a name="remarks"></a>Notes

Chacun de ces manipulateurs retourne un type non spécifié, appelé `T1` via `T10` , qui surcharge à la fois l' `basic_istream` \<**Elem**, **Tr**> `::` [opérateur>>](../standard-library/istream-operators.md#op_gt_gt) et l' `basic_ostream` \<**Elem**, **Tr**> `::` [opérateur<<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulateurs

|Nom|Description|
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Obtient une valeur monétaire, éventuellement au format international.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Obtient une heure dans une structure d'heure à l'aide d'un format spécifié.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Fournit une valeur monétaire, éventuellement au format international.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Fournit une heure dans une structure d'heure et une chaîne de format à utiliser.|
|[cotation](../standard-library/iomanip-functions.md#quoted)|Autorise un aller-retour pratique des chaînes avec des opérateurs d'insertion et d'extraction.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Efface les indicateurs spécifiés.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Définir la base pour les entiers.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Définit le caractère qui sera utilisé pour remplir les espaces dans un affichage aligné à droite.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Définit les indicateurs spécifiés.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Définit la précision des valeurs à virgule flottante.|
|[setw](../standard-library/iomanip-functions.md#setw)|Spécifie la largeur de la zone d'affichage.|

## <a name="see-also"></a>Voir aussi

[Référence des fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)\
[Sécurité des threads dans la bibliothèque C++ standard](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[iostream, programmation](../standard-library/iostream-programming.md)\
[Conventions iostreams](../standard-library/iostreams-conventions.md)
