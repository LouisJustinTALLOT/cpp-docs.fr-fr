---
title: /WINMD (générer des métadonnées Windows)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadata
ms.assetid: bcfb4901-411e-4c9e-9f78-23028b6e5fcc
ms.openlocfilehash: 93db20d14d3477734e35d33111246f9459310b90
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810365"
---
# <a name="winmd-generate-windows-metadata"></a>/WINMD (générer des métadonnées Windows)

Active la génération d’un fichier de métadonnées de Runtime Windows (.winmd).

> **/ WINMD**\[**:**{**NON**\|**UNIQUEMENT**}]

## <a name="arguments"></a>Arguments

**/WINMD**<br/>
Le paramètre par défaut pour les applications de plateforme Windows universelle. L’éditeur de liens génère le fichier exécutable binaire et le fichier de métadonnées .winmd.

**/WINMD:NO**<br/>
L’éditeur de liens génère le fichier exécutable binaire, mais pas un fichier .winmd.

**/ WINMD : UNIQUEMENT**<br/>
L’éditeur de liens génère uniquement le fichier .winmd, mais pas le fichier exécutable binaire.

## <a name="remarks"></a>Notes

Le **/WINMD** option de l’éditeur de liens est utilisée pour les applications UWP et de composants Windows runtime pour contrôler la création d’un fichier de métadonnées (.winmd) Windows Runtime. Un fichier .winmd est un type de DLL qui contient les métadonnées pour les types de runtime Windows et, dans le cas de composants d’exécution, les implémentations de ces types. Les métadonnées suivent le [ECMA-335](http://www.ecma-international.org/publications/standards/Ecma-335.htm) standard.

Par défaut, le nom de fichier de sortie présente sous la forme *binaryname*.winmd. Pour spécifier un autre nom de fichier, utilisez le [/WINMDFILE](winmdfile-specify-winmd-file.md) option.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** > **Windows métadonnées** page de propriétés.

1. Dans le **générer des métadonnées Windows** liste déroulante, sélectionnez l’option souhaitée.

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas : Création d’un composant Simple Windows Runtime et l’appeler à partir de JavaScript](/windows/uwp/winrt-components/walkthrough-creating-a-simple-windows-runtime-component-and-calling-it-from-javascript)<br/>
[Introduction à Microsoft Interface Definition Language 3.0](/uwp/midl-3/intro)<br/>
[/WINMDFILE (Spécifier un fichier winmd)](winmdfile-specify-winmd-file.md)<br/>
[/WINMDKEYFILE (Spécifier un fichier de clé winmd)](winmdkeyfile-specify-winmd-key-file.md)<br/>
[/WINMDKEYCONTAINER (Spécifier un conteneur de clé de nom fort)](winmdkeycontainer-specify-key-container.md)<br/>
[/WINMDDELAYSIGN (Signer partiellement un winmd)](winmddelaysign-partially-sign-a-winmd.md)<br/>
[Référence de l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
