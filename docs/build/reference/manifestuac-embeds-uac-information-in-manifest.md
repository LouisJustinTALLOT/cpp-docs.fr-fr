---
title: /MANIFESTUAC (Incorporer des informations sur le contrôle de compte d'utilisateur dans le manifeste)
ms.date: 06/12/2020
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 96719c6f6f5359afb03b967524b1f65db6dc664a
ms.sourcegitcommit: 8645408c7929558b8162f781776d0908d790a41c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85334934"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Incorporer des informations sur le contrôle de compte d'utilisateur dans le manifeste)

Spécifie si les informations de contrôle de compte d’utilisateur sont incorporées dans le manifeste du programme.

## <a name="syntax"></a>Syntaxe

> **`/MANIFESTUAC`**\
> **`/MANIFESTUAC:NO`**\
> **`/MANIFESTUAC:`**_`level`_\
> **`/MANIFESTUAC:`**_`uiAccess`_\
> **`/MANIFESTUAC:`**_`fragment`_

### <a name="parameters"></a>Paramètres

**`NO`**<br/>
L’éditeur de liens n’incorpore pas les informations de contrôle de compte d’utilisateur dans le manifeste du programme.

*`level`*<br/>
**`level=`** suivi de **`'asInvoker'`** , **`'highestAvailable'`** ou **`'requireAdministrator'`** . La valeur par défaut est **`'asInvoker'`** . Pour plus d’informations, consultez la section [Notes](#remarks) .

*`uiAccess`*<br/>
**`uiAccess='true'`** Si vous souhaitez que l’application contourne les niveaux de protection de l’interface utilisateur et l’entrée de lecteur vers des fenêtres d’autorisations supérieures sur le Bureau ; Sinon, **`uiAccess='false'`** . La valeur par défaut est **`uiAccess='false'`** . Définissez cet argument sur **`uiAccess='true'`** uniquement pour les applications d’accessibilité de l’interface utilisateur.

*`fragment`*<br/>
Chaîne qui contient les *`level`* valeurs et *`uiAccess`* . Peut éventuellement être placé entre des guillemets doubles. Pour plus d’informations, consultez la section [Notes](#remarks) .

## <a name="remarks"></a>Remarques

Si vous spécifiez plusieurs **`/MANIFESTUAC`** options sur la ligne de commande, la dernière entrée est prioritaire.

Les options possibles pour sont les suivantes **`/MANIFESTUAC:`** _`level`_ :

- **`level='asInvoker'`**: L’application s’exécute au même niveau d’autorisation que le processus qui l’a démarrée. Vous pouvez élever l’application à un niveau d’autorisation supérieur en sélectionnant **exécuter en tant qu’administrateur**.

- **`level='highestAvailable'`**: L’application s’exécute au niveau d’autorisation le plus élevé possible. Si l’utilisateur qui démarre l’application est membre du groupe administrateurs, cette option est la même que **`level='requireAdministrator'`** . Si le niveau d’autorisation le plus élevé disponible est supérieur au niveau du processus d’ouverture, le système vous invite à entrer les informations d’identification.

- **`level='requireAdministrator'`**: L’application s’exécute en utilisant des autorisations d’administrateur. L’utilisateur qui démarre l’application doit être membre du groupe administrateurs. Si le processus d’ouverture ne s’exécute pas avec des autorisations d’administration, le système vous invite à entrer les informations d’identification.

Vous pouvez spécifier les *`level`* valeurs et *`uiAccess`* en une seule étape à l’aide de l' **`/MANIFESTUAC:`** _`fragment`_ option. Le fragment doit se présenter sous la forme suivante :

> **`/MANIFESTUAC:`** \[ **`"`** ] **`level=`** { **`'asInvoker'`** | **`'highestAvailable'`** | **`'requireAdministrator'`** } **`uiAccess=`** { **`'true'`** | **`'false'`** } \[ **`"`** ]

Par exemple :

**`/MANIFESTUAC:"level='highestAvailable' uiAccess='true'"`**

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la **Configuration Properties**page de propriétés  >  **Linker**  >  **fichier manifeste** de l’éditeur de liens propriétés de configuration.

1. Modifiez les propriétés **activer le contrôle de compte d’utilisateur (UAC)**, le niveau d' **exécution UAC**et **contourner l’interface utilisateur** .

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Voir <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Voir aussi

[Informations de référence sur l’éditeur de liens MSVC](linking.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
