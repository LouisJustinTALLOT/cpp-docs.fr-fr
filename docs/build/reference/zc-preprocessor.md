---
title: '/Zc : préprocesseur (activer le mode de conformité de préprocesseur)'
description: 'Utilisez l’option de compilateur/Zc : preprocesseur pour activer la prise en charge du compilateur pour un préprocesseur conforme au standard.'
ms.date: 09/10/2020
f1_keywords:
- preprocessor
- /Zc:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /Zc:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: 356434e4892966b9a9304021dd5d8770dcc2f8b1
ms.sourcegitcommit: 6280a4c629de0f638ebc2edd446de2a9b11f0406
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "90042903"
---
# <a name="zcpreprocessor-enable-preprocessor-conformance-mode"></a>`/Zc:preprocessor` (Activer le mode de conformité de préprocesseur)

Cette option active un préprocesseur basé sur des jetons conforme aux normes C99 et C++ 11 et versions ultérieures. Pour plus d’informations, consultez [vue d’ensemble du nouveau préprocesseur MSVC](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntaxe

> **`/Zc:preprocessor`**[**-**]

## <a name="remarks"></a>Remarques

Utilisez l' **`/Zc:preprocessor`** option du compilateur pour activer le préprocesseur conforme. Vous pouvez utiliser **`/Zc:preprocessor-`** l’option pour spécifier explicitement le préprocesseur traditionnel (non conforme).

L' **`/Zc:preprocessor`** option est disponible à partir de Visual Studio 2019 version 16,5. Une version antérieure et incomplète de la nouvelle option de préprocesseur est disponible dans les versions de Visual Studio à partir de Visual Studio 2017 version 15,8. Pour plus d’informations, consultez [`/experimental:preprocessor`](experimental-preprocessor.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour inclure *`/Zc:preprocessor`* , puis cliquez sur **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
