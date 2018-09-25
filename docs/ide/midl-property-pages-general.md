---
title: 'Pages de propriétés MIDL : Général | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCMidlTool.PreprocessorDefinitions
- VC.Project.VCMidlTool.DefaultCharType
- VC.Project.VCMidlTool.WarnAsError
- VC.Project.VCMidlTool.AdditionalIncludeDirectories
- VC.Project.VCMidlTool.WarningLevel
- VC.Project.VCMidlTool.MkTypLibCompatible
- VC.Project.VCMidlTool.GenerateStublessProxies
- VC.Project.VCMidlTool.SuppressStartupBanner
- VC.Project.VCMidlTool.TargetEnvironment
- VC.Project.VCMidlTool.OVERWRITEStandardIncludePath
dev_langs:
- C++
helpviewer_keywords:
- MIDL, property pages
ms.assetid: 0692484c-a7e6-4270-8df7-981589368399
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 32e1c743844d252b391a4a747d803ba0e8c81c54
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431422"
---
# <a name="midl-property-pages-general"></a>Pages de propriétés MIDL : Général

La page de propriétés **Général** du dossier **MIDL** spécifie les options du compilateur MIDL suivantes :

- Définitions de préprocesseur [(/D](https://msdn.microsoft.com/library/windows/desktop/aa367321))

- Autres répertoires Include ([/I](https://msdn.microsoft.com/library/windows/desktop/aa367328))

- Chemin d’accès Include standard ignoré ([/no_def_idir](https://msdn.microsoft.com/library/windows/desktop/aa367347))

- Compatible MkTypLib ([/mktyplib203](https://msdn.microsoft.com/library/windows/desktop/aa367332))

- Niveau d’avertissement ([/W](https://msdn.microsoft.com/library/windows/desktop/aa367383))

- Avertissement comme erreur ([/WX](https://msdn.microsoft.com/library/windows/desktop/aa367387))

- Suppression de la bannière de démarrage ([/nologo](https://msdn.microsoft.com/library/windows/desktop/aa367341))

- Type de caractère MIDL ([/char](https://msdn.microsoft.com/library/windows/desktop/aa367314))

- Environnement cible ([/env](https://msdn.microsoft.com/library/windows/desktop/aa367323))

- Génération de proxies sans stub ([/Oicf](https://msdn.microsoft.com/library/windows/desktop/aa367352))

Pour plus d’informations sur l’accès à la page de propriétés **Général** dans le dossier **MIDL**, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).

Pour plus d’informations sur l’accès par programmation aux options MIDL des projets C++, consultez l’objet <xref:Microsoft.VisualStudio.VCProjectEngine.VCMidlTool>.

## <a name="see-also"></a>Voir aussi

[MIDL, page de propriétés](../ide/midl-property-pages.md)