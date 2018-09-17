---
title: '-Zc : auto (déduire le Type de Variable) | Microsoft Docs'
ms.custom: ''
ms.date: 02/28/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:auto
dev_langs:
- C++
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 09bb29b1baa6208f4b7473d8cbbc9a3abbe38e70
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45709590"
---
# <a name="zcauto-deduce-variable-type"></a>/Zc:auto (déduire le type de variable)

Le **/Zc : auto [-]** option du compilateur indique au compilateur comment utiliser le [auto, mot clé](../../cpp/auto-keyword.md) pour déclarer des variables. Si vous spécifiez l’option par défaut, **/Zc : auto**, le compilateur déduit le type de la variable déclarée de son expression d’initialisation. Si vous spécifiez **/Zc:auto-**, le compilateur alloue la variable à la classe de stockage automatique.

## <a name="syntax"></a>Syntaxe

> **/Zc:auto**[**-**]

## <a name="remarks"></a>Notes

Le standard C++ définit une signification originale et une autre révisée pour le mot clé `auto`. Avant Visual C++ 2010, le mot clé déclare une variable dans la classe de stockage automatique ; Autrement dit, une variable qui a une durée de vie locale. À partir de Visual C++ 2010, le mot clé déduit le type d’une variable à partir de l’expression d’initialisation de la déclaration. Utiliser le **/Zc : auto [-]** option du compilateur pour indiquer au compilateur d’utiliser la signification originale ou révisée de le `auto` mot clé. Le **/Zc : auto** option est activée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option ne change pas le paramètre par défaut **/Zc : auto**.

Le compilateur émet un message de diagnostic approprié si votre utilisation de la `auto` mot clé contredit actuel **/Zc : auto** option du compilateur. Pour plus d’informations, consultez [auto, mot clé](../../cpp/auto-keyword.md). Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Ajouter **/Zc : auto** ou **/Zc:auto-** à la **des options supplémentaires :** volet.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[auto, mot clé](../../cpp/auto-keyword.md)
