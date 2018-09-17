---
title: -errorReport (signaler les erreurs internes du compilateur) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ErrorReporting
- /errorreport
dev_langs:
- C++
helpviewer_keywords:
- /errorReport compiler option [C++]
- -errorReport compiler option [C++]
ms.assetid: 819828f8-b0a5-412c-9c57-bf822f17e667
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c96225e566593987bef8ec9a82c73daacfcefb6
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720107"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Signaler les erreurs internes du compilateur)

Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft.

## <a name="syntax"></a>Syntaxe

```
/errorReport:[ none | prompt | queue | send ]
```

## <a name="arguments"></a>Arguments

**none**<br/>
Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.

**prompt**<br/>
Vous invite à envoyer un rapport dès qu'une erreur interne du compilateur se produit. **invite** est la valeur par défaut lorsqu’une application est compilée dans l’environnement de développement.

**queue**<br/>
Met le rapport d’erreurs en file d’attente. Lorsque vous vous connectez avec des privilèges d’administrateur, une fenêtre s’affiche afin que vous pouvez signaler toute défaillance depuis la dernière fois que vous étiez connecté (vous ne serez pas invité à envoyer des rapports d’échecs plus d’une fois tous les trois jours). **file d’attente** est la valeur par défaut lorsqu’une application est compilée à une invite de commandes.

**send**<br/>
Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft si le rapport est activé par les paramètres de système de rapport d’erreurs Windows.

## <a name="remarks"></a>Notes

Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source. Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.

Dans les versions antérieures, lorsque vous avez obtenu un erreur interne du compilateur, vous étiez invité à appeler les Services de Support technique Microsoft pour signaler le problème. Avec **/errorReport**, vous pouvez fournir des informations de glace directement à Microsoft. Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.

La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **avancé** page de propriétés.

1. Modifier le **rapport d’erreurs** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)