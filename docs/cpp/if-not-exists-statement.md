---
title: __if_not_exists, instruction
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: e99fcee440bd69eabafec693df99d347f3aee828
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88560281"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists, instruction

L' **`__if_not_exists`** instruction vérifie si l’identificateur spécifié existe. S'il n'existe pas, le bloc d'instructions spécifié est exécuté.

## <a name="syntax"></a>Syntaxe

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Paramètres

*identificateur*\
Identificateur dont vous voulez tester l'existence.

*publication*\
Une ou plusieurs instructions à exécuter si l' *identificateur* n’existe pas.

## <a name="remarks"></a>Notes

> [!CAUTION]
> Pour obtenir les résultats les plus fiables, utilisez l' **`__if_not_exists`** instruction sous les contraintes suivantes.

- Appliquez l' **`__if_not_exists`** instruction uniquement aux types simples, et non aux modèles.

- Appliquez l' **`__if_not_exists`** instruction aux identificateurs à l’intérieur ou à l’extérieur d’une classe. N’appliquez pas l' **`__if_not_exists`** instruction à des variables locales.

- Utilisez l' **`__if_not_exists`** instruction uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, l' **`__if_not_exists`** instruction peut tester uniquement des types entièrement définis.

- Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.

Le complément de l' **`__if_not_exists`** instruction est l’instruction [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **`__if_not_exists`** , consultez [__if_exists instruction](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Instruction __if_exists](../cpp/if-exists-statement.md)
