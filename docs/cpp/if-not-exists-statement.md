---
title: __if_not_exists, instruction
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 845597460cdc0ce83adcbba1f47a78c83735cbf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62183633"
---
# <a name="ifnotexists-statement"></a>__if_not_exists, instruction

Le **__if_not_exists** instruction teste si l’identificateur spécifié existe. S'il n'existe pas, le bloc d'instructions spécifié est exécuté.

## <a name="syntax"></a>Syntaxe

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*identifier*|Identificateur dont vous voulez tester l'existence.|
|*statements*|Une ou plusieurs instructions à exécuter si *identificateur* n’existe pas.|

## <a name="remarks"></a>Notes

> [!CAUTION]
>  Pour obtenir des résultats plus fiables, utilisez le **__if_not_exists** instruction sous les contraintes suivantes.

- Appliquer le **__if_not_exists** instruction uniquement aux types simples, et non des modèles.

- Appliquer le **__if_not_exists** instruction aux identificateurs à la fois à l’intérieur ou en dehors d’une classe. N’appliquez pas le **__if_not_exists** instruction aux variables locales.

- Utilisez le **__if_not_exists** instruction uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, le **__if_not_exists** instruction peut tester uniquement les types entièrement définis.

- Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.

Le complément de la **__if_not_exists** instruction est la [__if_exists](../cpp/if-exists-statement.md) instruction.

## <a name="example"></a>Exemple

Pour obtenir un exemple illustrant comment utiliser **__if_not_exists**, consultez [__if_exists, instruction](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[__if_exists, instruction](../cpp/if-exists-statement.md)