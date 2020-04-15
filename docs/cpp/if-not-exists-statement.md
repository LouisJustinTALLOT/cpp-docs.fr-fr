---
title: __if_not_exists, instruction
ms.date: 11/04/2016
f1_keywords:
- __if_not_exists_cpp
helpviewer_keywords:
- __if_not_exists keyword [C++]
ms.assetid: a2f322d4-e96f-4a32-954e-4323d20c6e32
ms.openlocfilehash: 1118f9fcca525b2b2d5869fb507ee974d2b0d28f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374138"
---
# <a name="__if_not_exists-statement"></a>__if_not_exists, instruction

**L'__if_not_exists** indique l’existence de l’identifiant spécifié. S'il n'existe pas, le bloc d'instructions spécifié est exécuté.

## <a name="syntax"></a>Syntaxe

```
__if_not_exists ( identifier ) {
statements
};
```

#### <a name="parameters"></a>Paramètres

|Paramètre|Description|
|---------------|-----------------|
|*Identificateur*|Identificateur dont vous voulez tester l'existence.|
|*Déclarations*|Une ou plusieurs instructions à exécuter si *l’identifiant* n’existe pas.|

## <a name="remarks"></a>Notes

> [!CAUTION]
> Pour obtenir les résultats les plus fiables, utilisez **l’énoncé __if_not_exists** sous les contraintes suivantes.

- Appliquer la **déclaration __if_not_exists** uniquement à des types simples, pas des modèles.

- Appliquer la **__if_not_exists** déclaration aux identificateurs à l’intérieur ou à l’extérieur d’une classe. N’appliquez pas **l'__if_not_exists** déclaration aux variables locales.

- Utilisez la **__if_not_exists** déclaration uniquement dans le corps d’une fonction. En dehors du corps d’une fonction, **l'__if_not_exists** instruction ne peut tester que des types entièrement définis.

- Lorsque vous vérifiez la présence de fonctions surchargées, vous ne pouvez pas effectuer le test sur une forme spécifique de la surcharge.

Le complément à la **déclaration __if_not_exists** est la [déclaration __if_exists.](../cpp/if-exists-statement.md)

## <a name="example"></a>Exemple

Par exemple sur la façon d’utiliser **__if_not_exists**, voir [__if_exists Déclaration](../cpp/if-exists-statement.md).

## <a name="see-also"></a>Voir aussi

[Instructions de sélection](../cpp/selection-statements-cpp.md)<br/>
[Mots clés](../cpp/keywords-cpp.md)<br/>
[Déclaration __if_exists](../cpp/if-exists-statement.md)
