---
title: __if_not_exists, instruction
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 7372ac127a7b4dd5c05d58cfecca25f87690b0ae
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178176"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists, instruction

L’instruction **__if_not_exists** teste si l’identificateur spécifié existe. S'il n'existe pas, le bloc d'instructions spécifié est exécuté.

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
|*publication*|Une ou plusieurs instructions à exécuter si l' *identificateur* n’existe pas.|

## <a name="remarks"></a>Notes

> [!CAUTION]
>  Pour obtenir les résultats les plus fiables, utilisez l’instruction **__if_not_exists** sous les contraintes suivantes.

- Appliquez l’instruction **__if_not_exists** uniquement aux types simples, et non aux modèles.

- Appliquez l’instruction **__if_not_exists** aux identificateurs à l’intérieur ou à l’extérieur d’une classe. N’appliquez pas l’instruction **__if_not_exists** à des variables locales.

- Utilisez l’instruction **__if_not_exists** uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, l’instruction **__if_not_exists** peut tester uniquement des types entièrement définis.

- Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.

Le complément de l’instruction **__if_not_exists** est l’instruction [__if_exists](../cpp/if-exists-statement.md) .

## <a name="example"></a>Exemple

Pour obtenir un exemple d’utilisation de **__if_not_exists**, consultez [__if_exists instruction](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[__if_exists, instruction](../cpp/if-exists-statement.md)
