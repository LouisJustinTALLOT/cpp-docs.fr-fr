---
title: -/errorreport (signaler les erreurs internes du compilateur) | Documents Microsoft
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
ms.openlocfilehash: 67e87143d31de98039f5d679c102a5815dd87abb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377246"
---
# <a name="errorreport-report-internal-compiler-errors"></a>/errorReport (Signaler les erreurs internes du compilateur)
Vous permet de signaler les erreurs internes du compilateur (ICE) directement à Microsoft.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/errorReport:[ none | prompt | queue | send ]  
```  
  
## <a name="arguments"></a>Arguments  
 **none**  
 Les rapports sur les erreurs internes du compilateur ne seront pas collectés ni envoyés à Microsoft.  
  
 **prompt**  
 Vous invite à envoyer un rapport dès qu'une erreur interne du compilateur se produit. **invite de commandes** est la valeur par défaut lorsqu’une application est compilée dans l’environnement de développement.  
  
 **queue**  
 Met le rapport d’erreurs en file d’attente. Lorsque vous vous connectez avec des privilèges d’administrateur, une fenêtre s’affiche afin que vous pouvez signaler les erreurs depuis la dernière fois que vous étiez connecté (vous ne serez pas invité à envoyer des rapports pour les échecs de plus d’une fois tous les trois jours). **file d’attente** est la valeur par défaut lorsqu’une application est compilée à une invite de commandes.  
  
 **send**  
 Envoie automatiquement des rapports d’erreurs internes du compilateur à Microsoft si le rapport est activé par les paramètres de système de rapport d’erreurs Windows.  
  
## <a name="remarks"></a>Notes  
 Une erreur interne du compilateur se produit quand le compilateur ne peut pas traiter un fichier de code source. Quand une telle erreur se produit, le compilateur ne génère pas de fichier de sortie ni de diagnostic utile que vous pouvez utiliser pour corriger votre code.  
  
 Dans les versions antérieures, lorsque vous avez obtenu une glace, vous ont été invité à appeler le Support technique de Microsoft pour signaler le problème. Avec **/errorReport**, vous pouvez fournir des informations ICE directement à Microsoft. Vos rapports d’erreurs peuvent aider à améliorer les versions ultérieures du compilateur.  
  
 La capacité d’un utilisateur à envoyer des rapports dépend des autorisations de stratégie ordinateur et utilisateur.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur le **avancé** page de propriétés.  
  
4.  Modifier la **rapport d’erreurs** propriété.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ErrorReporting%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)