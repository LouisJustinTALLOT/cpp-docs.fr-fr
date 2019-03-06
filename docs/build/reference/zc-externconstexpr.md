---
title: '/ Zc : externconstexpr (activer les variables extern constexpr)'
ms.date: 02/28/2018
f1_keywords:
- /Zc:externConstexpr
helpviewer_keywords:
- -Zc:externConstexpr compiler option (C++)
- extern constexpr variables (C++)
ms.assetid: 4da5e33a-2e4d-4ed2-8616-bd8f43265c27
ms.openlocfilehash: b0af9fa0cc61b82853e64808897b30aaf2fa887d
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57415160"
---
# <a name="zcexternconstexpr-enable-extern-constexpr-variables"></a>/ Zc : externconstexpr (activer les variables extern constexpr)

Le **/Zc : externconstexpr** option du compilateur indique au compilateur de se conformer à la norme C++ et permettre une liaison externe pour `constexpr` variables. Par défaut, Visual Studio donne toujours un `constexpr` variable une liaison interne, même si vous spécifiez le `extern` mot clé.

## <a name="syntax"></a>Syntaxe

> **/Zc:externConstexpr**[**-**]

## <a name="remarks"></a>Notes

Le **/Zc : externconstexpr** option du compilateur indique au compilateur d’appliquer une liaison externe aux variables déclarées à l’aide de `extern constexpr`. Dans les versions antérieures de Visual Studio et, par défaut ou si **/Zc:externConstexpr-** est spécifié, Visual Studio applique une liaison interne à `constexpr` même si de variables le `extern` mot clé est utilisé. Le **/Zc : externconstexpr** option est disponible à partir de Visual Studio 2017 mise à jour 15.6. et est désactivée par défaut. Le [/ permissive-](permissive-standards-conformance.md) option n’active pas **/Zc : externconstexpr**.

Si un fichier d’en-tête contient une variable déclarée `extern constexpr`, il doit être marqué [__declspec (selectany)](../../cpp/selectany.md) afin de fusionner les déclarations en double dans une seule instance dans le fichier binaire lié. Sinon, vous pouvez voir erreurs de l’éditeur de liens, par exemple, LNK2005, les violations de la règle de définition unique.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Pour définir cette option de compilateur dans Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Ajouter **/Zc : externconstexpr** ou **/Zc:externConstexpr-** à la **des options supplémentaires :** volet.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](../../build/reference/zc-conformance.md)<br/>
[auto, mot clé](../../cpp/auto-keyword.md)
