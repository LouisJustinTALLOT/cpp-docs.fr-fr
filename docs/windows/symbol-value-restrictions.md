---
title: Restrictions de la valeur de symbole | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.symbol.restrictions.value
dev_langs:
- C++
helpviewer_keywords:
- symbols [C++], value restrictions
- restrictions, symbol values
ms.assetid: 32467ec3-690b-4cd0-a4d0-7d189a3296cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c0f6939cfb9cd1dc72026441d946431097a5c3d7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375279"
---
# <a name="symbol-value-restrictions"></a>Restrictions relatives à la valeur d'un symbole

Une valeur de symbole peut être un entier exprimé de façon normale pour les directives de préprocesseur #define. Voici quelques exemples de valeurs de symboles :

```
18
4001
0x0012
-3456
```

Les valeurs de symboles des ressources (accélérateurs, images bitmap, curseurs, boîtes de dialogue, icônes, menus, tables de chaînes et informations de version) doivent être des nombres décimaux compris entre 0 et 32 767 (mais en aucun cas des valeurs hexadécimales). Les valeurs de symboles de certaines ressources, telles que les contrôles de boîte de dialogue ou des chaînes spécifiques de la table de chaînes, peuvent être comprises entre 0 et 65 534 ou -32 768 et 32 767.

Les symboles des ressources sont des nombres de 16 bits. Vous pouvez les entrer en tant que nombres signés ou non signés. Toutefois, ils sont utilisés de façon interne en tant qu'entiers non signés. Les nombres négatifs sont castés en leur valeur positive correspondante.

Voici quelques limitations des valeurs de symboles :

- L'environnement de développement Visual Studio et MFC utilisent certaines plages de nombres à des fins spéciales. Tous les nombres avec le bit le plus significatif défini (de -32 768 à -1 ou de 32 768 à 65 534, en fonction du signe) sont réservés par MFC.

- Vous ne pouvez pas définir une valeur de symbole à l'aide d'autres chaînes de symboles. Par exemple, la définition de symbole suivante n'est pas prise en charge :

    ```cpp
    #define IDC_MYEDIT  IDC_OTHEREDIT  //not supported
    ```

- Vous ne pouvez pas utiliser de macros de préprocesseur avec des arguments en tant que définitions de valeur. Exemple :

    ```cpp
    #define   IDD_ABOUT  ID(7) //not supported
    ```

   n'est pas une expression valide, quelle que soit la valeur de `ID` au moment de la compilation.

- Votre application peut comporter un fichier existant contenant des symboles définis par des expressions. Pour plus d’informations sur la façon d’inclure les symboles en tant que symboles en lecture seule, consultez [symboles à l’aide de partagés (lecture seule) ou calculés](../windows/including-shared-read-only-or-calculated-symbols.md).

Pour plus d’informations sur les plages numériques, consultez [TN023 : ressources MFC Standard](../mfc/tn023-standard-mfc-resources.md).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Modification de la valeur numérique d’un symbole](../windows/changing-a-symbol-s-numeric-value.md)<br/>
[Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)<br/>
[ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)