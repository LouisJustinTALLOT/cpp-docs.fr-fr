---
title: /MANIFESTUAC (Incorporer des informations sur le contrôle de compte d'utilisateur dans le manifeste)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
ms.openlocfilehash: 8ae9d18bb0fe2172886ef24250d53cf76851bbba
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57420425"
---
# <a name="manifestuac-embeds-uac-information-in-manifest"></a>/MANIFESTUAC (Incorporer des informations sur le contrôle de compte d'utilisateur dans le manifeste)

Spécifie si les informations de contrôle de compte d’utilisateur sont incorporées dans le manifeste du programme.

## <a name="syntax"></a>Syntaxe

```
/MANIFESTUAC
/MANIFESTUAC:NO
/MANIFESTUAC:fragment
/MANIFESTUAC:level=_level
/MANIFESTUAC:uiAccess=_uiAccess
```

### <a name="parameters"></a>Paramètres

*fragment*<br/>
Chaîne qui contient le `level` et `uiAccess` valeurs. Pour plus d’informations, consultez la section Notes plus loin dans cette rubrique.

*_level*<br/>
Un des *asInvoker*, *highestAvailable*, ou *requireAdministrator*. La valeur par défaut est asInvoker. Pour plus d’informations, consultez la section Notes plus loin dans cette rubrique.

*_uiAccess*<br/>
**true** si vous souhaitez que l’application ignore les niveaux de protection d’interface utilisateur et exécute l’entrée vers des fenêtres d’autorisations supérieures sur le bureau ; sinon, **false**. Valeur par défaut est **false**. La valeur **true** uniquement pour les applications d’accessibilité d’interface utilisateur.

## <a name="remarks"></a>Notes

Si vous spécifiez plusieurs options/MANIFESTUAC sur la ligne de commande, le dernier entré est prioritaire.

Les choix pour MANIFESTUAC sont les suivantes :

- `asInvoker`: L’application s’exécutera avec les mêmes autorisations que le processus qui l’a démarrée. L’application peut être élevée à un niveau d’autorisation plus élevé en sélectionnant **exécuter en tant qu’administrateur**.

- highestAvailable : L’application s’exécute avec le niveau d’autorisation le plus élevé possible. Si l’utilisateur qui démarre l’application est membre du groupe Administrateurs, cette option est la même que requireAdministrator. Si le niveau d’autorisation disponible la plus élevé est supérieur au niveau du processus d’ouverture, le système vous invite pour les informations d’identification.

- requireAdministrator : L’application s’exécutera avec les autorisations d’administrateur. L’utilisateur qui démarre l’application doit être membre du groupe Administrateurs. Si le processus d’ouverture ne fonctionne pas avec des autorisations administratives, le système vous invite pour les informations d’identification.

Vous pouvez spécifier les niveau et les valeurs uiAccess en une seule étape en utilisant l’option/MANIFESTUAC : fragment. Le fragment doit être sous la forme suivante :

```
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"
```

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le nœud **Propriétés de configuration**.

1. Développez le **l’éditeur de liens** nœud.

1. Sélectionnez le **le fichier manifeste** page de propriétés.

1. Modifier le **activer contrôle (compte utilisateur)**, **niveau d’exécution UAC**, et **ignorer la Protection UI UAC** propriétés.

### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation

1. Voir <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.

## <a name="see-also"></a>Voir aussi

[Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)
