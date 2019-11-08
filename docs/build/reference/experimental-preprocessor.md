---
title: '/experimental : préprocesseur (activer le mode de conformité de préprocesseur)'
description: 'Utilisez l’option du compilateur de préprocesseur/experimental : pour activer la prise en charge expérimentale du compilateur pour un préprocesseur conforme au standard.'
ms.date: 10/31/2019
f1_keywords:
- preprocessor
- /experimental:preprocessor
helpviewer_keywords:
- preprocessor conformance
- /experimental:preprocessor
- Enable preprocessor conformance mode
ms.openlocfilehash: cb1ac63d2c12083975139455d8625544cb419adf
ms.sourcegitcommit: 2362d15b5eb18d27773c3f7522da3d0eed9e2571
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73754045"
---
# <a name="experimentalpreprocessor-enable-preprocessor-conformance-mode"></a>/experimental : préprocesseur (activer le mode de conformité de préprocesseur)

Cette option active un préprocesseur expérimental basé sur des jetons qui est plus conforme aux normes C++ 11, y compris les fonctionnalités du préprocesseur C99. Pour plus d’informations, consultez [vue d’ensemble du préprocesseur expérimental MSVC](../../preprocessor/preprocessor-experimental-overview.md).

## <a name="syntax"></a>Syntaxe

> **/experimental : préprocesseur**[ **-** ]

## <a name="remarks"></a>Notes

Utilisez l’option du compilateur de **préprocesseur/experimental :** pour activer le préprocesseur conforme expérimental. Vous pouvez utiliser **/experimental : preprocesseur-** option pour spécifier explicitement le préprocesseur traditionnel.

L’option **/experimental : preprocesser** est disponible à partir de Visual Studio 2017 version 15,8.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour obtenir des informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration** > **C/C++**  > **Ligne de commande**.

1. Modifiez la propriété **options supplémentaires** pour inclure **/experimental : préprocesseur** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
