---
title: '&lt;iomanip&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs:
- C++
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a410dae35771d89b9d9ae72c8221501f051d10e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846569"
---
# <a name="ltiomanipgt"></a>&lt;iomanip&gt;

Inclure le `iostreams` en-tête standard \<iomanip > pour définir plusieurs manipulateurs qui acceptent chacun un argument unique.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iomanip>

```

## <a name="remarks"></a>Notes

Chacun de ces manipulateurs retourne un type non spécifié, appelé **T1** à **T10**, qui surcharge à la fois `basic_istream`\<**Elem**, **Tr**>`::`[operator>>](../standard-library/istream-operators.md#op_gt_gt) et `basic_ostream`\<**Elem**, **Tr**>`::`[operator<<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulateurs

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Obtient une valeur monétaire, éventuellement au format international.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Obtient une heure dans une structure d'heure à l'aide d'un format spécifié.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Fournit une valeur monétaire, éventuellement au format international.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Fournit une heure dans une structure d'heure et une chaîne de format à utiliser.|
|[quoted](../standard-library/iomanip-functions.md#quoted)|Autorise un aller-retour pratique des chaînes avec des opérateurs d'insertion et d'extraction.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Efface les indicateurs spécifiés.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Définir la base pour les entiers.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Définit le caractère qui sera utilisé pour remplir les espaces dans un affichage aligné à droite.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Définit les indicateurs spécifiés.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Définit la précision des valeurs à virgule flottante.|
|[setw](../standard-library/iomanip-functions.md#setw)|Spécifie la largeur de la zone d'affichage.|

## <a name="see-also"></a>Voir aussi

[Informations de référence sur les fichiers d’en-tête](../standard-library/cpp-standard-library-header-files.md)<br/>
[Sécurité des threads dans la bibliothèque standard C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programmation](../standard-library/iostream-programming.md)<br/>
[iostreams, conventions](../standard-library/iostreams-conventions.md)<br/>
