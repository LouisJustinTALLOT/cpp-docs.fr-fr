---
title: -MANIFESTUAC (informations incorpore un compte d’utilisateur dans le manifeste) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.UACUIAccess
- VC.Project.VCLinkerTool.UACExecutionLevel
- VC.Project.VCLinkerTool.EnableUAC
dev_langs:
- C++
helpviewer_keywords:
- /MANIFESTUAC linker option
- MANIFESTUAC linker option
- -MANIFESTUAC linker option
ms.assetid: 2d243c39-fa13-493c-b56f-d0d972a1603a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bdfd872b43fbabdb14457ca54e6c4dfbe039313f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
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
  
#### <a name="parameters"></a>Paramètres  
 `fragment`  
 Chaîne qui contient le `level` et `uiAccess` valeurs. Pour plus d’informations, consultez la section Notes plus loin dans cette rubrique.  
  
 `_level`  
 Un des *asInvoker*, *highestAvailable*, ou *requireAdministrator*. La valeur par défaut est asInvoker. Pour plus d’informations, consultez la section Notes plus loin dans cette rubrique.  
  
 `_uiAccess`  
 `true` Si vous souhaitez que l’application ignore les niveaux de protection d’interface utilisateur et exécute l’entrée vers des fenêtres d’autorisation plus élevée sur le bureau. dans le cas contraire, `false`. La valeur par défaut est `false`. La valeur `true` uniquement pour les applications d’accessibilité d’interface utilisateur.  
  
## <a name="remarks"></a>Notes  
 Si vous spécifiez des options /MANIFESTUAC multiples sur la ligne de commande, la dernière entrée est prioritaire.  
  
 Les choix pour MANIFESTUAC sont les suivantes :  
  
-   `asInvoker`: L’application s’exécutera avec les mêmes autorisations que le processus qui l’a démarré. L’application peut être élevée à un niveau d’autorisation supérieur en sélectionnant **exécuter en tant qu’administrateur**.  
  
-   highestAvailable : l’application s’exécutera avec le niveau d’autorisation le plus élevé possible. Si l’utilisateur qui démarre l’application est membre du groupe Administrateurs, cette option est la même que requireAdministrator. Si le niveau d’autorisation disponible la plus élevé est supérieur au niveau du processus d’ouverture, le système demande des informations d’identification.  
  
-   requireAdministrator : l’application s’exécutera avec les autorisations d’administrateur. L’utilisateur qui démarre l’application doit être membre du groupe Administrateurs. Si le processus d’ouverture ne fonctionne pas avec des autorisations d’administration, le système demande des informations d’identification.  
  
 Vous pouvez spécifier les niveau et les valeurs uiAccess en une seule étape à l’aide de l’option/MANIFESTUAC : fragment. Le fragment doit être sous la forme suivante :  
  
```  
"level=[ asInvoker | highestAvailable | requireAdministrator ] uiAccess=[ true | false ]"  
```  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **le fichier manifeste** page de propriétés.  
  
5.  Modifier la **activer le compte d’utilisateur contrôle (UAC)**, **niveau d’exécution UAC**, et **ignorer la Protection UI UAC** propriétés.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Voir <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.EnableUAC%2A>, <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACExecutionLevel%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.UACUIAccess%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)