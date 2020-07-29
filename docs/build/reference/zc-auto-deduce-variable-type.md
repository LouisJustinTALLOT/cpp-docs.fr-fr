---
title: /Zc:auto (déduire le type de variable)
ms.date: 02/28/2018
f1_keywords:
- /Zc:auto
helpviewer_keywords:
- -Zc compiler options (C++)
- Deduce variable type (C++)
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 5f5bc102-44c3-4688-bbe1-080594dcee5c
ms.openlocfilehash: 866cccb490136e951effb1f8da20877c8d5ec763
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217179"
---
# <a name="zcauto-deduce-variable-type"></a>`/Zc:auto`(Déduire le type de variable)

L' **`/Zc:auto`** option du compilateur indique au compilateur comment utiliser le [ `auto` mot clé](../../cpp/auto-keyword.md) pour déclarer des variables. Si vous spécifiez l’option par défaut, **`/Zc:auto`** , le compilateur déduit le type de la variable déclarée à partir de son expression d’initialisation. Si vous spécifiez **`/Zc:auto-`** , le compilateur alloue la variable à la classe de stockage automatique.

## <a name="syntax"></a>Syntaxe

> **`/Zc:auto`**[**`-`**]

## <a name="remarks"></a>Notes

La norme C++ définit une signification originale et modifiée pour le **`auto`** mot clé. Avant Visual Studio 2010, le mot clé déclare une variable dans la classe de stockage automatique. autrement dit, une variable qui a une durée de vie locale. À compter de Visual Studio 2010, le mot clé déduit le type d’une variable à partir de l’expression d’initialisation de la déclaration. Utilisez l' **`/Zc:auto`** option du compilateur pour indiquer au compilateur d’utiliser la signification révisée du **`auto`** mot clé. L' **`/Zc:auto`** option est activée par défaut. L' [`/permissive-`](permissive-standards-conformance.md) option ne change pas le paramètre par défaut **`/Zc:auto`** .

Le compilateur émet un message de diagnostic approprié si votre utilisation du **`auto`** mot clé contredit l' **`/Zc:auto`** option de compilateur actuelle. Pour plus d’informations, consultez [ `auto` mot clé](../../cpp/auto-keyword.md). Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Ajoutez **`/Zc:auto`** ou **`/Zc:auto-`** au volet **options supplémentaires :** .

## <a name="see-also"></a>Voir aussi

[`/Zc`Conformité](zc-conformance.md)<br/>
[`auto`Mot](../../cpp/auto-keyword.md)
