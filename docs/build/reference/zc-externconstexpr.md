---
title: /Zc:externConstexpr (Activer les variables externes constexpr)
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: db5a8892bcc11538c3ff883a0e9a3a27db0ee14f
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91502797"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>`/Zc:externConstexpr` (Activer les variables extern constexpr)

L' **`/Zc:externConstexpr`** option du compilateur indique au compilateur qu’il doit se conformer à la norme C++ et autoriser la liaison externe pour les **`constexpr`** variables. Par défaut, Visual Studio fournit toujours une **`constexpr`** liaison interne variable, même si vous spécifiez le **`extern`** mot clé.

## <a name="syntax"></a>Syntax

> **`/Zc:externConstexpr`**[**`-`**]

## <a name="remarks"></a>Remarques

L' **`/Zc:externConstexpr`** option de compilateur force le compilateur à appliquer une liaison externe aux variables déclarées à l’aide de `extern constexpr` . Dans les versions antérieures de Visual Studio, et par défaut, ou si **`/Zc:externConstexpr-`** est spécifié, Visual Studio applique la liaison interne aux **`constexpr`** variables même si le **`extern`** mot clé est utilisé. L' **`/Zc:externConstexpr`** option est disponible à partir de Visual Studio 2017 Update 15,6. et est désactivé par défaut. L' [`/permissive-`](permissive-standards-conformance.md) option n’est pas activée **`/Zc:externConstexpr`** .

Si un fichier d’en-tête contient une variable déclarée `extern constexpr` , il doit être marqué [`__declspec(selectany)`](../../cpp/selectany.md) pour fusionner les déclarations dupliquées en une seule instance du fichier binaire lié. Dans le cas contraire, vous risquez de voir des erreurs de l’éditeur de liens, par exemple LNK2005, pour les violations de la règle à une seule définition.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Ajoutez **`/Zc:externConstexpr`** ou **`/Zc:externConstexpr-`** au volet **options supplémentaires :** .

## <a name="see-also"></a>Voir aussi

[`/Zc` Conformité](zc-conformance.md)<br/>
[`auto` Mot](../../cpp/auto-cpp.md)
