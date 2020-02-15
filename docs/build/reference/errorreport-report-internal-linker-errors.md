---
title: /ERRORREPORT (Signaler les erreurs internes de l’Éditeur de liens)
description: Guide de référence des options de ligne de commande Microsoft NMAKE.
ms.date: 02/09/2020
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
ms.openlocfilehash: 5e919d4f7eb59524b9145c8e3e59613e60aef1d2
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257687"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Signaler les erreurs internes de l'Éditeur de liens)

L’option **/errorreport** est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/Errorreport :** \[ **aucune** \| **invite** \| **file d’attente** \| **Envoyer** ]

## <a name="remarks"></a>Notes

Les arguments **/errorreport** sont remplacés par les paramètres de service rapport d’erreurs Windows. L’éditeur de liens envoie automatiquement des rapports d’erreurs internes à Microsoft, si la création de rapports est activée par Rapport d’erreurs Windows. Aucun rapport n’est envoyé s’il est désactivé par Rapport d’erreurs Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez **Propriétés de Configuration** > **éditeur de liens** > page de propriétés **avancé** .

1. Modifiez la propriété **rapport d’erreurs** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Voir aussi

\ de référence de l' [éditeur de liens MSVC](linking.md)
[Options de l’éditeur de liens MSVC](linker-options.md)
