---
title: '/experimental : module (activer la prise en charge du module)'
description: 'Utilisez l’option de compilateur/experimental : module pour activer la prise en charge expérimentale du compilateur pour les modules.'
ms.date: 09/03/2019
f1_keywords:
- module
- /experimental:module
helpviewer_keywords:
- module
- /experimental:module
- Enable module support
ms.openlocfilehash: 82cce127ad5a2f87d11e4a653035bd80ea9f5001
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70294456"
---
# <a name="experimentalmodule-enable-module-support"></a>/experimental : module (activer la prise en charge du module)

Active la prise en charge expérimentale du compilateur pour les modules, comme spécifié par le brouillon C++ 20 standard.

## <a name="syntax"></a>Syntaxe

> **/experimental : module** [ **-** ]

## <a name="remarks"></a>Notes

Vous pouvez activer la prise en charge des modules expérimentaux à l’aide de l’option du compilateur **/experimental : module** , ainsi que de l’option [/std : c + + latest](std-specify-language-standard-version.md) . Vous pouvez utiliser **/experimental : module-** pour désactiver explicitement la prise en charge des modules.

Cette option est disponible à partir de Visual Studio 2015 Update 1. À compter de Visual Studio 2019 version 16,2, les modules standard C++ 20 standard ne sont pas entièrement implémentés dans le compilateur Microsoft C++ . Vous pouvez utiliser la fonctionnalité Modules pour créer des modules à partition unique et importer les modules de bibliothèque standard fournis par Microsoft. Un module et le code qui le consomme doivent être compilés avec les mêmes options de compilateur.

Pour plus d’informations sur les modules et comment les utiliser et les créer, consultez [vue d' C++ensemble des modules dans ](../../cpp/modules-cpp.md).

Voici un exemple des options de ligne de commande du compilateur utilisées pour créer un module d’exportation à partir du fichier source *moduleName. IXX*:

```cmd
cl /EHsc /MD /experimental:module /module:export /module:name ModuleName /module:wrapper C:\Output\path\ModuleName.h /module:output C:\Output\path\ModuleName.ifc -c ModuleName.ixx
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés **Propriétés** > de > configuration**C/C++** **Language** .

1. Modifiez la **propriété C++ activer les modules (expérimental)** , puis choisissez **OK**.

## <a name="see-also"></a>Voir aussi

[/Zc (Conformité)](zc-conformance.md)
