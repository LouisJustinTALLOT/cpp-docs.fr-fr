---
description: En savoir plus sur:/WINMD (générer des métadonnées Windows)
title: /WINMD (générer des métadonnées Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 7cf52a49716e6ec30a29c7e6a96fe7a078b4830c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97259082"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (générer des métadonnées Windows)

Active la génération d’un fichier de métadonnées de Windows Runtime (. winmd).

> **/WINMD** \[ **:**{**non** \| **uniquement**}]

## <a name="arguments"></a>Arguments

**/WINMD**<br/>
Paramètre par défaut pour les applications plateforme Windows universelle. L’éditeur de liens génère le fichier exécutable binaire et le fichier de métadonnées. winmd.

**/WINMD : NON**<br/>
L’éditeur de liens génère uniquement le fichier exécutable binaire, mais pas le fichier. winmd.

**/WINMD : UNIQUEMENT**<br/>
L’éditeur de liens génère uniquement le fichier. winmd, mais pas le fichier exécutable binaire.

## <a name="remarks"></a>Notes

L’option **/WINMD** de l’éditeur de liens est utilisée pour les applications UWP et les composants Windows Runtime pour contrôler la création d’un fichier de métadonnées de Windows Runtime (. WINMD). Un fichier. winmd est un type de DLL qui contient des métadonnées pour les types Windows Runtime et, dans le cas des composants d’exécution, les implémentations de ces types. Les métadonnées suivent la norme [ECMA-335](https://www.ecma-international.org/publications/standards/Ecma-335.htm) .

Par défaut, le nom du fichier de sortie se présente sous la forme *binaryname*. winmd. Pour spécifier un autre nom de fichier, utilisez l’option [/WINMDFILE](winmdfile-specify-winmd-file.md) .

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés  >    >  **métadonnées Windows** de l’éditeur de liens propriétés de configuration.

1. Dans la zone de liste déroulante **générer les métadonnées Windows** , sélectionnez l’option souhaitée.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : création d’un composant Windows Runtime simple et appel de ce composant à partir de JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Présentation de Microsoft Interface Definition Language 3,0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (spécifier un fichier winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (spécifier le fichier de clé winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (spécifier le conteneur de clé)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (signer partiellement un winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
