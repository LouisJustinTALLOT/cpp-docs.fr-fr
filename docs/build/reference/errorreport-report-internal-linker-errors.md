---
title: -ERRORREPORT (signaler les erreurs internes de l’éditeur de liens) | Microsoft Docs
ms.custom: ''
ms.date: 12/28/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /ERRORREPORT
- VC.Project.VCLinkerTool.ErrorReporting
dev_langs:
- C++
helpviewer_keywords:
- /ERRORREPORT linker option
- ERRORREPORT linker option
- -ERRORREPORT linker option
ms.assetid: f5fab595-a2f1-4eb0-ab5c-1c0fbd3d8c28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30cc9cbab9a3575eee2f791b0af7dfcaffc1538d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701088"
---
# <a name="errorreport-report-internal-linker-errors"></a>/ERRORREPORT (Signaler les erreurs internes de l'Éditeur de liens)

> **/ errorreport :**[ **aucun** | **invite** | **file d’attente** | **envoyer** ]

## <a name="arguments"></a>Arguments

**none**<br/>
Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.

**prompt**<br/>
Vous invite à envoyer un rapport dès qu'une erreur interne du compilateur se produit. **invite** est la valeur par défaut lorsqu’une application est compilée dans l’environnement de développement.

**queue**<br/>
Met le rapport d’erreurs en file d’attente. Lorsque vous vous connectez avec des privilèges d’administrateur, une fenêtre s’affiche afin que vous pouvez signaler toute défaillance depuis la dernière fois que vous étiez connecté (vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours). **file d’attente** est la valeur par défaut lorsqu’une application est compilée à une invite de commandes.

**send**<br/>
Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft si le rapport est activé par les paramètres de service de rapport d’erreurs Windows.

## <a name="remarks"></a>Notes

Le **/ERRORREPORT** option vous permet de fournir des informations sur l’erreur (ICE) interne du compilateur directement à Microsoft.

L’option **/errorreport : send** envoie automatiquement les informations d’erreur à Microsoft, si activé par les paramètres du service de rapport d’erreurs Windows.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration** > **l’éditeur de liens** > **avancé** page de propriétés.

1. Modifier le **rapport d’erreurs** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Voir aussi

[/errorReport (signaler les erreurs du compilateur interne)](../../build/reference/errorreport-report-internal-compiler-errors.md)
[définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
