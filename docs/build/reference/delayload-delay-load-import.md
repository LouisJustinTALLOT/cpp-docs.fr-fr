---
title: -DELAYLOAD (différer le chargement l’importation) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
dev_langs:
- C++
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 800b3d7d588d1038ac61cb7c9c4b9f1913bec9d4
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722369"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Différer le chargement de l'importation)

> **/ DELAYLOAD :**_dllname_

## <a name="parameters"></a>Paramètres

*dllname*<br/>
Le nom d'une DLL dont vous voulez différer le chargement.

## <a name="remarks"></a>Notes

Avec l'option /DELAYLOAD, la DLL spécifiée par `dllname` n'est chargée que lors du premier appel du programme à une fonction contenue dans cette DLL. Pour plus d’informations, consultez [prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md). Vous pouvez utiliser cette option autant de fois que nécessaire pour spécifier autant de DLL que vous voulez. Vous devez utiliser Delayimp.lib au moment de lier votre programme, ou vous pouvez implémenter votre propre fonction d'assistance du chargement différé.

Le [/retarder](../../build/reference/delay-delay-load-import-settings.md) option spécifie la liaison et le chargement des options pour chaque DLL à chargement différé.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

2. Dans le **l’éditeur de liens** dossier, sélectionnez le **entrée** page de propriétés.

3. Modifier le **chargement différé des DLL** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)