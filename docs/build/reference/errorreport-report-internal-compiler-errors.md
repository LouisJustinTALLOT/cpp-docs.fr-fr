---
title: /errorReport (Signaler les erreurs internes du compilateur)
description: Référence pour l’option de ligneC++ de commande Microsoft C/compiler/ErrorReport.
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
ms.openlocfilehash: afc366728e62029ffbd3993e2fdd740e3aaf3369
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439888"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Signaler les erreurs internes du compilateur)

> [!NOTE]
> L’option **/errorreport** est déconseillée. À compter de Windows Vista, le rapport d’erreurs est contrôlé par les paramètres d' [rapport d’erreurs Windows (WER)](/windows/win32/wer/windows-error-reporting) .

## <a name="syntax"></a>Syntaxe

> **/errorreport :** \[**aucune** \| **invite** \| **file d’attente** \| **Envoyer** ]

## <a name="remarks"></a>Notes

Une erreur interne du compilateur est générée lorsque le compilateur ne peut pas traiter un fichier de code source. Lorsqu’une glace se produit, le compilateur ne produit pas de fichier de sortie ou tout diagnostic utile que vous pouvez utiliser pour corriger votre code.

Les arguments **/errorreport** sont remplacés par les paramètres de service rapport d’erreurs Windows. Le compilateur envoie automatiquement des rapports d’erreurs internes à Microsoft, si la création de rapports est activée par Rapport d’erreurs Windows. Aucun rapport n’est envoyé s’il est désactivé par Rapport d’erreurs Windows.


### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l’environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez les **Propriétés de configuration** > page de propriétés **avancé** **CC++ /**  > .

1. Modifiez la propriété **rapport d’erreurs** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)\
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
