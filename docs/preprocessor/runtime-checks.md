---
description: 'En savoir plus sur : pragma runtime_checks'
title: runtime_checks, pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.runtime_checks
- runtime_checks_CPP
helpviewer_keywords:
- runtime_checks pragma
- pragmas, runtime_checks
ms.assetid: ae50b43f-f88d-47ad-a2db-3389e9e7df5b
ms.openlocfilehash: 2ee04751e9cc978487670314675d3fa4ae52bd3d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97342294"
---
# <a name="runtime_checks-pragma"></a>runtime_checks, pragma

Désactive ou restaure les paramètres [/RTC](../build/reference/rtc-run-time-error-checks.md) .

## <a name="syntax"></a>Syntaxe

> **#pragma runtime_checks ("** [ *runtime_checks* ] **",** { **Restore**  |  **off** } **)**

## <a name="remarks"></a>Notes

Vous ne pouvez pas activer une vérification au moment de l’exécution qui n’a pas été activée par une option du compilateur. Par exemple, si vous ne spécifiez pas `/RTCs` sur la ligne de commande, la spécification de `#pragma runtime_checks( "s", restore)` n’active pas la vérification du frame de pile.

Le pragma **runtime_checks** doit apparaître à l’extérieur d’une fonction et prend effet à la première fonction définie après l’affichage du pragma. Les arguments **restore** et **off** activent ou désactivent les options spécifiées dans **runtime_checks** .

Le pragma **runtime_checks** peut être égal à zéro ou plusieurs des paramètres indiqués dans le tableau suivant.

### <a name="parameters-of-the-runtime_checks-pragma"></a>Paramètres du pragma runtime_checks

| Paramètre(s) | Type de contrôle à l'exécution |
|--------------------|-----------------------------|
| **s** | Active la vérification de pile (frame). |
| **c** | Signale quand une valeur est assignée à un type de données plus petit qui se traduit par une perte de données. |
| **u** | Signale quand une variable est utilisée avant d’être définie. |

Ces paramètres sont les mêmes que ceux utilisés avec l' `/RTC` option de compilateur. Par exemple :

```cpp
#pragma runtime_checks( "sc", restore )
```

L'utilisation du pragma **runtime_checks** avec la chaîne vide (**""**) est une forme particulière de la directive :

- Quand vous utilisez le paramètre **off** , il active les vérifications des erreurs d’exécution énumérées dans le tableau ci-dessus, OFF.

- Quand vous utilisez le paramètre **Restore** , il réinitialise les vérifications d’erreurs au moment de l’exécution à celles que vous avez spécifiées à l’aide de l' `/RTC` option du compilateur.

```cpp
#pragma runtime_checks( "", off )
/* runtime checks are off in this region */
#pragma runtime_checks( "", restore )
```

## <a name="see-also"></a>Voir aussi

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
