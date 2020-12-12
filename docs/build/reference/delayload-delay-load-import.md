---
description: En savoir plus sur:/DELAYLOAD (différer le chargement de l’importation)
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
ms.openlocfilehash: 9f6a91a102b66a16896d51b960d44273a7935d79
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201493"
---
# <a name="delayload-delay-load-import"></a>/DELAYLOAD (Différer le chargement de l'importation)

> **/Delayload :**_DllName_

## <a name="parameters"></a>Paramètres

*DllName*<br/>
Le nom d'une DLL dont vous voulez différer le chargement.

## <a name="remarks"></a>Notes

Avec l'option /DELAYLOAD, la DLL spécifiée par `dllname` n'est chargée que lors du premier appel du programme à une fonction contenue dans cette DLL. Pour plus d’informations, consultez [prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md). Vous pouvez utiliser cette option autant de fois que nécessaire pour spécifier autant de DLL que vous voulez. Vous devez utiliser Delayimp.lib au moment de lier votre programme, ou vous pouvez implémenter votre propre fonction d'assistance du chargement différé.

L’option [/delay](delay-delay-load-import-settings.md) spécifie les options de liaison et de chargement pour chaque dll à chargement différé.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le dossier de l' **éditeur de liens** , sélectionnez la page de propriétés **entrée** .

1. Modifiez la propriété **chargement différé des dll** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
