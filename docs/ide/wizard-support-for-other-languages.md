---
title: Prise en charge d’autres langues par l’Assistant | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.appwiz.EastAsianLanguages
dev_langs:
- C++
helpviewer_keywords:
- wizards [C++], language support
- language support for MFC projects
- projects [C++], language support
ms.assetid: b653c673-0687-455c-885f-15d7e2f4149d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 75aafd7177c3799c17b75419fd5ab9f54af91d35
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "33332440"
---
# <a name="wizard-support-for-other-languages"></a>Prise en charge d'autres langues par l'Assistant
Quand vous installez Visual Studio, le programme d’installation détecte les paramètres régionaux installés sur votre système et installe le ou les modèles de langue correspondant à ces paramètres. Par exemple, s’il détecte des paramètres d’Europe de l’Ouest, le programme d’installation installe les modèles anglais, français, italiens, espagnols et allemands. Ces langues figurent dans la liste **Langue des ressources** affichée dans la page [Type d’application](../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant Application MFC.  
  
## <a name="language-templates"></a>Modèles de langue  
 Les modèles ne sont pas tous installés sur tous les systèmes, car ils sont basés sur l’encodage ANSI et les ressources ne sont pas toutes modifiables sur tous les systèmes. Par exemple, par défaut, vous ne pouvez pas modifier des ressources de langue japonaise sur un système français.  
  
 Si vous utilisez Windows 2000 ou version ultérieure et que vous souhaitez créer une application MFC dans une autre langue, vous devez copier sur votre système le répertoire de modèles pour la langue appropriée à partir du support d’installation (disque 1) de Visual Studio.  
  
> [!NOTE]
>  Pour modifier le projet créé, vous devez remplacer les paramètres régionaux de votre système par les paramètres régionaux de la langue sélectionnée.  
  
 Chaque modèle est stocké dans un dossier spécifique du répertoire \Microsoft Visual Studio .NET 2003\Vc7\VCWizards\mfcappwiz\templates\, comme indiqué dans le tableau ci-dessous. Pour accéder au modèle de langue souhaité, copiez le dossier correspondant dans le répertoire \mfcappwiz\templates\ sur votre ordinateur. Une fois ce dossier copié, la langue apparaît dans la liste **Langue des ressources** affichée dans la page **Type d’application** de l’Assistant Application MFC.  
  
### <a name="language-templates-provided-in-visual-studio-net"></a>Modèles de langue fournis dans Visual Studio .NET  
  
|Langue|Modèle|  
|--------------|--------------|  
|Chinois (traditionnel)|1028|  
|Chinois (simplifié)|2052|  
|Anglais|1033|  
|Français|1036|  
|Allemand|1031|  
|Italien|1040|  
|Japonais|1041|  
|Coréen|1042|  
|Espagnol|3082|  
  
## <a name="format-of-visual-c-wizard-generated-files"></a>Format des fichiers Visual C++ générés par l’Assistant  
 Les Assistants Visual C++ génèrent les projets en Unicode quand la version de langue installée de Visual Studio ne correspond pas aux paramètres régionaux système. Par exemple, quand la version japonaise de Visual Studio est installée sur un ordinateur dont les paramètres régionaux sont définis avec une autre langue, les Assistants Visual C++ génèrent des projets composés de fichiers Unicode. Il s’agit d’un comportement courant sur les ordinateurs configurés avec les packs multilingues Windows.  
  
 Il en va différemment sur les systèmes où les paramètres régionaux système sont identiques à ceux de la version de langue de Visual Studio. Dans ce cas, les fichiers projet sont créés en ANSI, dans la page de codes système.  
  
## <a name="see-also"></a>Voir aussi  
 [Types de fichiers créés pour les projets Visual C++](../ide/file-types-created-for-visual-cpp-projects.md)   
 [Création et gestion de projets Visual C++](../ide/creating-and-managing-visual-cpp-projects.md)