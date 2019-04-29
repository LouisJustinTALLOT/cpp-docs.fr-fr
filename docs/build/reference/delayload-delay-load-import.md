---
title: /DELAYLOAD (Différer le chargement de l'importation)
ms.date: 11/04/2016
f1_keywords:
- /delayload
- VC.Project.VCLinkerTool.DelayLoadDLLS
helpviewer_keywords:
- DELAYLOAD linker option
- -DELAYLOAD linker option
- /DELAYLOAD linker option
- delayed loading of DLLs, /DELAYLOAD option
ms.assetid: 39ea0f1e-5c01-450f-9c75-2d9761ff9b28
ms.openlocfilehash: e92b470b7b5e76b39371f333cbbda150e7f6e8c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273353"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Différer le chargement de l'importation)

> **/ DELAYLOAD :**_dllname_

## <a name="parameters"></a>Paramètres

*dllname*<br/>
Le nom d'une DLL dont vous voulez différer le chargement.

## <a name="remarks"></a>Notes

Avec l'option /DELAYLOAD, la DLL spécifiée par `dllname` n'est chargée que lors du premier appel du programme à une fonction contenue dans cette DLL. Pour plus d’informations, consultez [prise en charge de l’éditeur de liens pour les DLL à chargement différé](linker-support-for-delay-loaded-dlls.md). Vous pouvez utiliser cette option autant de fois que nécessaire pour spécifier autant de DLL que vous voulez. Vous devez utiliser Delayimp.lib au moment de lier votre programme, ou vous pouvez implémenter votre propre fonction d'assistance du chargement différé.

Le [/retarder](delay-delay-load-import-settings.md) option spécifie la liaison et le chargement des options pour chaque DLL à chargement différé.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Dans le **l’éditeur de liens** dossier, sélectionnez le **entrée** page de propriétés.

1. Modifier le **chargement différé des DLL** propriété.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
