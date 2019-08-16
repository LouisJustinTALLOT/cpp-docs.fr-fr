---
title: Fonctionnalités avancées, Assistant Application MFC
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.advanced
helpviewer_keywords:
- MFC Application Wizard, advanced features
ms.assetid: 8a6681c5-6576-4b12-841a-6862beee76fa
ms.openlocfilehash: dc2b745bf97dff65a3612c29745c9d0e455a347d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507805"
---
# <a name="advanced-features-mfc-application-wizard"></a>Fonctionnalités avancées, Assistant Application MFC

La rubrique répertorie les options de fonctionnalités supplémentaires de l’application, telles que l’aide, la prise en charge de l’impression, etc. Dans chaque section, spécifiez la prise en charge supplémentaire de ces fonctionnalités avancées.

- **Aide contextuelle (HTML)**

   Génère un ensemble de fichiers d’aide pour l’aide contextuelle, disponible à l’aide de la touche F1 et d’un menu aide, ou en cliquant sur un bouton **aide** dans une boîte de dialogue. La prise en charge de l'aide nécessite le compilateur d'aide. Si vous n'en disposez pas, vous pouvez l'installer en exécutant à nouveau le programme d'installation.

   Consultez [HTML Help: Aide contextuelle pour vos programmes](../../mfc/html-help-context-sensitive-help-for-your-programs.md) et vos [fichiers d’aide (aide HTML)](../../build/reference/help-files-html-help.md) pour plus d’informations.

- **Impression et aperçu avant impression**

   Génère le code pour gérer les commandes d’impression, de configuration de l’impression et d’aperçu avant impression en appelant des fonctions membres de la [classe CView](../../mfc/reference/cview-class.md) à partir de la bibliothèque MFC. L'Assistant ajoute également des commandes pour ces fonctions au menu de l'application. La prise en charge de l’impression est disponible uniquement pour les applications qui spécifient la **prise en charge de l’architecture document/vue** dans la page [type d’application, Assistant Application MFC](../../mfc/reference/application-type-mfc-application-wizard.md) de l’Assistant. Par défaut, les applications à architecture Document/Vue disposent d'une prise en charge de l'impression.

- **Automation**

   Spécifie que l'application peut manipuler des objets implémentés dans une autre application ou expose l'application aux clients Automation.

- **Contrôles ActiveX**

   Prend en charge les contrôles ActiveX (valeur par défaut). Si vous ne sélectionnez pas cette option et que vous souhaitez ultérieurement insérer des contrôles ActiveX dans votre projet, vous devez ajouter un appel à [AfxEnableControlContainer (](ole-initialization.md#afxenablecontrolcontainer) dans la fonction membre [CWinApp:: InitInstance](../../mfc/reference/cwinapp-class.md#initinstance) de votre application.

- **MAPI (API de messagerie)**

   Spécifie que l'application peut créer, manipuler, transférer et stocker des messages électroniques.

- **Sockets Windows**

   Prend en charge Windows Sockets, que vous pouvez utiliser pour écrire des applications qui communiquent sur les réseaux TCP/IP.

- **Active Accessibility**

   Ajoute la prise en charge de [IAccessible](/windows/win32/api/oleacc/nn-oleacc-iaccessible) aux classes dérivées de [CWnd](../../mfc/reference/cwnd-class.md), que vous pouvez utiliser pour personnaliser l’interface utilisateur pour une meilleure interaction avec les clients d’accessibilité.

- **Manifeste de contrôle commun**

   Activé par défaut. Génère un manifeste d’application qui active la DLL de contrôles communs incluse dans Microsoft Windows XP et des systèmes d’exploitation plus récents.

   La version 6 de la DLL de contrôles communs ne met pas automatiquement à jour la version précédente des contrôles communs utilisée par vos applications existantes. Pour utiliser la version 6 de la DLL de contrôles communs, vous devez créer un manifeste d'application qui commande à votre application de charger la DLL. Cette DLL de contrôles communs prend également en charge les thèmes Windows XP.

   Un manifeste d'application peut également spécifier d'autres DLL et versions demandées par votre application. Pour plus d’informations sur les manifestes d’application, consultez [applications isolées et assemblys côte à côte](/windows/win32/SbsCs/isolated-applications-and-side-by-side-assemblies-portal) dans le SDK Windows.

- **Prendre en charge le gestionnaire de redémarrage**

   Ajoute la prise en charge du [Gestionnaire de redémarrage Windows](/windows/win32/RstMgr/using-restart-manager). Cette vidéo montre comment utiliser le gestionnaire de redémarrage à partir de MFC: [Comment faire: Utilisez le nouveau gestionnaire](/previous-versions/visualstudio/visual-studio-2010/dd831853(v%3dvs.100))de redémarrage.

- **Volets Frame avancés**

   |Option|Description|
   |------------|-----------------|
   |**Volet d’ancrage de l’Explorateur**|Crée un volet d’ancrage qui ressemble à l' **Explorateur de solutions** Visual Studio à gauche de la fenêtre frame principale.|
   |**Frame d’ancrage de sortie**|Crée un volet d’ancrage qui ressemble au volet de **sortie** de Visual Studio qui se trouve sous la fenêtre frame principale.|
   |**Volet d’ancrage des propriétés**|Crée un volet d’ancrage qui ressemble au volet **Propriétés** de Visual Studio à droite de la fenêtre frame principale.|
   |**Volet de navigation**|Crée un volet d'ancrage qui ressemble à la barre de navigation Outlook et se trouve à gauche de la fenêtre frame principale.|
   |**Barre de légende**|Crée une barre de légende de style Office au-dessus de la fenêtre frame principale.|

- **Nombre de fichiers dans la liste des fichiers récents**

   Spécifie le nombre de fichiers à répertorier dans la liste des derniers fichiers utilisés. Le nombre par défaut est 4.

## <a name="see-also"></a>Voir aussi

[Assistant Application MFC](../../mfc/reference/mfc-application-wizard.md)
